# ☄️ Análisis de Impacto: Asteroide Apophis 99942

## ¿Para qué sirve realmente este programa?

Para poder calcular dónde estará el Asteroide y qué trayectoria sigue alrededor del Sol.

El problema es que las ecuaciones que describen su movimiento no se pueden resolver fácilmente con una fórmula directa. Por eso se usan métodos numéricos como Newton-Raphson.

Lo que hace este programa es tomar una aproximación inicial de la posición del asteroide e ir corrigiéndola poco a poco hasta encontrar un resultado mucho más preciso.

---

## 🧮 ¿Qué está calculando el método?

El programa calcula principalmente dos cosas:

### La posición del asteroide en su órbita

Esto se representa con la anomalía excéntrica $(E)$.

Básicamente sirve para saber en qué parte de la órbita se encuentra el asteroide en un momento determinado.

---

### La distancia del asteroide respecto al Sol

Esto se representa con la variable $(r)$.

Ese valor indica qué tan lejos está Apophis del Sol durante la simulación.

---

## 🔄 ¿Qué significa que el método converja?

Al iniciar el programa, los valores iniciales todavía no son exactos.

Entonces el método de Newton-Raphson comienza a corregir esos números iteración por iteración.

En cada paso el error se hace más pequeño hasta que el programa encuentra una solución precisa.

En este caso el método convergió en 3 iteraciones, lo que significa que:

- el programa encontró rápidamente una solución estable,
- el error se redujo casi a cero,
- y los resultados obtenidos ya son bastante precisos para el modelo utilizado.

---

## 📈 Resultados Obtenidos

| Variable | Resultado |
|---|---|
| Anomalía excéntrica $(E)$ | 5.2988849621 |
| Radio orbital $(r)$ | 0.8245631608 |
| Iteraciones realizadas | 3 |
| Tolerancia alcanzada | $10^{-6}$ |

---

## 📌 ¿Qué significan estos resultados?

El valor de $(E)$ indica la posición aproximada del asteroide dentro de su órbita.

El valor de $(r)$ indica que, durante la simulación, Apophis se encontraba aproximadamente a:

$$
0.8245631608 \text{ UA}
$$

del Sol.

La parte importante del proyecto no es solamente obtener números, sino demostrar cómo un método numérico puede resolver problemas que serían muy difíciles de hacer manualmente.

---

## 💻 Importancia del programa

Sin métodos numéricos, resolver este tipo de ecuaciones orbitales tomaría muchísimo tiempo y sería muy complicado hacerlo a mano.

La programación en C permite automatizar todos los cálculos y obtener resultados precisos en pocos segundos.

Este tipo de procedimientos se utilizan en simulaciones orbitales y estudios astronómicos para analizar trayectorias de objetos cercanos a la Tierra.