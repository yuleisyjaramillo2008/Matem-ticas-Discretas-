<a href="../README.md"><code>◀ Regresar al Índice (README)</code></a>
# 🧠 RESUMEN TEÓRICO: LÓGICA PROPOSICIONAL

A continuación se presenta el marco conceptual y práctico para el análisis lógico matemático, abarcando desde las definiciones básicas hasta las leyes lógicas y reglas de inferencia para la simplificación de enunciados.

---

## 📌 1. Definición de Proposición

Una **proposición lógica** es un enunciado u oración declarativa a la cual se le puede asignar de forma inequívoca un único **valor de verdad**: ya sea **Verdadero (V)** o **Falso (F)**.

> ⚠️ **Regla Fundamental:** Una proposición afirma o niega algo, pero **jamás** puede poseer ambos valores simultáneamente. Esto las diferencia de las preguntas, exclamaciones o mandatos, las cuales carecen de valor de verdad.

*Las proposiciones constituyen la base fundamental de la lógica matemática, permitiendo modelar frases del lenguaje natural y operarlas mediante estructuras algebraicas.*

---

## 🗂️ 2. Tipos de Proposiciones

Podemos clasificar las estructuras de pensamiento bajo dos metodologías esenciales:

### A. Según su Estructura
Determina cómo se construyen los enunciados en el documento.

* **Proposiciones Simples:** Expresiones directas sin conectores.
* **Proposiciones Compuestas:** Unión de dos o más enunciados mediante conectivas.

![Carátula](Captura%20de%20pantalla%202026-06-15%20075058.png)

---

### B. Según su Resultado (Tablas de Verdad)

<details open>
<summary><b>📐 Tautología</b></summary>
<br>

Es una proposición compuesta que resulta estrictamente **VERDADERA** en la totalidad de sus combinaciones posibles, sin importar los valores de verdad individuales de las variables que la componen.
<br><br>
![Carátula](Captura%20de%20pantalla%202026-06-15%20075111.png)
</details>

<details>
<summary><b>❌ Contradicción</b></summary>
<br>

Representa el opuesto absoluto de la tautología. Ocurre cuando la evaluación final del enunciado da como resultado **FALSO** para cada uno de los escenarios lógicos evaluados.
<br><br>
![Carátula](Captura%20de%20pantalla%202026-06-15%20075117.png)
</details>

<details>
<summary><b>⚡ Contingencia</b></summary>
<br>

Es la situación más habitual en el análisis cotidiano. Ocurre cuando la columna resultante final de la matriz contiene combinaciones mezcladas de valores **Verdaderos (V)** y **Falsos (F)** alternados.
<br><br>
![Carátula](Captura%20de%20pantalla%202026-06-15%20075129.png)
</details>

---

## 🔗 3. Conectores Lógicos

### ¿Qué son?
Los conectores (o conectivos) lógicos son símbolos y operadores formales encargados de entrelazar proposiciones simples para estructurar expresiones compuestas complejas.

![Carátula](Captura%20de%20pantalla%202026-06-15%20075150.png)

### 📊 Especificaciones del Comportamiento Operacional

| Operador | Operación Lógica | Regla de Oro Matemática | Captura Visual |
| :---: | :---: | :--- | :---: |
| **`¬`** | **Negación** | Invierte el valor de verdad de la variable actual. | ![Carátula](Captura%20de%20pantalla%202026-06-15%20075158.png) |
| **`∧`** | **Conjunción** | Es **Verdadera (V)** únicamente si todas sus componentes son verdaderas. | ![Carátula](Captura%20de%20pantalla%202026-06-15%20075205.png) |
| **`∨`** | **Disyunción** | Es **Falsa (F)** únicamente si todas sus componentes son falsas. | ![Carátula](Captura%20de%20pantalla%202026-06-15%20075210.png) |
| **`→`** | **Condicional** | Es **Falsa (F)** solo si el antecedente es Verdadero y el consecuente Falso. | ![Carátula](Captura%20de%20pantalla%202026-06-15%20075216.png) |
| **`↔`** | **Bicondicional** | Es **Verdadera (V)** si ambas variables poseen valores idénticos de entrada. | ![Carátula](Captura%20de%20pantalla%202026-06-15%20075223.png) |

---

## 📋 4. Tablas de Verdad

Una tabla de verdad es una matriz de análisis algorítmico gráfico que sirve para mapear y visualizar el comportamiento de una función lógica frente a todas las combinaciones binarias posibles.

### 🛠️ Guía Metodológica Paso a Paso

```text
  [Paso 1: Contar Variables] ➔ [Paso 2: Generar Combinaciones] ➔ [Paso 3: Aplicar Jerarquías] ➔ [Paso 4: Operar Conectores] ➔ [Paso 5: Clasificar]
```

1. **Identificar Variables:** Contar el número de variables únicas ($n$) y calcular la extensión física de las filas de la tabla mediante la fórmula exponencial: `$2^n$`.
2. **Estructurar Combinaciones:** Rellenar las columnas de las variables de forma balanceada alternando Verdaderos (V) y Falsos (F).
3. **Jerarquía Lógica:** Descomponer el problema evaluando primero los paréntesis `()`, luego corchetes `[]` y finalmente llaves `{}`.
4. **Cálculo de Operaciones:** Resolver las subexpresiones aplicando estrictamente las reglas de oro de los conectores analizados.
5. **Clasificación Formal:** Diagnosticar el resultado de la columna final para catalogarla como Tautología, Contradicción o Contingencia.

### 🔍 Ejemplo de Demostración Práctica
Dada la expresión: `((p ∧ q) → p)`
* **Número de variables ($n$):** 2
* **Filas calculadas:** `$2^2 = 4$`

![Carátula](Captura%20de%20pantalla%202026-06-15%20075238.png)

> **Resultado del Análisis:** Al tener una columna de salida compuesta puramente por estados verdaderos, se concluye formalmente que esta proposición constituye una **Tautología**.

---

## 📜 5. Leyes Proposicionales

Son equivalencias e identidades lógicas formales que permiten transformar y reescribir ecuaciones lógicas complejas en expresiones minimalistas equivalentes, reduciendo el costo algorítmico.

![Carátula](Captura%20de%20pantalla%202026-06-15%20075246.png)

---

## 🧠 6. Reglas de Inferencia

Constituyen reglas lógicas y mecanismos formales deductivos que nos permiten estructurar silogismos y razonamientos válidos para derivar una **conclusión lógica** irrebatible a partir de un conjunto inicial de premisas.

![Carátula](Captura%20de%20pantalla%202026-06-15%20075253.png)


<br>


<p align="right">
  <a href="../README.md"><code>◀ Regresar al Índice</code></a>
  <a href="#top"><code>▲ Subir</code></a>
</p>


