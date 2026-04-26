# Números Primos — Herramientas y Exploración Geométrica

**Un laboratorio computacional para investigar números primos: funciones de identificación y generación, un dataset de más de 3 millones de primos, y un espacio de experimentación abierto donde se prueban distintas transformaciones matemáticas en busca de patrones ocultos.**

---

## Motivación

Los números primos son, posiblemente, el objeto más estudiado y menos comprendido de la matemática. No existe una expresión analítica cerrada que los genere todos, y su distribución aparenta ser caótica a simple vista. Sin embargo, la historia de la teoría de números demuestra que detrás de esa aparente aleatoriedad se esconden regularidades extraordinarias.

Este proyecto ataca el problema desde dos frentes:

1. **Herramientas computacionales** — Un conjunto de funciones para identificar, generar y navegar números primos de forma eficiente.
2. **Exploración experimental** — Pruebas de comportamiento de los primos bajo distintas transformaciones matemáticas, buscando patrones que no son visibles en la recta numérica.

La primera línea de exploración proyecta los primos sobre la circunferencia unitaria vía $p \mod \pi$, pero el proyecto está diseñado para incorporar nuevos enfoques a medida que se descubran avenidas prometedoras — ya sean algebraicas, geométricas, espectrales u otras.

---

## Arquitectura del proyecto

```
Numeros_Primos/
├── README.md
├── Proyecto_Primos.ipynb    # Funciones fundamentales + generación del dataset
├── Aplicaciones.ipynb       # Exploración experimental del comportamiento de los Primos.
└── primos.csv               # ~3 millones de primos hasta 50,000,000
```

---

## Notebook 1 — Funciones fundamentales

`Proyecto_Primos.ipynb` contiene un toolkit completo para trabajar con números primos:

| Función | Firma | Descripción |
|---------|-------|-------------|
| `Prime(n)` | `int → bool` | Determina si `n` es primo. Optimizada: descarta pares, múltiplos de 3 y 5, y solo prueba divisores impares hasta $\sqrt{n}$. |
| `List_Prime_numbers(m, n)` | `int, int → list` | Genera todos los primos en el rango $[m, n]$. |
| `Next_Prime(n)` | `int → int` | Encuentra el primo inmediatamente posterior a `n`. |
| `Previous_Prime(n)` | `int → int` | Encuentra el primo inmediatamente anterior a `n`. |
| `Previous_Next_Prime(n)` | `int → tuple` | Devuelve la pareja (primo anterior, primo siguiente) a `n`. |
| `First_Prime_Numbers(n)` | `int → list` | Genera los primeros `n` números primos. |

Todas las funciones incluyen validación de entrada (tipo, rango, casos borde).

### Generación del dataset

El notebook incluye un bloque que genera el archivo `primos.csv` iterando en ventanas de 100,000 números hasta los 50 millones, escribiendo en modo append para evitar mantener toda la lista en memoria:

```
0 → 100,000 → 200,000 → ... → 50,000,000
       ↓           ↓                 ↓
   List_Prime   List_Prime      List_Prime
       ↓           ↓                 ↓
       └─── append al CSV ───────────┘
```

**Resultado:** `primos.csv` — 3,001,134 números primos, desde el 2 hasta el 49,999,991.

---

## Notebook 2 — Aplicaciones y exploración

`Aplicaciones.ipynb` contiene pruebas de comportamiento de los primos bajo distintas transformaciones. 

### 1. Primos sobre la circunferencia unitaria.

#### El mapeo

Cada primo $p$ se proyecta al círculo mediante:

$$\theta_p = p \mod \pi$$

lo que produce un ángulo en $[0, \pi)$. A partir de este ángulo se calculan las coordenadas cartesianas y el área del triángulo formado con el origen:

$$x_p = \cos(\theta_p), \qquad y_p = \sin(\theta_p), \qquad A_p = \frac{x_p \cdot y_p}{2}$$

