# Conjetura de Collatz — Verificación y Exploración

**Herramientas computacionales para experimentar con la conjetura de Collatz: desde la verificación paso a paso de secuencias individuales, hasta futuras exploraciones sobre la estructura y el comportamiento de las trayectorias.**

---

## La conjetura

La conjetura de Collatz (también llamada problema $3n + 1$) es uno de los problemas abiertos más famosos de la matemática. La regla es simple:

$$
f(n) = \begin{cases} n / 2 & \text{si } n \text{ es par} \\ 3n + 1 & \text{si } n \text{ es impar} \end{cases}
$$

La conjetura afirma que, para **todo** entero positivo $n$, la aplicación iterada de $f$ eventualmente llega a 1. Nadie lo ha demostrado, pero tampoco se ha encontrado un contraejemplo — se ha verificado computacionalmente hasta números del orden de $10^{20}$.

---

## Contenido actual

### `Conjetura_Collatz.ipynb`

El notebook contiene una función que ejecuta la secuencia de Collatz para cualquier entero positivo, imprimiendo cada paso y el número total de iteraciones necesarias para llegar a 1.

| Función | Firma | Descripción |
|---------|-------|-------------|
| `collatz(n)` | `int → None` | Aplica la regla de Collatz iterativamente desde `n`, imprime cada valor intermedio y el conteo total de pasos. |

### Ejemplo

```python
collatz(5)
# 16
# 8
# 4
# 2
# 1
# Pasos = 5
```

La secuencia de 5 sube a 16 (vía $3 \times 5 + 1$) y luego desciende por divisiones sucesivas hasta 1 en 5 pasos.

---

## Direcciones de exploración

El proyecto está diseñado para crecer. Algunas líneas de investigación posibles:

- **Longitud de secuencias** — ¿Cómo se distribuye el número de pasos en función de $n$? ¿Hay patrones en los picos?
- **Valores máximos alcanzados** — ¿Qué tan alto sube la secuencia antes de colapsar a 1? ¿Existe relación entre $n$ y su altitud máxima?
- **Estructura de árboles inversos** — Construir el árbol de Collatz hacia atrás: ¿qué números convergen al mismo camino?
- **Comportamiento modular** — ¿Los residuos de $n$ módulo algún número predicen la longitud o forma de la trayectoria?
- **Visualización de trayectorias** — Grafos, espirales o mapas de calor que revelen patrones no evidentes en la secuencia numérica.
- **Conexiones con otros problemas** — Relación con los primos, con secuencias binarias, o con dinámica discreta.

---

## Estructura del proyecto

```
Collatz/
├── README.md
└── Conjetura_Collatz.ipynb   # Función de verificación + ejemplos
```

---

## Requisitos

```
python 3.x
```

No requiere dependencias externas.
