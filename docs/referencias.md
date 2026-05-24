# 📚 Referencias y Fuentes de Información

## Introducción

Para desarrollar este proyecto se consultaron bases de datos astronómicas oficiales, documentación científica y material relacionado con mecánica orbital y métodos numéricos.

Los parámetros orbitales utilizados para la simulación del asteroide Apophis fueron tomados y adaptados a las unidades empleadas en el programa desarrollado en C.

---

# 🌎 Bases de Datos Astronómicas

## NASA JPL Small-Body Database

Base de datos oficial utilizada para obtener información orbital del asteroide 99942 Apophis.

- [NASA CNEOS](https://cneos.jpl.nasa.gov/)

- [Base de datos orbital de Apophis](https://ssd.jpl.nasa.gov/tools/sbdb_lookup.html#/?sstr=99942)

- [ESA](https://www.esa.int/)

Datos consultados:

- Excentricidad orbital
- Semieje mayor
- Parámetros orbitales
- Información del acercamiento de 2029

---

# 📖 Referencias Matemáticas

## Método de Newton-Raphson

Se utilizó bibliografía y teoría de métodos numéricos para implementar el algoritmo iterativo multivariable.

Temas utilizados:

- Sistemas no lineales
- Jacobiano
- Derivadas parciales
- Convergencia numérica
- Tolerancia de error

---

# 🛰️ Referencias sobre Mecánica Orbital

## Leyes de Kepler

Las ecuaciones orbitales implementadas en el proyecto se basan en:

1. Primera Ley de Kepler
2. Segunda Ley de Kepler
3. Ecuación de Kepler

La ecuación principal utilizada fue:



---

# 💻 Herramientas Utilizadas

| Herramienta | Uso |
|---|---|
| Lenguaje C | Implementación del algoritmo |
| GCC | Compilación del programa |
| Visual Studio Code | Desarrollo del proyecto |
| MkDocs Material | Documentación web |
| MathJax | Renderizado matemático |
| Chart.js | Gráficas del simulador |

---

# 📌 Observaciones

Algunos valores fueron redondeados para facilitar las simulaciones numéricas y mantener estabilidad en las iteraciones del método de Newton-Raphson.

El objetivo del proyecto es educativo y busca mostrar cómo los métodos numéricos pueden aplicarse al cálculo orbital y a la simulación de trayectorias astronómicas.