# ☄️ Proyecto: Asteroide Apophis

## Introducción

Para este proyecto elegimos el asteroide Apophis y usamos las leyes de Kepler para ver su trayectoria. Como son ecuaciones no lineales y no se pueden resolver exactas, aplicamos lo que siempre nos dice el profe: que los métodos numéricos son para aproximar. Así que armamos un código en C con el método de Newton-Raphson multivariable para ir calculando, paso a paso, la anomalía excéntrica y la distancia radial."

---

## El proyecto integra:

- Métodos numéricos.
- Álgebra matricial.
- Programación en C.
- Modelado orbital.
- Uso de matrices jacobianas.

---

## ☄️ Asteroide 99942 Apophis

Elegimos a Apophis porque es un asteroide cercano a la Tierra, de los que se clasifican como NEO. 

Lo interesante de este objeto es que el 13 de abril de 2029 va a realizar uno de los acercamientos más importantes y cercanos que se tengan registrados.

| Parámetro | Valor Aproximado |
|---|---|
| Diámetro | 370 m |
| Velocidad aproximada | 30 km/s |
| Fecha de acercamiento | 13 de abril de 2029 |
| Distancia estimada | ~32000 km |

---

## Método Utilizado

Para aproximar la solución orbital se utilizó el método de Newton-Raphson multivariable aplicado al siguiente sistema no lineal:

$$
f_1(E,r)=E-e\sin(E)-M
$$

$$
f_2(E,r)=r-a(1-e\cos(E))
$$

<div align="center">
  <video width="100%" style="max-width: 800px; border-radius: 15px; box-shadow: 0 10px 30px rgba(0,255,255,0.3);" autoplay muted loop playsinline>
    <source src="assets/292107_medium(1).mp4" type="video/mp4">
    Tu navegador no soporta la reproducción de videos.
  </video>
</div>

El proceso iterativo se ejecuta mediante programación en lenguaje C hasta alcanzar una tolerancia de:

$$
10^{-6}
$$