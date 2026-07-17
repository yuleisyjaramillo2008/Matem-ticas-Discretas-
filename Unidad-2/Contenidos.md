# 🎛️ Fundamentos de Circuitos y Optimización Lógica

---

## 🔌 1. Compuertas Lógicas

* **¿Qué es?**
  * Circuitos electrónicos diseñados para operar con valores binarios.
  * Manejan estados representados por niveles lógicos discretos (0 y 1).
  * Construidas físicamente mediante transistores, diodos y resistencias.
* **¿Cómo se aplica?**
  * Su comportamiento se define mediante leyes del Álgebra Booleana.
  * Se representan gráficamente usando símbolos específicos internacionales.
  * Se analizan con Tablas de Verdad para describir la salida.
* **¿Dónde se aplica en computación?**
  * Base de ingeniería para fabricar Circuitos Integrados (CI) comerciales.
  * Permiten determinar la función lógica de microprocesadores y hardware.
* **Ejemplo Práctico:**
  * Compuerta AND con operación de producto lógico directo.
  * Salida alta (1) sólo si todas las entradas valen 1.
  ```text
  Si entrada A = 1 y entrada B = 1, entonces Salida x = 1
  ```

---

## 📜 2. Leyes y Teoremas del Álgebra de Boole

* **¿Qué es?**
  * Conjunto formal de reglas, axiomas y teoremas lógicos matemáticos.
  * Estructuran el razonamiento mediante variables que adoptan dos valores.
  * Operan únicamente sobre los estados: 0 (Bajo) y 1 (Alto).
* **¿Cómo se aplica?**
  * Se utilizan para realizar transformaciones algebraicas en sentencias lógicas.
  * Reducen expresiones booleanas complejas a sus formas más simples.
* **¿Dónde se aplica en computación?**
  * Garantizan la consistencia lógica interna en algoritmos informáticos.
  * Optimizan el diseño de circuitos digitales ahorrando componentes físicos.


### 📊 Tabla de Teoremas y Leyes del Álgebra Booleana

| Categoría | Teorema / Ley | Expresión Matemática |
| :--- | :--- | :--- |
| **Identidades Básicas** | Elemento Neutro / Nulo | $x \cdot 0 = 0$ <br> $x + 1 = 1$ |
| | Identidad | $x \cdot 1 = x$ <br> $x + 0 = x$ |
| | Idempotencia | $x \cdot x = x$ <br> $x + x = x$ |
| | Complemento | $x \cdot \bar{x} = 0$ <br> $x + \bar{x} = 1$ |
| **Leyes Algebraicas** | Conmutativa | $x + y = y + x$ <br> $x \cdot y = y \cdot x$ |
| | Asociativa | $x + (y + z) = (x + y) + z$ <br> $x(yz) = (xy)z$ |
| | Distributiva | $x(y + z) = xy + xz$ <br> $(w + x)(y + z) = wy + xy + wz + xz$ |
| | Absorción | $x + xy = x$ <br> $A \cdot (A + B) = A$ |
| | Simplificación Adicional | $x + \bar{x}y = x + y$ |
| **Teoremas Clave** | De Morgan | $\overline{(x + y)} = \bar{x} \cdot \bar{y}$ <br> $\overline{(x \cdot y)} = \bar{x} + \bar{y}$ |
| | Consenso Dual | $(X + Y)(\bar{X} + Z)(Y + Z) = (X + Y)(\bar{X} + Z)$ |
| | Expansión de Shannon | $f = x \cdot f_x + \bar{x} \cdot f_{\bar{x}}$ |
| | Resolución Booleana | $\frac{A \lor B, \; \neg A \lor C}{B \lor C}$ *(Regla de inferencia)* |


---

## 🗺️ 3. Mapas de Karnaugh (K-Maps)

* **¿Qué es?**
  * Método gráfico sistemático utilizado para simplificar ecuaciones lógicas de raíz.
  * Transforma tablas de verdad en circuitos lógicos de manera ordenada.
  * Procedimiento altamente práctico para problemas de hasta 5 variables.

### 🛠️ Pasos para Construir y Resolver un Mapa

1. **Construcción del mapa:** Se organiza una matriz o diagrama de celdas. Los cuadros adyacentes deben diferir en una sola variable aplicando Código Gray.
2. **Transferencia de datos:** Se colocan los "1" en las celdas de la cuadrícula. Corresponden a los resultados altos de la tabla de verdad.
3. **Identificación de "unos" aislados:** Primer paso estratégico esencial del mapa. Consiste en marcar aquellos "1" que no poseen vecinos adyacentes.
4. **Localización de pares forzosos:** Identificar estados "1" que posean un único vecino. Permiten amarrar grupos mínimos cerrados de dos elementos.
5. **Agrupamiento de potencias de 2:** Realizar agrupaciones masivas de celdas lógicas válidas. Siguen estrictamente la progresión exponencial geométrica \(2^n\) (1, 2, 4, 8).
6. **Priorización de grupos grandes:** Buscar octetos (8) primero, luego cuádruples (4). Dejar los pares (2) al final, reusando "unos" ya agrupados.
7. **Suma de resultados:** La función simplificada final se construye sumando los términos. Consiste en la unión lógica de cada grupo simplificado.

### 📐 Diferentes Agrupaciones de "Unos"

* **Pares (Grupo de 2 términos):** Formados por dos "1" adyacentes continuos. Eliminan exactamente una variable de la expresión original combinada.
* **Cuádruples (Grupo de 4 términos):** Bloques adyacentes en línea o cuadrados de 2x2. Resultan más efectivos que los pares para la simplificación.
* **Octetos (Grupo de 8 términos):** Agrupaciones masivas de alta prioridad en la tabla. Simplifican la función anulando tres variables directamente.

