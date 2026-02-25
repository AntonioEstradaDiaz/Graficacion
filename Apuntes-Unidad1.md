1. Introducción a la graficación por computadora

La graficación por computadora es el área de la informática encargada de la generación, manipulación y representación de imágenes mediante el uso de algoritmos y modelos matemáticos. Permite transformar datos numéricos en representaciones visuales comprensibles para el usuario.

La graficación puede clasificarse en:

Gráficos 2D

Gráficos 3D

Renderizado en tiempo real

Procesamiento de imágenes

Visualización científica

Actualmente es una disciplina fundamental en áreas como videojuegos, simuladores, diseño asistido por computadora y animación digital.

1.1 Historia y evolución de la graficación por computadora

La evolución de la graficación por computadora comenzó en la década de 1950 con el uso de osciloscopios para mostrar líneas simples.

Algunos hitos importantes incluyen:

1963: Ivan Sutherland desarrolla Sketchpad, considerado el primer sistema interactivo de gráficos por computadora.

Década de 1970: Desarrollo de gráficos vectoriales y primeras técnicas de renderizado.

Década de 1980: Aparición de estaciones de trabajo gráficas y software CAD.

Década de 1990: Popularización de gráficos 3D y aceleración por hardware.

Siglo XXI: Renderizado en tiempo real, motores gráficos avanzados y realidad virtual.

La evolución ha estado ligada al avance del hardware (GPU) y los algoritmos matemáticos aplicados a la representación visual.

1.2 Áreas de aplicación

La graficación por computadora tiene aplicaciones en múltiples campos:

Videojuegos y entretenimiento digital

Diseño industrial y arquitectura (CAD)

Animación y cine

Simuladores médicos y militares

Visualización científica

Realidad virtual y aumentada

Interfaces gráficas de usuario

En el ámbito educativo, permite comprender fenómenos matemáticos y físicos mediante representaciones visuales dinámicas.

1.3 Aspectos matemáticos de la graficación

La graficación por computadora se fundamenta en conceptos matemáticos como:

Álgebra lineal

Vectores

Matrices

Transformaciones lineales

Rotaciones, traslaciones y escalamiento

Geometría analítica

Ecuaciones de rectas y planos

Intersección de figuras

Cálculo de distancias

Trigonometría

Funciones seno y coseno

Ángulos y radianes

Proyecciones

Cálculo diferencial

Curvas paramétricas

Interpolación

Cálculo de normales para iluminación

Las transformaciones geométricas en gráficos 3D se realizan comúnmente mediante matrices de transformación 4x4.

1.4 Modelos del color: RGB, CMY, HSV y HSL

Los modelos de color permiten representar colores mediante valores numéricos.

RGB (Red, Green, Blue)

Modelo aditivo basado en luz.
Se utiliza en pantallas y dispositivos digitales.

Cada color se representa mediante la combinación de tres componentes:

Rojo (R)

Verde (G)

Azul (B)

Valores típicos: 0–255 por canal.

Ejemplo:
RGB(255, 0, 0) = Rojo puro.

CMY (Cyan, Magenta, Yellow)

Modelo sustractivo utilizado en impresión.
Se basa en la absorción de luz.

Cian

Magenta

Amarillo

Se relaciona inversamente con RGB.

HSV (Hue, Saturation, Value)

Modelo basado en percepción humana.

Hue (Matiz): Color base (0°–360°).

Saturation (Saturación): Intensidad del color.

Value (Valor): Brillo.

Es muy utilizado en edición digital y selección de colores.

HSL (Hue, Saturation, Lightness)

Similar a HSV pero usa luminosidad en lugar de valor.

Hue

Saturation

Lightness

Permite mayor control sobre iluminación perceptual.

Tutorial: Iluminación básica de un cubo en Blender

Abrir Blender.

Eliminar el cubo inicial si es necesario.

Agregar un nuevo cubo: Shift + A → Mesh → Cube.

Agregar una luz: Shift + A → Light → Point o Area.

