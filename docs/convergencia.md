# 📈 Análisis de Convergencia

## Método Iterativo

El método de Newton-Raphson multivariable aproxima progresivamente la solución del sistema no lineal mediante correcciones sucesivas calculadas con la matriz Jacobiana.

La convergencia se controla mediante el cálculo del error:

$$
\text{Error} =
\sqrt{
f_1^2 + f_2^2
}
$$

El programa detiene las iteraciones cuando el error es menor que la tolerancia establecida:

$$
10^{-6}
$$

---

## 📊 Resultados de la Ejecución

La ejecución del programa mostró convergencia estable después de 3 iteraciones.

| Variable | Resultado |
|---|---|
| Radio orbital $(r)$ | 0.8245631608 |
| Iteraciones realizadas | 3 |
| Tolerancia alcanzada | $10^{-6}$ |

---

## 📌 Interpretación

Los resultados obtenidos muestran que el método converge rápidamente utilizando valores iniciales adecuados.

La matriz Jacobiana permite calcular las correcciones necesarias en cada iteración para aproximar la solución del sistema.

El uso de programación en C automatiza el proceso numérico y reduce considerablemente el tiempo de cálculo.