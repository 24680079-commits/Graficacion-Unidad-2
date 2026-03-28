# Graficacion-Unidad-2

# Graficación 2D

La graficación 2D es una rama de la computación gráfica que se encarga de representar objetos en un plano bidimensional utilizando coordenadas (X, Y). Este tipo de graficación es fundamental en aplicaciones como interfaces gráficas, videojuegos, simulaciones y diseño digital.

---

## 2.1 Transformación Bidimensional

Las transformaciones bidimensionales permiten modificar la posición, orientación o tamaño de los objetos en el plano cartesiano. Estas transformaciones son esenciales en gráficos por computadora para manipular figuras de forma eficiente.

---

### 2.1.1 Traslación

La traslación consiste en desplazar una figura de una posición a otra sin alterar su forma ni su tamaño.

#### Fórmulas:

x' = x + dx  
y' = y + dy  

Donde:
- dx = desplazamiento en X  
- dy = desplazamiento en Y  

#### Ejemplo:

Punto original:
P(2, 3)

Traslación: dx = 4, dy = 2

Resultado:
P'(6, 5)

---

### 2.1.2 Escalamiento

El escalamiento modifica el tamaño de una figura, ya sea ampliándola o reduciéndola.

#### Fórmulas:

x' = x * Sx  
y' = y * Sy  

Donde:
- Sx, Sy = factores de escala  

#### Ejemplo:

Punto original:
P(3, 4)

Escalamiento: Sx = 2, Sy = 2

Resultado:
P'(6, 8)

Si el factor es menor a 1, la figura se reduce.

---

### 2.1.3 Rotación

La rotación permite girar una figura alrededor de un punto, generalmente el origen.

#### Fórmulas:

x' = x cos(θ) - y sin(θ)  
y' = x sin(θ) + y cos(θ)  

Donde:
- θ = ángulo de rotación  

#### Ejemplo:

Punto:
P(1, 0)

Rotación de 90°

Resultado:
P'(0, 1)

---

### 2.1.4 Sesgado (Shear)

El sesgado transforma una figura inclinándola en el eje X o Y.

#### Fórmulas:

En X:
x' = x + Shx * y  

En Y:
y' = y + Shy * x  

#### Ejemplo:

Punto:
P(2, 3)

Sesgado en X con Shx = 1:

x' = 2 + (1)(3) = 5  

Resultado:
P'(5, 3)

---

## 2.2 Representación Matricial de Transformaciones Bidimensionales

Las transformaciones se representan mediante matrices para facilitar su implementación en sistemas computacionales. Se utilizan coordenadas homogéneas agregando una tercera componente (1).

#### Ejemplo de matriz de traslación:

| 1  0  dx |
| 0  1  dy |
| 0  0  1  |

Punto:

| x |
| y |
| 1 |

Resultado:

P' = T * P

#### Ejemplo en Python:

```python
import numpy as np

# Punto original
p = np.array([2, 3, 1])

# Matriz de traslación
T = np.array([
    [1, 0, 4],
    [0, 1, 2],
    [0, 0, 1]
])
```

# Resultado
p_prima = T @ p
print(p_prima)

## 2.3 Trazo de Líneas Curvas

Las curvas permiten representar formas suaves y continuas en gráficos por computadora.

2.3.1 Curvas de Bézier

Las curvas de Bézier se definen mediante puntos de control y permiten modelar trayectorias suaves.

Fórmula cuadrática:

B(t) = (1 - t)^2 P0 + 2(1 - t)t P1 + t^2 P2

Donde:

t ∈ [0,1]
Ejemplo:

Puntos:
P0 = (0,0)
P1 = (1,2)
P2 = (3,0)
```
import numpy as np

def bezier(t, P0, P1, P2):
    return (1-t)**2 * P0 + 2*(1-t)*t * P1 + t**2 * P2

print(bezier(0.5, np.array([0,0]), np.array([1,2]), np.array([3,0]))
```

2.3.2 B-Spline

Las curvas B-Spline son generalizaciones de las curvas de Bézier que permiten mayor control sobre la forma de la curva.

Características:
Mayor suavidad
Control local
No dependen de todos los puntos de control
Aplicaciones:
Diseño asistido por computadora (CAD)
Modelado geométrico
Animación
## 2.4 Fractales

Los fractales son estructuras geométricas que presentan auto-similitud, es decir, sus partes son similares al todo a diferentes escalas.

Características:
Detalle infinito
Patrones repetitivos
Generación mediante algoritmos iterativos
Ejemplo: Conjunto de Mandelbrot
```
import numpy as np

def mandelbrot(c, max_iter):
    z = 0
    for i in range(max_iter):
        z = z*z + c
        if abs(z) > 2:
            return i
    return max_iter

print(mandelbrot(complex(0.3, 0.5), 100))
```

## 2.5 Uso y Creación de Fuentes de Texto

Las fuentes permiten representar caracteres dentro de un sistema gráfico.

Tipos de fuentes:
Bitmap: basadas en píxeles
Vectoriales: escalables sin pérdida de calidad
Formatos comunes:
TrueType (TTF)
OpenType (OTF)

Las fuentes vectoriales utilizan líneas y curvas para definir caracteres, lo que permite su escalabilidad en diferentes resoluciones sin pérdida de calidad.

## Bibliografía 
Foley, J. D., van Dam, A., Feiner, S. K., & Hughes, J. F. (1996). Computer Graphics: Principles and Practice. Addison-Wesley.
Hearn, D., & Baker, M. P. (2010). Computer Graphics with OpenGL (4th ed.). Pearson.
Angel, E., & Shreiner, D. (2015). Interactive Computer Graphics: A Top-Down Approach with WebGL (7th ed.). Addison-Wesley.
Rogers, D. F. (2001). An Introduction to NURBS: With Historical Perspective. Morgan Kaufmann.
Sederberg, T. W. (2012). Computer Aided Geometric Design. Brigham Young University.
