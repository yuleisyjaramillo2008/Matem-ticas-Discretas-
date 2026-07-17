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

