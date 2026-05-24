# 📐 Teoría Matemática: Método de Newton-Raphson Multivariable

## Introducción

Para calcular la posición aproximada del asteroide Apophis se utilizó el método de Newton-Raphson multivariable.

Este método numérico permite resolver sistemas de ecuaciones no lineales mediante aproximaciones sucesivas.

En lugar de obtener la solución directamente, el algoritmo comienza con valores iniciales y los va corrigiendo poco a poco hasta reducir el error.

Las variables principales son:

- $(E)$ → anomalía excéntrica.
- $(r)$ → distancia radial respecto al Sol.

Las ecuaciones del sistema son:

$$
f_1(E,r)=E-e\sin(E)-M
$$

$$
f_2(E,r)=r-a(1-e\cos(E))
$$

donde:

| Variable | Significado |
|---|---|
| $e$ | Excentricidad orbital |
| $a$ | Semieje mayor |
| $M$ | Anomalía media |
| $E$ | Anomalía excéntrica |
| $r$ | Distancia radial |

---

## 🔄 ¿Cómo funciona Newton-Raphson?

El método toma una aproximación inicial y realiza correcciones iterativas.

En cada iteración:

1. Se evalúan las ecuaciones.
2. Se calcula el Jacobiano.
3. Se obtiene la corrección numérica.
4. Se actualizan los valores.
5. El error disminuye progresivamente.

El proceso continúa hasta alcanzar una tolerancia pequeña.
