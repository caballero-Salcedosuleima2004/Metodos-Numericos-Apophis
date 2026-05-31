# 📈 Convergencia

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

La ejecución del programa convergio despues de 3 iteraciones.

| Variable | Resultado |
|---|---|
| Radio orbital $(r)$ | 0.8245631608 |
| Iteraciones realizadas | 3 |
| Tolerancia alcanzada | $10^{-6}$ |

---

## Interpretación

Como conclusión, vimos que el método converge bastante rápido si le metemos valores iniciales buenos. La matriz Jacobiana hace bien su trabajo calculando las correcciones en cada iteración para irnos acercando a la solución. Además, haberlo programado en C nos ahorró muchísimo tiempo, ya que automatiza todo el proceso numérico de golpe.