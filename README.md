# Proyectos_de_Matematicas

Repositorio personal para agrupar proyectos de programación orientados a temas matemáticos.
Aquí se irán incorporando códigos de distintas áreas, por ejemplo:

- Conjetura de Collatz
- Números primos
- etc

## Proyectos

### 1. Conjetura de Collatz
- **Carpeta:** `Collatz/`
- **Archivo principal:** `Conjetura_Collatz.ipynb`
- **Descripción breve:**
	Dado un número entero positivo, el programa aplica iterativamente la regla de Collatz:
	- Si el número es par, se divide entre $2$.
	- Si el número es impar, se calcula $3n + 1$.
	El proceso continúa hasta llegar a 1, mostrando la secuencia y el número de pasos.

### 2. Números primos
- **Carpeta:** `Numeros_Primos/`
- **Archivo principal:** `Proyecto_Primos.ipynb`
- **Descripción breve:**
	Este módulo desarrolla utilidades para análisis de números primos con enfoque en validación y reutilización. La función base es `Prime()`, que verifica si un valor es primo tras validar la entrada y comprobar divisibilidad en el rango $[2, \sqrt{n}]$: si encuentra divisor retorna `False`, y si no, `True`.
	
	Funciones incluidas:
	- `List_Prime_numbers(m, n)`: lista los números primos dentro del intervalo `[m, n]`.
	- `Next_Prime(n)`: obtiene el primo inmediatamente posterior a `n`.
	- `Previous_Prime(n)`: obtiene el primo inmediatamente anterior a `n`.
	- `Previous_Next_Prime(n)`: devuelve en una tupla el primo anterior y el siguiente de `n`.
	- `First_Prime_Numbers(n)`: genera los primeros `n` números primos.

## Estructura

```text
Proyectos_de_Matematicas/
├── README.md
├── Collatz/
│   └── Conjetura_Collatz.ipynb
└── Numeros_Primos/
    └── Proyecto_Primos.ipynb
```

> La estructura irá creciendo a medida que se agreguen nuevas carpetas y notebooks.

## Notas

- Cada subcarpeta representa un tema o problema matemático específico.
- Cada proyecto puede contener notebooks, scripts y resultados asociados.
- Este repositorio está en construcción y se actualizará de forma incremental.