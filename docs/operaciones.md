# 🧮 Operaciones Numéricas

## Sistema No Lineal

$$
f_1(E,r)=E-e\sin(E)-M
$$

$$
f_2(E,r)=r-a(1-e\cos(E))
$$

---

## Matriz Jacobiana

$$
J=
\begin{bmatrix}
1-e\cos(E) & 0 \\
-ae\sin(E) & 1
\end{bmatrix}
$$

---

## Sustitución Numérica

$$
J=
\begin{bmatrix}
0.878668 & 0 \\
0.136279 & 1
\end{bmatrix}
$$

---

## Determinante

$$
\det(J)=0.878668
$$

---

## Matriz Inversa

$$
J^{-1}=
\begin{bmatrix}
1.138086 & 0 \\
-0.155097 & 1
\end{bmatrix}
$$

---

## Fórmula de Actualización

$$
\mathbf{x}_{n+1}
=
\mathbf{x}_n
-
J^{-1}\mathbf{F}(\mathbf{x}_n)
$$

---

## Resultados del Programa

| Variable | Resultado |
|---|---|
| Radio orbital $(r)$ | 0.8245631608 |
| Iteraciones | 3 |
| Tolerancia | $10^{-6}$ |