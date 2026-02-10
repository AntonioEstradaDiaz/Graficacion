# 🟦 Práctica: Dibujo de un Polígono 2D en Blender con Python

## 🎯 Objetivo
Aprender a generar un polígono 2D de forma programática en Blender utilizando Python y la API `bpy`.  
Se busca comprender la creación de vértices, aristas y objetos dentro de una escena.

---

## 🧰 Requisitos
- Blender 3.x o superior
- Conocimientos básicos de Python
- Editor de scripts de Blender

---

## ⚙️ Conceptos utilizados
- Creación de mallas (`meshes`)
- Creación de objetos (`objects`)
- Coordenadas polares a cartesianas
- Uso de ciclos `for`
- Manipulación de escenas en Blender

---

## 🧠 Explicación general
El script crea un polígono usando una función que recibe:
- Nombre del objeto
- Número de lados
- Radio del polígono

Los vértices se calculan usando funciones trigonométricas (`cos` y `sin`), distribuyéndolos uniformemente en un círculo.

Luego se crean aristas para conectar cada vértice con el siguiente y cerrar la figura.

---

## ▶️ Pasos para ejecutar la práctica

1. Abrir Blender
2. Ir a la pestaña **Scripting**
3. Crear un nuevo Script
4. Copiar el código
5. Presionar **Run Script**

---

## ✅ Resultado esperado
Se generará automáticamente un polígono 2D dentro de la escena.  
En el ejemplo actual se crea un **hexágono** de radio 5.

---

## 💻 Código
```python
import bpy
import math

def crear_poligono_2d(nombre, lados, radio):
    # Crear una nueva malla y un nuevo objeto
    malla = bpy.data.meshes.new(nombre)
    objeto = bpy.data.objects.new(nombre, malla)

    # Vincular el objeto a la escena actual
    bpy.context.collection.objects.link(objeto)

    vertices = []
    aristas = []

    # Cálculo de vértices usando coordenadas polares a cartesianas
    for i in range(lados):
        angulo = 2 * math.pi * i / lados
        x = radio * math.cos(angulo)
        y = radio * math.sin(angulo)
        vertices.append((x, y, 0))  # Z = 0 para mantenerlo en 2D

    # Definir las conexiones (aristas) entre los vértices
    for i in range(lados):
        aristas.append((i, (i + 1) % lados))

    # Cargar los datos en la malla
    malla.from_pydata(vertices, aristas, [])
    malla.update()

# Limpiar la escena antes de empezar
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete()

# Llamada a la función: Un hexágono de radio 5
crear_poligono_2d("Poligono2D", lados=6, radio=5)

