# Unidad 2: Gráficos Bidimensionales y Transformaciones

Este documento detalla los fundamentos teóricos sobre las transformaciones en el plano, la representación matricial, el trazado de curvas, fractales y el manejo de fuentes tipográficas, orientado a la Ingeniería en Sistemas Computacionales.

---

## 2.1. Transformación Bidimensional
Las transformaciones geométricas permiten alterar la posición, el tamaño o la orientación de un objeto en un plano $XY$.

### 2.1.1. Traslación
Consiste en desplazar un objeto a lo largo de una trayectoria recta de una ubicación de coordenadas a otra.
* **Ecuaciones:** $x' = x + t_x$
    $y' = y + t_y$
Donde $(t_x, t_y)$ es el vector de traslación.

### 2.1.2. Escalamiento
Cambia el tamaño de un objeto. Un factor de escala mayor a 1 aumenta el tamaño, mientras que uno menor a 1 lo reduce.
* **Ecuaciones:**
    $x' = x \cdot s_x$
    $y' = y \cdot s_y$

### 2.1.3. Rotación
Gira un objeto alrededor de un punto pivote (generalmente el origen) mediante un ángulo $\theta$.
* **Ecuaciones:**
    $x' = x \cos(\theta) - y \sin(\theta)$
    $y' = y \sin(\theta) + x \cos(\theta)$

### 2.1.4. Sesgado (Shearing)
Transformación que distorsiona la forma de un objeto, haciendo que parezca que sus capas se deslizan unas sobre otras. Puede aplicarse en dirección $X$ o $Y$.

---

## 2.2. Representación Matricial de las Transformaciones
Para realizar secuencias de transformaciones de manera eficiente, se utilizan **coordenadas homogéneas**, lo que permite representar todas las operaciones como multiplicaciones de matrices de $3 \times 3$.

La matriz de traslación se representa así:
$$
\begin{bmatrix} 
x' \\ 
y' \\ 
1 
\end{bmatrix} = 
\begin{bmatrix} 
1 & 0 & t_x \\ 
0 & 1 & t_y \\ 
0 & 0 & 1 
\end{bmatrix} \cdot 
\begin{bmatrix} 
x \\ 
y \\ 
1 
\end{bmatrix}
$$

> ###  Ejercicio de Control: Teclas de Dirección
> En aplicaciones interactivas, la traslación se vincula a eventos del teclado. Por ejemplo, al presionar `Flecha Derecha`, incrementamos el valor de $t_x$ en la matriz de transformación, provocando que el renderizado mueva el objeto hacia la derecha en cada ciclo de actualización (*update loop*).

---

## 2.3. Trazo de Líneas Curvas
En gráficos por computadora, las curvas se definen matemáticamente mediante puntos de control para ahorrar memoria y permitir escalabilidad.

### 2.3.1. Bézier
Se basan en polinomios de Bernstein. La curva pasa por los puntos inicial y final, mientras que los puntos intermedios determinan la forma de la curvatura pero no necesariamente tocan la línea.

### 2.3.2. B-spline
Ofrecen mayor flexibilidad que las de Bézier porque permiten **control local**: mover un punto de control solo afecta a una sección de la curva, no a toda la figura.

> ### Ejercicio: Dibujo de la Animación (Walk Cycle)
> Para la animación de "Walk Cycle" realizada (ej. el tigre o el gato), se utilizan estas curvas para definir el flujo del movimiento en las articulaciones. Al interpolar las posiciones de los puntos de control frame a frame, se logra un movimiento fluido y natural en el trazado manual.

---

## 2.4. Fractales
Los fractales son estructuras geométricas complejas caracterizadas por la **autosimilitud** (se ven iguales a cualquier escala). Se generan mediante algoritmos recursivos.
* **Aplicaciones:** Generación de paisajes naturales, nubes, texturas de piel y follaje en videojuegos.

---

## 2.5. Uso y Creación de Fuentes de Texto
El texto en sistemas gráficos se divide principalmente en dos tipos:
1.  **Fuentes de Mapa de Bits (Bitmap):** Se definen como una matriz de píxeles. Son rápidas pero se "pixelean" al escalarlas.
2.  **Fuentes Vectoriales (Outline):** Se definen mediante curvas (generalmente Bézier). Pueden escalarse infinitamente sin perder nitidez. Su creación implica definir los nodos y curvas de cada glifo en un editor tipográfico.

---

## Referencias Bibliográficas

* Hearn, D., & Baker, M. P. (2006). *Gráficos por computadora con OpenGL* (3ra ed.). Pearson Educación.
* Hughes, J. F., Van Dam, A., Foley, J. D., & Feiner, S. K. (2014). *Computer Graphics: Principles and Practice*. Addison-Wesley Professional.
* Watt, A. (2000). *3D Computer Graphics*. Addison-Wesley.
