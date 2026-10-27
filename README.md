# Interpoladores: lineal a tramos, Lagrange y splines cúbicas

Proyecto personal en el que implemento y comparo tres métodos de interpolación
para mostrar su funcionamiento, sus ventajas y sus limitaciones: primero con una
función conocida y después con datos reales.

> Interpolar es estimar un valor que no medimos, pero que está entre datos que
> sí conocemos.

## Contenido

| Sección | Qué se hace |
|---|---|
| **Interpolación lineal a tramos** | Une puntos vecinos con rectas usando `np.interp`. |
| **Polinomio de Lagrange** | Implementación desde cero de los polinomios base $\ell_k(x)$ y del interpolante $p(x)=\sum y_k\,\ell_k(x)$. |
| **Splines cúbicas** | Spline cúbica natural con `scipy.interpolate.CubicSpline`, con continuidad en altura, pendiente y curvatura. |
| **Comparación** | Los tres métodos sobre 6 puntos de $\sin(x)$, evaluados con el error cuadrático medio (ECM). |
| **Fenómeno de Runge** | Con $f(x)=1/(1+25x^2)$ se muestra cómo Lagrange oscila en los bordes al aumentar los puntos, mientras la spline converge. |
| **El pato** | Reconstrucción del contorno de un pato (Burden y Faires, tabla 3.18) con 21 puntos. |
| **Datos reales** | Temperatura mínima diaria en Melbourne (1981–1990): se ocultan días, se reconstruyen con cada método y se mide el error. |
| **Aplicaciones** | Imputación de series de tiempo, meteorología, gráficos por computadora, imágenes, finanzas, robótica y audio. |

## Resultados principales

**Sobre $\sin(x)$ con 6 puntos (ECM):**

| Método | ECM |
|---|---|
| Lineal a tramos | 0.00966 |
| Lagrange (grado 5) | 0.00013 |
| Spline cúbica | 0.00002 |

**Fenómeno de Runge (error máximo):**

| Puntos | Lagrange | Spline |
|---|---|---|
| 6 | 0.433 | 0.423 |
| 11 | 1.916 | 0.022 |
| 16 | 2.104 | 0.031 |

**Temperatura en Melbourne** (se conserva 1 de cada 3 días y se estiman los 40 ocultos):

| Método | ECM | Error típico (°C) |
|---|---|---|
| Lineal a tramos | 4.57 | 2.14 |
| Lagrange (grado 20) | 918 873.10 | 958.58 |
| Spline cúbica | 4.83 | 2.20 |

## Conclusiones

- La interpolación **lineal a tramos** es simple y robusta, pero deja esquinas.
- Un solo **polinomio de Lagrange** funciona con pocos puntos, pero con muchos
  puntos igualmente espaciados oscila en los bordes (fenómeno de Runge).
- Las **splines cúbicas** trabajan por tramos y empalman suavemente; evitan las
  oscilaciones y reconstruyen formas como el lomo del pato.
- Con datos reales y ruidosos, pasar exactamente por todos los puntos no siempre
  es buena idea: hay que esconder datos y medir el error, igual que con cualquier
  modelo de aprendizaje automático.

## Cómo ejecutarlo

```bash
pip install -r requirements.txt
jupyter notebook interpolacion.ipynb
```

También funciona directamente en Google Colab. Los datos de temperatura se
descargan desde una URL pública, así que no hace falta subir archivos.

## Tecnologías

Python · NumPy · pandas · Matplotlib · SciPy · Jupyter / Google Colab

## Referencias

- Burden, R. L. y Faires, J. D. *Análisis numérico*.
- Datos: [Daily minimum temperatures in Melbourne](https://github.com/jbrownlee/Datasets/blob/master/daily-min-temperatures.csv).

---

`#Python` `#NumPy` `#Pandas` `#Matplotlib` `#SciPy` `#Jupyter` `#GoogleColab`
`#Interpolacion` `#Lagrange` `#Splines` `#SplinesCubicas` `#FenomenoDeRunge`
`#MetodosNumericos` `#AnalisisNumerico` `#SeriesDeTiempo` `#ImputacionDeDatos`
`#MachineLearning` `#AprendizajeAutomatico` `#CienciaDeDatos` `#DataScience`
