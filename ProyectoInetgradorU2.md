# Guía de Proceso: Animación de Walk Cycle Frame a Frame

Este documento detalla el flujo de trabajo seguido para la creación de una animación de ciclo de caminata (*walk cycle*) en 2D utilizando Blender. El enfoque principal es el dibujo manual (calcado) basado en referencias generadas por inteligencia artificial.

## 1. Conceptualización y Referencia
El primer paso consistió en definir la estructura del movimiento. En lugar de utilizar una referencia estándar de internet, se utilizó **Inteligencia Artificial** para generar una hoja de poses (*pose sheet*) personalizada.

* **Uso de IA:** Se generó una secuencia de poses que definen la personalidad del personaje (un tigre en este caso).
* **Guía de Poses:** La referencia resultante se organizó para identificar claramente los cuatro momentos clave de la caminata:
    1.  **Contacto (Contact):** Ambos pies tocan el suelo.
    2.  **Bajada (Down):** El punto de máxima presión donde el cuerpo absorbe el impacto.
    3.  **Paso (Passing):** Una pierna cruza a la otra.
    4.  **Subida (Up):** El punto más alto antes del siguiente paso.

       ![Guía de Poses del Tigre](tiger_poses.png)

       

## 2. Metodología en Blender
Para tener un control total sobre la estética y la topografía de la animación, se optó por un método de **trazado manual (calcado)** en lugar de utilizar herramientas de vectorización automática.

### Configuración del Espacio de Trabajo
1.  **Importación de Referencia:** Se coloca la imagen de la guía de poses en el fondo del *viewport* de Blender (como un *Empty* o *Background Image*).
2.  **Grease Pencil / Trazado:** Se utiliza una capa de dibujo para realizar el trazado de cada frame.
3.  **Papel Cebolla (Onion Skinning):** Esta herramienta es vital para visualizar el frame anterior y posterior, permitiendo ajustar la fluidez del movimiento y mantener la consistencia del volumen del personaje.

## 3. Proceso de Animación Paso a Paso

### Fase A: Bloqueo de Poses Clave (Blocking)
Se dibujan primero las poses de "Contacto" y "Paso". Esto establece el ritmo y la distancia que recorre el personaje. Es fundamental asegurar que la animación sea cíclica (que el último frame conecte perfectamente con el primero).

### Fase B: Adición de Extremas (Down & Up)
Una vez que el ritmo base es correcto, se añaden las poses de "Bajada" y "Subida". Aquí es donde se le da "peso" al personaje; si el cuerpo no baja lo suficiente en el contacto, la caminata se siente rígida.

### Fase C: Refinamiento Frame a Frame
Se revisa la secuencia completa eliminando imperfecciones en el trazo y asegurando que las partes del cuerpo (cola, orejas, etc.) sigan leyes de inercia o movimiento secundario.

## 4. Notas Técnicas
* **FPS (Frames per Second):** La animación se trabajó a [insertar aquí tus FPS, ej: 24 fps] para lograr una sensación de movimiento suave pero con estilo tradicional.
* **Ciclo Infinito:** Para verificar el loop en Blender, se utiliza el modificador de ciclos en las curvas de animación o simplemente se repiten los frames en la línea de tiempo.

---
**Elaborado por:** Estrada Diaz Antonio  
**Carrera:** Ingeniería en Sistemas Computacionales  
**Propósito:** Documentación de práctica de animación 2D y uso de referencias asistidas por IA.