Posicionar la luz sobre el cubo.

Ajustar intensidad en el panel de propiedades.

Activar modo Rendered para visualizar sombras.

Modificar material del cubo en la pestaña Material Properties.

Ajustar parámetros de Roughness y Metallic.

Renderizar con F12.

Este ejercicio permite comprender:

Normales de superficie.

Interacción luz-objeto.

Sombras.

Materiales.

1.5 Representación y trazo de líneas y polígonos

La representación gráfica básica comienza con el trazo de líneas.

Una línea en 2D puede representarse mediante:

Forma paramétrica

Algoritmo de Bresenham

Ecuación punto-pendiente

Los polígonos se definen como conjuntos de vértices conectados por segmentos de línea.

En gráficos por computadora, los polígonos son la base del modelado 3D, ya que los objetos complejos se construyen mediante mallas poligonales.

1.5.1 Formatos de imagen

Existen dos grandes tipos de imágenes:

Mapas de bits (Raster)

JPEG

PNG

BMP

GIF

Se basan en píxeles.

Imágenes vectoriales

SVG

EPS

PDF

Se basan en ecuaciones matemáticas.

Diferencia principal:
Raster pierde calidad al escalar.
Vector mantiene calidad al escalar.

Práctica: Dibujo de un polígono

Ejemplo conceptual en Python:
```python
import bpy
import math

def crear_poligono_2d(nombre, lados, radio):
    malla = bpy.data.meshes.new(nombre)
    objeto = bpy.data.objects.new(nombre, malla)

    bpy.context.collection.objects.link(objeto)

    vertices = []
    aristas = []
    
    for i in range(lados):
        angulo = 2 * math.pi * i / lados
        x = radio * math.cos(angulo)
        y = radio * math.sin(angulo)
        vertices.append((x, y, 0))

    for i in range(lados):
        aristas.append((i, (i + 1) % lados))

   
    malla.from_pydata(vertices, aristas, [])
    malla.update()
    
    bpy.ops.object.select_all(action='SELECT')
    bpy.ops.object.delete()
    crear_poligono_2d("Poligono2D", lados=6, radio=5)

```
Práctica: La Flor de la Vida

La Flor de la Vida es un patrón geométrico compuesto por múltiples círculos superpuestos.

Ejemplo básico:
```python
# tu código aquí
```
Este ejercicio permite aplicar:

Trigonometría

Ángulos

Repetición

Simetría

1.6 Procesamiento de mapas de bits

El procesamiento de mapas de bits implica manipular imágenes píxel por píxel.

Algunas operaciones comunes:

Conversión a escala de grises

Ajuste de brillo y contraste

Filtros (blur, sharpen)

Detección de bordes

Transformaciones geométricas

Las imágenes raster se almacenan como matrices de valores numéricos que representan intensidad de color.

El procesamiento digital de imágenes es ampliamente utilizado en:

Visión por computadora

Reconocimiento facial

Inteligencia artificial

Medicina digital

Conclusión

La graficación por computadora combina matemáticas, programación y diseño visual para generar representaciones digitales. Desde el trazo básico de líneas hasta el modelado e iluminación 3D, constituye una disciplina esencial en la informática moderna.

El conocimiento de modelos de color, transformaciones geométricas y procesamiento de imágenes permite desarrollar aplicaciones visuales avanzadas y comprender el funcionamiento interno de motores gráficos y sistemas digitales.

Bibliografía

Foley, J. D., van Dam, A., Feiner, S. K., & Hughes, J. F. (2014). Computer graphics: Principles and practice (3rd ed.). Addison-Wesley.

Hearn, D., & Baker, M. P. (2011). Computer graphics with OpenGL (4th ed.). Pearson.

Szeliski, R. (2010). Computer vision: Algorithms and applications. Springer.

Shirley, P. (2016). Fundamentals of computer graphics (4th ed.). CRC Press.

Blender Foundation. (2024). Blender manual. Recuperado de https://docs.blender.org