#### Campos derivados

| Campo | Fórmula | Interpretación |
|-------|---------|----------------|
| `rest` | $p \mod \pi$ | Posición angular del primo en la circunferencia |
| `cos` | $\cos(\text{rest})$ | Coordenada horizontal sobre el círculo unitario |
| `sin` | $\sin(\text{rest})$ | Coordenada vertical sobre el círculo unitario |
| `area` | $\frac{\cos \cdot \sin}{2}$ | Área del triángulo (origen, proyección, eje $x$) |

#### Visualización: Primo vs Área

El scatter plot de $p$ contra $A_p$ revela bandas de densidad que no son aleatorias — la distribución de áreas para los primos no es uniforme, lo que sugiere que la posición angular de los primos respecto a $\pi$ tiene estructura interna.

```
Área (Ap)
 0.5 ┤ ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·
     │ ·····················································  ← bandas de densidad
   0 ┤─────────────────────────────────────────────────────
     │ ·····················································
-0.5 ┤ ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·  ·
     └──────────────────────────────────────────────────────→ Primo (p)
```

###  2. Factorial Pirmo
Se define una función que calcula el factorial primo definido como el factorial de un número dejando en su producto, únicamente los números primos anteriores al número a calcularle el factorial.

 #### Visualización

Muestra el scatrer plot del logaritmo (para reducir la escala y poder visualizar el comportamiento) del factorial primo de los números del 1 al 200. 
---

## Líneas de investigación

El notebook de aplicaciones es un espacio vivo de experimentación. La exploración sobre la circunferencia unitaria es la primera, pero no la única dirección prevista. Algunas preguntas y enfoques en el horizonte:

- **Distribución de gaps angulares** — ¿Los huecos entre posiciones angulares consecutivas siguen algún patrón?
- **Densidad espectral** — ¿Una transformada de Fourier sobre las posiciones angulares revela frecuencias dominantes?
- **Correlación con funciones conocidas** — ¿La distribución de áreas se relaciona con la función zeta de Riemann o la función $\text{Li}(x)$?
- **Extensión a otros módulos** — ¿Qué ocurre si se usa $p \mod e$, $p \mod \sqrt{2}$, u otros irracionales como base del mapeo?
- **Otros espacios de representación** — Proyecciones en espirales, superficies, o espacios de mayor dimensión.
- **Relaciones con otras sucesiones** — Fibonacci, triangulares, factoriales y su interacción con los primos.

El objetivo final: encontrar una estructura — o varias — que acerque a una expresión analítica, o una familia de expresiones, que capture el comportamiento de los primos. Cada nueva exploración que se agregue al notebook de aplicaciones es un paso en esa dirección.

---

## Ejemplo rápido

```python
# Notebook 1: Funciones fundamentales
Prime(97)                        # True
List_Prime_numbers(10, 30)       # [11, 13, 17, 19, 23, 29]
Next_Prime(100)                  # 101
Previous_Next_Prime(50)          # (47, 53)
First_Prime_Numbers(5)           # [2, 3, 5, 7, 11]

# Notebook 2: Exploración geométrica
import pandas as pd, math
df = pd.read_csv('primos.csv')
df['rest'] = df.Primos.apply(lambda x: x % math.pi)
df['cos']  = df.rest.apply(math.cos)
df['sin']  = df.rest.apply(math.sin)
df['area'] = (df.cos * df.sin) / 2
```

---

## Requisitos

```
numpy
matplotlib
pandas
```

---

## Estado del proyecto

| Componente | Estado |
|-----------|--------|
| Funciones de identificación y generación | Completo |
| Dataset de primos hasta 50M | Completo |
| Proyección a circunferencia unitaria | Completo |
| Visualización Primo vs Área | Completo |
| Análisis de distribución angular | En exploración |
| Búsqueda de expresiones analíticas | Objetivo a largo plazo |
