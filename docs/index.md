# ☄️ Proyecto: Defensa Planetaria – Asteroide Apophis

## Introducción

Este proyecto implementa el método de Newton-Raphson multivariable para aproximar la trayectoria orbital del asteroide 99942 Apophis mediante ecuaciones no lineales basadas en las leyes de Kepler.

La simulación fue desarrollada en lenguaje C y permite calcular numéricamente la anomalía excéntrica y la distancia radial del asteroide utilizando procesos iterativos.

---

## 🎯 Objetivo del Proyecto

El objetivo principal es aplicar métodos numéricos para resolver ecuaciones orbitales que no pueden despejarse algebraicamente de forma directa.

El proyecto integra:

- Métodos numéricos.
- Álgebra matricial.
- Programación en C.
- Modelado orbital.
- Uso de matrices jacobianas.

---

## ☄️ Asteroide 99942 Apophis

Apophis es un asteroide cercano a la Tierra clasificado como NEO (Near Earth Object).

El 13 de abril de 2029 realizará uno de los acercamientos más importantes registrados para un objeto de este tipo.

| Parámetro | Valor Aproximado |
|---|---|
| Diámetro | 370 m |
| Velocidad aproximada | 30 km/s |
| Fecha de acercamiento | 13 de abril de 2029 |
| Distancia estimada | ~32000 km |

---

## 🧠 Método Utilizado

Para aproximar la solución orbital se utilizó el método de Newton-Raphson multivariable aplicado al siguiente sistema no lineal:

$$
f_1(E,r)=E-e\sin(E)-M
$$

$$
f_2(E,r)=r-a(1-e\cos(E))
$$

<div align="center">
  <video width="100%" style="max-width: 800px; border-radius: 15px; box-shadow: 0 10px 30px rgba(0,255,255,0.3);" autoplay muted loop playsinline>
    <source src="assets/60700-495934974_medium.mp4" type="video/mp4">
    Tu navegador no soporta la reproducción de videos.
  </video>
</div>

El proceso iterativo se ejecuta automáticamente mediante programación en lenguaje C hasta alcanzar una tolerancia de:

$$
10^{-6}
$$