### 💡 Estrategias Clave para la Simplificación

* **Minimización de grupos:** El objetivo principal es usar la menor cantidad posible de lazos. Se busca cubrir la totalidad de los "unos" del mapa.
* **Solapamiento permitido:** Es válido y necesario que un "1" comparta múltiples lazos. Ayuda a consolidar grupos de mayor dimensión para simplificar más.
* **Reducción de errores:** Su uso automatizado visual mitiga fallas en la síntesis. Reduce la probabilidad de cometer errores frente al álgebra manual pura.

# ⚡ Conceptos Avanzados de Álgebra Booleana

A continuación se detallan tres teoremas fundamentales utilizados en la minimización de funciones lógicas, síntesis de hardware y verificación formal de sistemas en la Ingeniería de la Computación.

---

## 🏛️ 1. Teorema del Consenso Dual

<details open>
<summary><b>Click para expandir detalles teóricos y aplicación</b></summary>
<br>

> **Definición rápida:** Es la contraparte del Teorema del Consenso original bajo el Principio de Dualidad. Su función principal es identificar y eliminar términos lógicamente redundantes en expresiones de tipo **Producto de Sumas (POS)**.

| Criterio | Descripción |
| :--- | :--- |
| **¿Cómo se aplica?** | Se identifican dos factores que contienen una variable opuesta (por ejemplo, \(X\) y \(\neg X\)). Si existe un tercer factor formado por las otras variables de los dos primeros, ese tercer factor es el **consenso** y se puede eliminar de la expresión. |
| **Aplicación en Computación** | Se utiliza en la **optimización de circuitos lógicos** para reducir el número de puertas físicas necesarias en un chip de silicio sin alterar el comportamiento lógico del sistema. |

### 🔍 Ejemplo Práctico de Simplificación

* **Expresión original:**
  ```text
  (X + Y)(¬X + Z)(Y + Z)(W + Z)
  ```
* **Análisis del caso:** Se identifican las variables opuestas \(X\) y \(\neg X\) en los primeros dos paréntesis. Tomando las variables acompañantes (\(Y\) y \(Z\)), descubrimos que el término `(Y + Z)` es el consenso potencial redundante.
* **Resultado simplificado:**
  ```text
  (X + Y)(¬X + Z)(W + Z)
  ```
  *(Se eliminó con éxito el término redundante)*

</details>

---

## 📐 2. Expansión de Shannon

<details>
<summary><b>Click para expandir detalles teóricos y aplicación</b></summary>
<br>

> **Definición rápida:** Conocido como el *Teorema de Descomposición Universal*, establece que cualquier función booleana puede descomponerse en la suma ponderada de sus co-factores respecto a una variable elegida (denominada variable pivote).

\[\text{Fórmula General: } f = x \cdot f_x + \neg x \cdot f_{\neg x}\]

| Criterio | Descripción |
| :--- | :--- |
| **¿Cómo se aplica?** | Se selecciona una variable como pivote. Luego, se evalúa la función original cuando esa variable vale \(1\) (\(f_x\)) y cuando vale \(0\) (\(f_{\neg x}\)). Finalmente, se reconstruye la estructura usando la fórmula de expansión. |
| **Aplicación en Computación** | Es la base matemática para el diseño físico de **Multiplexores (MUX)** en hardware y para la creación de **Diagramas de Decisión Binaria (BDD)** en herramientas de software CAD. |

### 🔍 Ejemplo Práctico de Evaluación

Sea la función lógca:
```text
F(A, B, C) = AB + ¬AC + BC
```

Evaluando la expresión con la variable **A** como pivote:
* **Si \(A = 1\):** \(F(1, B, C) = B\)
* **Si \(A = 0\):** \(F(0, B, C) = C\)

```text
Resultado final expandido: F = A · (B) + ¬A · (C)
```

</details>

---

## 🧠 3. Resolución Booleana

<details>
<summary><b>Click para expandir detalles teóricos y aplicación</b></summary>
<br>

> **Definición rápida:** Es una regla de inferencia lógica algorítmica que genera una nueva cláusula simplificada (llamada **resolvente**) a partir de dos cláusulas previas que contienen literales estrictamente complementarios.

| Criterio | Descripción |
| :--- | :--- |
| **¿Cómo se aplica?** | 1. Se expresa el sistema en **Forma Normal Conjuntiva (CNF)**.<br>2. Se buscan pares de cláusulas con un literal en común pero con signos opuestos.<br>3. Se deriva el resolvente y se añade al conjunto de reglas para concluir. |
| **Aplicación en Computación** | Es fundamental en el desarrollo de **motores SAT (Satisfacibilidad)** y demostradores automáticos de teoremas, esenciales para la verificación formal de software crítico e Inteligencia Artificial. |

### 🔍 Ejemplo Práctico Basado en Casos de Soporte Técnico

Imagine un sistema informático analizado bajo las siguientes dos reglas lógicas:

* **Cláusula 1:** `X + Y` \(\rightarrow\) *(El problema es de software **O** es de hardware)*
* **Cláusula 2:** `¬X + Z` \(\rightarrow\) *(Si **NO** es un problema de software, el sistema se reiniciará)*

Al aplicar el método de resolución y eliminar las variables complementarias \(X\) y \(\neg X\), el sistema deduce la siguiente conclusión automática:

```text
Resolvente obtenido: Y + Z
(Conclusión: O el problema es de hardware, O el sistema se reiniciará)
```

</details>

---

