# 💻 Implementación en Lenguaje C

## Código Fuente

```c
#include <stdio.h>
#include <math.h>

int main() {

    double e = 0.19116634;
    double a = 0.92238032;
    double M = 5.4595;

    double E = 5.4;
    double r = 0.80;

    double f1, f2;
    double J11, J12, J21, J22;
    double det;

    double inv11, inv12, inv21, inv22;

    double deltaE, deltar;

    double tolerancia = 1e-6;
    double error = 10.0;

    int iteracion = 0;
    int maxIter = 100;

    while(error > tolerancia && iteracion < maxIter) {

        f1 = E - e * sin(E) - M;

        f2 = r - a * (1 - e * cos(E));

        J11 = 1 - e * cos(E);
        J12 = 0;

        J21 = -a * e * sin(E);
        J22 = 1;

        det = (J11 * J22) - (J12 * J21);

        inv11 = J22 / det;
        inv12 = -J12 / det;

        inv21 = -J21 / det;
        inv22 = J11 / det;

        deltaE = inv11 * f1 + inv12 * f2;

        deltar = inv21 * f1 + inv22 * f2;

        E = E - deltaE;

        r = r - deltar;

        error = sqrt((f1 * f1) + (f2 * f2));

        printf("\\nIteracion: %d\\n", iteracion + 1);

        printf("E = %.10f\\n", E);

        printf("r = %.10f\\n", r);

        printf("Error = %.10lf\\n", error);

        iteracion++;
    }

    printf("\\n==============================\\n");

    printf("RESULTADOS FINALES\\n");

    printf("==============================\\n");

    printf("Anomalia Excentrica (E): %.10f\\n", E);

    printf("Radio Orbital (r): %.10f\\n", r);

    printf("Iteraciones realizadas: %d\\n", iteracion);

    printf("Tolerancia alcanzada: %.10e\\n", tolerancia);

    return 0;
}
```

---

# 📥 Entrada del Programa

| Parámetro | Valor |
|---|---|
| Excentricidad $(e)$ | 0.19116634 |
| Semieje mayor $(a)$ | 0.92238032 |
| Anomalía media $(M)$ | 5.4595 |
| Valor inicial de $(E)$ | 5.4 |
| Valor inicial de $(r)$ | 0.80 |

---

# 📤 Salida del Programa

```text
RESULTADOS FINALES

Anomalia Excentrica (E): 5.2988849621
Radio Orbital (r): 0.8245631608
Iteraciones realizadas: 3
Tolerancia alcanzada: 1.0000000000e-06
```