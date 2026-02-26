# Generación Procedural de Escenario con Curva Sinusoidal y Animación de Cámara en Blender

Este script en Python para Blender (bpy) genera un escenario procedural basado en una curva sinusoidal y crea una animación de cámara en primera persona que recorre dicha curva.

El proyecto demuestra:

- Uso del modelo de color RGB  
- Construcción procedural mediante funciones matemáticas  
- Aplicación de transformaciones (traslación, rotación y escala)  
- Cálculo de derivadas para orientar objetos  
- Animación automática con keyframes  

---

## Importaciones

```python
import bpy
import math
```

bpy → API oficial de Blender para manipular escenas.  
math → Biblioteca matemática para usar sin, cos, atan, etc.

---

## 1. Creación de Materiales (Modelo RGB)

```python
def crear_material(nombre, color_rgb):
    mat = bpy.data.materials.new(name=nombre)
    mat.diffuse_color = (*color_rgb, 1.0)
    return mat
```

### ¿Qué hace?

- Crea un nuevo material.  
- Usa el modelo de color RGB.  
- El 1.0 final representa el canal Alpha (opacidad).  

Ejemplo de color:

```python
(0.0, 0.8, 1.0)
```

Representa un color azul neón.

---

## 2. Generación del Escenario Sinusoidal

```python
def generar_escenario_onda():
```

Esta función contiene toda la lógica principal.

---

### 2.1 Limpieza de la Escena

```python
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete()
```

Se eliminan todos los objetos para comenzar desde cero.

---

### 2.2 Definición de Materiales

```python
mat_pared_a = crear_material("ParedOscura", (0.1, 0.1, 0.1))
mat_pared_b = crear_material("ParedDetalle", (0.0, 0.8, 1.0))
```

ParedOscura → Gris oscuro  
ParedDetalle → Azul neón  

---

### 2.3 Parámetros de la Curva

```python
cantidad_bloques = 30
distancia_pasillo = 40
amplitud = 5
frecuencia = 0.2
ancho_pasillo = 4
```

Explicación matemática:

La curva utilizada es:

y = A · sin(fx)

Donde:

- A → amplitud (altura de la onda)  
- f → frecuencia  
- x → posición horizontal  

---

## 3. Construcción Procedural

```python
for i in range(cantidad_bloques):
```

Se generan bloques a lo largo de la curva.

---

### 3.1 Posición en la Curva

```python
x = (i / (cantidad_bloques - 1)) * distancia_pasillo
y_base = amplitud * math.sin(frecuencia * x)
```

x avanza linealmente.  
y_base sigue la función seno.

---

### 3.2 Cálculo de la Derivada (Orientación)

```python
pendiente = amplitud * frecuencia * math.cos(frecuencia * x)
angulo_rotacion = math.atan(pendiente)
```

La derivada de:

y = A sin(fx)

es:

y' = A f cos(fx)

Esto permite:

- Obtener la pendiente  
- Calcular el ángulo de rotación  
- Hacer que los cubos sigan la tangente de la curva  

---

### 3.3 Creación de Paredes Paralelas

```python
for offset in [-ancho_pasillo, ancho_pasillo]:
```

Se crean dos paredes:

- Una a la izquierda  
- Una a la derecha  

```python
bpy.ops.mesh.primitive_cube_add(location=(x, y_base + offset, 1))
```

Se posicionan usando traslación.  
Se rotan usando el ángulo calculado.

---

### 3.4 Lógica Visual

```python
if offset < 0 and i % 2 == 0:
```

Alterna bloques con color neón.  
Aplica escalado en eje Z.

```python
bloque.scale.z = 1.5
```

Demuestra transformación por escala.

---

## 4. Creación del Suelo

```python
bpy.ops.mesh.primitive_plane_add(location=(distancia_pasillo/2, 0, 0))
```

Se crea un plano base.

Se escala para cubrir toda el área del recorrido:

```python
suelo.scale.x = distancia_pasillo / 1.8
suelo.scale.y = amplitud + ancho_pasillo
```

---

## 5. Animación de Cámara en Primera Persona

```python
bpy.ops.object.camera_add()
```

Se crea una cámara nueva.

```python
bpy.context.scene.camera = camara
```

Se establece como cámara activa.

---

### Configuración de Frames

```python
frames_totales = 150
bpy.context.scene.frame_end = frames_totales
```

Duración total: 150 frames.

---

### Movimiento de Cámara

```python
for f in range(frames_totales + 1):
```

Se calcula un parámetro normalizado:

```python
t = f / frames_totales
```

Luego:

```python
x_cam = t * distancia_pasillo
y_cam = amplitud * math.sin(frecuencia * x_cam)
```

La cámara sigue exactamente la misma curva.

---

### Rotación Dinámica

```python
derivada_cam = amplitud * frecuencia * math.cos(frecuencia * x_cam)
rot_z = math.atan(derivada_cam)
```

La cámara rota siguiendo la tangente de la curva.

```python
camara.rotation_euler.x = math.radians(90)
camara.rotation_euler.z = rot_z + math.radians(90)
```

Esto logra:

- Vista en primera persona  
- Movimiento fluido  
- Orientación natural  

---

### Inserción de Keyframes

```python
camara.keyframe_insert(data_path="location", frame=f)
camara.keyframe_insert(data_path="rotation_euler", frame=f)
```

Esto guarda:

- Posición  
- Rotación  

En cada frame, generando animación automática.

---

## Ejecución Final

```python
generar_escenario_onda()
```

Ejecuta todo el proceso.

---

## Conceptos Aplicados

- Graficación por computadora  
- Modelado procedural  
- Transformaciones geométricas  
- Derivadas y tangentes  
- Animación basada en funciones matemáticas  
- Modelo de color RGB  
- Automatización con Python en Blender  

---

## Resultado

El script genera:

- Un pasillo con paredes siguiendo una onda sinusoidal  
- Alternancia visual con efecto neón  
- Suelo adaptado al recorrido  
- Cámara animada en primera persona siguiendo la curva  
