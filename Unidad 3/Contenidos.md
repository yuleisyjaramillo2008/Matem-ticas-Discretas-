<a href="../README.md"><code>◀ Regresar al Índice (README)</code></a>

# 🕸️ I. Teoría de Grafos

La Teoría de Grafos proporciona el marco matemático e informático fundamental para modelar y analizar estructuras interconectadas complejas, priorizando las relaciones topológicas sobre las geométricas.

---

## 📐 1. Definición y Naturaleza Matemática

Un grafo se define formalmente como un par ordenado:

\[G = (V, E)\]

* **\(V\) (Vertices):** Un conjunto finito y no vacío de vértices o nodos.
* **\(E\) (Edges):** Un conjunto de aristas o lados que representan las conexiones lógicas entre dichos nodos.

> 💡 **Nota de Diseño:** Un grafo captura información puramente **topológica**, lo que significa que prioriza la conectividad y la existencia de rutas por encima de propiedades geométricas tradicionales como distancias físicas, formas o ángulos de dibujo.

---

## 📜 2. Origen e Importancia en la Computación

<details open>
<summary><b>Click para ver antecedentes e impacto actual</b></summary>
<br>

La teoría nació formalmente en **1736** cuando el matemático **Leonhard Euler** resolvió el célebre problema de los *Siete Puentes de Königsberg*, demostrando matemáticamente que era imposible cruzarlos todos pasando exactamente una sola vez por cada uno.

En la ingeniería de la computación moderna, constituye la piedra angular para:
* 🤖 **Inteligencia Artificial y Redes Sociales:** Modelado de grafos de conocimiento, algoritmos de recomendación y redes de amigos.
* 🗺️ **Optimización de Recursos:** Diseño de enrutamiento de paquetes en redes IP, logística de transporte físico y trazado de pistas en circuitos integrados (microchips).
* 💾 **Sistemas Operativos:** Organización jerárquica de archivos, detección de interbloqueos (*deadlocks*) y algoritmos de recolección de basura en memoria.

</details>

---

## 📋 3. Terminología y Propiedades Clave

<details>
<summary><b>Click para expandir glosario estructural</b></summary>
<br>

### 🔹 Conceptos Fundamentales
* **Adyacencia:** Propiedad que une a dos vértices si existe una arista directa entre ellos.
* **Incidencia:** Relación que vincula a una arista con los dos vértices que actúan como sus extremos.
* **Grado (Valencia):** Representa el número total de aristas que inciden sobre un vértice específico.

### 🤝 Lema del Apretón de Manos (Handshaking Lemma)
Establece de manera analítica que la suma de los grados de todos los vértices dentro de un grafo es siempre equivalente al doble del número de aristas del mismo:

\[\sum_{v \in V} \text{deg}(v) = 2\vert{}E\vert{}\]

### 🛠️ Clasificación Estructural
1. **Grafo Simple:** Estructura limpia que carece estrictamente de lazos (aristas que conectan a un nodo consigo mismo) y de aristas paralelas.
2. **Dígrafo (Grafo Dirigido):** Las conexiones poseen un sentido o dirección específica, representada visualmente mediante flechas orientadas.
3. **Grafo Bipartito:** Los vértices se dividen en dos conjuntos independientes disjuntos, donde las aristas solo pueden enlazar nodos de grupos diferentes.

</details>

---

## 💻 4. Representación Matricial (Computacional)

Para que las computadoras puedan procesar y ejecutar operaciones sobre grafos de manera eficiente en memoria, se implementan estructuras matriciales binarias:

| Tipo de Matriz | Definición Operacional | Ventaja Principal |
| :--- | :--- | :--- |
| 🔲 **Matriz de Adyacencia** | Matriz cuadrada de dimensión \(V \times V\) donde un `1` denota conexión directa entre dos nodos y un `0` representa su ausencia. | Alta velocidad de consulta para verificar si dos nodos específicos están conectados. |
| 📊 **Matriz de Incidencia** | Matriz rectangular de dimensión \(V \times E\) que mapea las relaciones y dependencias cruzadas entre vértices y aristas. | Facilita el análisis analítico de flujos, propiedades estructurales y recorridos. |

---

## 🧮 5. Caminos, Circuitos y Algoritmos

```text
       [Euleriano] ➔ Recorre todas las ARISTAS una sola vez.
       [Hamiltoniano] ➔ Visita todos los VÉRTICES una sola vez.
```

### 🔁 Paseos y Ciclos Lógicos
* **Estructuras de Euler:** 
  * Un *paseo euleriano* transita por cada arista del grafo exactamente una vez. 
  * Un *circuito euleriano* es un paseo cerrado donde todos los vértices deben poseer obligatoriamente un **grado par**.
* **Estructuras de Hamilton:** Se concentran exclusivamente en la visita de nodos, requiriendo tocar cada vértice del grafo exactamente una sola vez sin repetir.

### 🛠️ Algoritmos de Optimización de Redes

## 🧮 II. Algoritmos de Optimización en Grafos

Los algoritmos de Fleury y Dijkstra representan dos enfoques fundamentales para la resolución de problemas de optimización en redes, abordando desde el recorrido completo de aristas hasta el cálculo de las rutas más cortas.

---

### 🔁 1. Algoritmo de Fleury

<details open>
<summary><b>Click para expandir el funcionamiento de Fleury</b></summary>
<br>

> **Definición rápida:** Este algoritmo se utiliza específicamente para encontrar caminos o circuitos eulerianos. Su objetivo principal es diseñar un recorrido secuencial que logre pasar por cada arista del grafo exactamente una sola vez.

* **¿Cuándo se usa?** Es vital en problemas de logística pesada, recolección de residuos y optimización de rutas de distribución donde resulta ineficiente o prohibido repetir el tránsito por la misma vía.

#### 🛠️ Pasos para su Ejecución

1. **Verificar condiciones:** El grafo debe ser conexo. 
   * Si todos los vértices tienen **grado par**, existe un circuito (regresa al inicio).
   * Si hay exactamente **dos vértices de grado impar**, existe un paseo (empieza en uno y termina obligatoriamente en el otro).
2. **Selección inicial:** Elige un vértice para empezar. Si el análisis determinó la existencia de vértices de grado impar, debes arrancar la secuencia desde uno de ellos.
3. **⚠️ La Regla de Oro (No atravesar puentes):** Al elegir la siguiente arista para avanzar, **no utilices un "puente"** (una arista que, si se elimina, divide el grafo restante en dos secciones aisladas) a menos que no tengas ninguna otra opción disponible.
4. **Recorrer y eliminar:** Marca la arista recorrida, avanza al siguiente vértice y bórrala mentalmente de la matriz del mapa.
5. **Iteración cíclica:** Repite el proceso de selección y eliminación hasta haber transitado por la totalidad de las aristas y vaciar el grafo.

</details>

---

### 🗺️ 2. Algoritmo de Dijkstra

<details>
<summary><b>Click para expandir el funcionamiento de Dijkstra</b></summary>
<br>

> **Definición rápida:** Es la herramienta por excelencia para la optimización de rutas y la reducción de costos en redes ponderadas, especializándose en encontrar el camino más corto entre un nodo origen y todos los demás nodos de un grafo con pesos asociados.

* **¿Dónde se aplica?** Es el motor lógico y matemático detrás de los sistemas de posicionamiento global y aplicaciones de navegación moderna como Google Maps para calcular el camino más rápido entre dos puntos geográficos.
* **🚨 Regla Crítica:** Este algoritmo funciona única y exclusivamente con **pesos positivos** (valores mayores a cero). No es capaz de procesar aristas con pesos negativos debido a su naturaleza ávida (*greedy*).

#### 🛠️ Pasos para su Ejecución

1. **Inicializar el sistema:** Se asigna un valor de distancia de `0` al nodo origen seleccionado y una distancia de "infinito" (`∞`) a todos los demás nodos de la red. Se configuran todos los elementos en el estado de "no visitados".
2. **Seleccionar nodo:** Se localiza y elige el nodo no visitado que posea la distancia acumulada más corta registrada hasta el momento.
3. **Relajar aristas:** Para el nodo seleccionado, se calculan las distancias proyectadas hacia sus vecinos directos sumando el peso de la arista de conexión. Si esta nueva distancia resulta menor a la que el vecino tenía guardada, se actualiza el valor de forma automática.
4. **Marcar como visitado:** Una vez evaluados todos sus vecinos inmediatos, el nodo se etiqueta como "visitado" para bloquearlo y no volver a procesarlo en memoria.
5. **Repetir:** El proceso continúa de forma iterativa hasta que la totalidad de los nodos del sistema hayan sido visitados o se alcance el nodo destino.
6. **Construcción del Resultado:** Se reconstruye la ruta mínima mapeando en reversa los nodos predecesores que fueron registrados durante las actualizaciones de relajación.

</details>

---

### 📊 Comparativa de Aplicaciones Prácticas

A continuación se presenta un cuadro comparativo que diferencia los propósitos de ambos algoritmos dentro del desarrollo de software y hardware:

| Algoritmo | Propósito Principal | Aplicación en la Computación |
| :---: | :--- | :--- |
| **Fleury** | Recorrer cada arista de la red exactamente una sola vez de forma secuencial. | Trazado de pistas en circuitos impresos (PCB), diseño de rutas de carteros, optimización de maquinaria de limpieza de calles y robótica de cobertura. |
| **Dijkstra** | Encontrar la ruta o camino de coste mínimo absoluto entre dos nodos de un grafo ponderado. | Algoritmos de enrutamiento de paquetes de datos en Internet (como OSPF), sistemas de navegación GPS satelital y optimización de redes de telecomunicaciones. |

---

---
## 📊 Representación Matricial Computacional

Para que las computadoras puedan procesar, almacenar y operar con grafos en memoria de manera estructurada, se transforman las conexiones visuales en matrices de datos lógicos.

---

### 🔲 1. Matriz de Adyacencia

<details open>
<summary><b>Click para expandir detalles de la Matriz de Adyacencia</b></summary>
<br>

> **Enfoque principal:** Es el método estándar y más común utilizado en ingeniería para verificar de manera inmediata la existencia de conexiones directas entre nodos individuales.

* **Estructura Matemática:** Consiste en una matriz estrictamente cuadrada de dimensión $n \times n$, donde $n$ representa la cantidad total de vértices del grafo. Tanto las filas como las columnas representan los mismos nodos de la red.
* **Valores Binarios:** Cada celda de la matriz contiene un `1` si existe un enlace o arista directa uniendo a ambos vértices, y un `0` en caso de que no exista relación alguna.
* **💪 Su Superpoder (Ventaja):** Destaca por su **velocidad de consulta constante**. Permite verificar instantáneamente si dos nodos están relacionados sin necesidad de recorrer la red completa, lo que la hace la herramienta ideal para motores de sugerencias en tiempo real dentro de redes sociales (como la función *"Personas que quizá conozcas"*).

</details>

---

### 📊 2. Matriz de Incidencia

<details>
<summary><b>Click para expandir detalles de la Matriz de Incidencia</b></summary>
<br>

> **Enfoque principal:** Este método cambia radicalmente el foco de atención de la computadora, moviendo la prioridad desde los nodos hacia las aristas (las conexiones en sí mismas).

* **Estructura Matemática:** Consiste en una matriz típicamente rectangular cuyas dimensiones están delimitadas por la cantidad de **Vértices $\times$ Aristas**. Las filas corresponden a los nodos y las columnas representan cada arista del sistema.
* **Valores de Pertenencia:** Los datos de las celdas marcan relaciones de pertenencia estructural, indicando cuáles dos vértices actúan específicamente como los extremos físicos de cada arista analizada.
* **🎯 Ventaja Principal:** Facilita el análisis anatómico y estructural del grafo, simplificando el desarrollo de algoritmos de conectividad avanzada. Es sumamente útil en la simulación de redes viales, detección de cuellos de botella en tráfico y cálculos de flujo de carga pesada.

</details>

---

### ⚖️ Cuadro Comparativo para el Portafolio

A continuación se detalla la comparativa técnica de rendimiento y diseño entre ambas metodologías de representación de datos:

| Característica | Matriz de Adyacencia | Matriz de Incidencia |
| :--- | :--- | :--- |
| **Relación Base** | Nodo vs. Nodo | Nodo vs. Arista |
| **Dimensiones** | Cuadrada ($n \times n$) | Rectangular (Vértices $\times$ Aristas) |
| **Prioridad Técnica** | Rapidez absoluta de consulta de conexiones | Análisis de propiedades estructurales del grafo |
| **Uso Común** | Redes sociales, bases de datos orientadas a grafos | Navegación GPS, tráfico urbano y telecomunicaciones |

---

### 💡 ¿Por qué son importantes en la Ingeniería de la Computación?

El análisis de estructuras de datos demuestra que **ninguna matriz es inherentemente mejor que la otra**, sino que su selección depende estrictamente de los requerimientos del problema de software o hardware a resolver:

* **Matriz de Adyacencia:** Es óptima y computacionalmente eficiente cuando el sistema necesita responder rápidamente **"quién está conectado con quién"**.
* **Matriz de Incidencia:** Es la opción ideal cuando el algoritmo necesita comprender con exactitud **"cómo están construidos los caminos"** a lo largo de la infraestructura de red.

---

# 🌳 II. Teoría de Árboles

La Teoría de Árboles modela estructuras de datos jerárquicas y dinámicas no lineales de alta eficiencia, esenciales para la organización de archivos, optimización de búsquedas y compresión de información en computación.

---

## 🔬 1. Definición y Propiedades Fundamentales

Un **árbol** es un caso especial y restrictivo de grafo que se define formalmente como una estructura **no dirigida, conexa y que carece estrictamente de circuitos o ciclos** (acíclica).

> 💎 **La Propiedad de Unicidad:** Esta ausencia absoluta de bucles o ciclos garantiza matemáticamente que **existe un único camino** posible para conectar cualquier par de vértices dentro del sistema. Esta característica elimina la redundancia y permite una navegación jerárquica exacta y predecible.

---

## 🗂️ 2. Componentes y Relaciones Jerárquicas

<details open>
<summary><b>Click para expandir la anatomía de un Árbol Enraizado</b></summary>
<br>

Al definir un nodo inicial como el origen, el árbol se convierte en una estructura enraizada donde cada componente adopta un rol específico:

```text
               [ Raíz ]          ➔ Valencia de Entrada = 0
               /      \
        [ Interno ]  [ Interno ] ➔ Valencia de Salida ≠ 0
          /     \          \
      [ Hoja ] [ Hoja ]  [ Hoja ] ➔ Valencia de Salida = 0
```

* **👑 Raíz:** Es el nodo supremo o principal del cual desciende toda la estructura. Posee una valencia de entrada igual a cero.
* **🌿 Nodos Rama (Internos):** Son nodos intermedios que conectan subestructuras. Tienen una valencia de salida distinta de cero (poseen hijos).
* **🍂 Hojas (Terminales):** Son los nodos finales del árbol. Poseen una valencia de salida igual a cero, marcando el fin de una ruta de datos.
* **👪 Relaciones Familiares:** Se emplean analogías como *padre, hijo, hermano, ancestro y descendiente* para describir con precisión la posición relativa de cada nodo en la jerarquía.
* **📏 Altura:** Representa la longitud máxima o número de aristas que componen el paseo más largo desde la raíz hasta la hoja más profunda.

</details>

---

## 🚀 3. Tipos de Árboles y Aplicaciones Reales

<details>
<summary><b>Click para ver estructuras avanzadas e ingeniería de software</b></summary>
<br>

La optimización de algoritmos se basa en variantes de árboles diseñadas para propósitos computacionales específicos:

* **📊 Árboles de Búsqueda Binaria (ABB / BST):** Organizan los datos de manera que los valores menores al nodo actual se desplazan al subárbol izquierdo y los mayores al derecho. Permiten realizar búsquedas, inserciones y eliminaciones ultra rápidas en **tiempo logarítmico `$O(\log n)$`**.
* **⚖️ Árboles Balanceados (AVL):** Son árboles de búsqueda binaria auto-equilibrables. Monitorean su propia altura de forma dinámica para reestructurarse ante cada inserción, garantizando siempre la máxima velocidad de operación en el peor de los casos.
* **🧮 Árboles de Expresión:** Estructuras utilizadas por los compiladores de software para parsear y procesar ecuaciones algebraicas. Los operadores actúan como nodos internos y los operandos (números o variables) se ubican en las hojas.
* **🗜️ Código de Huffman:** Un algoritmo de compresión de datos sin pérdida. Utiliza árboles binarios para asignar secuencias binarias cortas a los caracteres más frecuentes del texto, eliminando cualquier ambigüedad en la descompresión.

</details>

---

## 🔄 4. Métodos de Recorrido Sistemático

Para procesar la información contenida en un árbol, el microprocesador debe ejecutar un recorrido sistemático que le permita visitar cada nodo exactamente una sola vez. Existen tres metodologías fundamentales:

| Tipo de Recorrido | Secuencia de Operación | Aplicación Computacional Clave |
| :---: | :---: | :--- |
| **Preorden** | `Raíz` ➔ `Izquierdo` ➔ `Derecho` | Es la herramienta ideal para clonar, duplicar o copiar la estructura exacta de un árbol en otra sección de la memoria. |
| **Inorden** | `Izquierdo` ➔ `Raíz` ➔ `Derecho` | Al aplicarse sobre un Árbol de Búsqueda Binaria (ABB), devuelve los datos ordenados de forma ascendente. Es óptimo para generar reportes estructurados. |
| **Postorden** | `Izquierdo` ➔ `Derecho` ➔ `Raíz` | Es el estándar para la **recolección de basura y liberación de memoria física** (elimina hijos antes que padres para evitar fugas de memoria). También se usa para resolver árboles de expresión matemática. |

---
# 🔄 IV. Métodos de Recorrido Sistemático en Árboles

Los recorridos son algoritmos diseñados para visitar de manera sistemática y secuencial cada uno de los nodos de un árbol exactamente una sola vez, mapeando estructuras jerárquicas en secuencias lineales procesables por el hardware.

---

## 🔲 1. Recorrido en Preorden (NID / RID)

<details open>
<summary><b>Click para expandir la secuencia de Preorden</b></summary>
<br>

> **Principio de Operación:** En este método, el microprocesador evalúa y procesa el nodo raíz actual antes de descender hacia cualquiera de sus subárboles dependientes.

### 🛠️ Secuencia de Pasos Algorítmicos
```text
  [1] Visitar Raíz (N) ➔ [2] Procesar Subárbol Izquierdo (I) ➔ [3] Procesar Subárbol Derecho (D)
```

1. **Visitar el nodo Raíz (N):** Se extrae o procesa el valor del nodo actual en el que se encuentra el puntero.
2. **Recorrer el subárbol Izquierdo (I):** Se invoca el algoritmo de forma recursiva hacia la bifurcación izquierda.
3. **Recorrer el subárbol Derecho (D):** Se invoca el algoritmo de forma recursiva hacia la bifurcación derecha.

* **💻 Aplicación en Computación:** Es la herramienta estándar para **clonar o copiar un árbol estructuralmente en otra sección de la memoria**. Asimismo, se emplea en la **serialización de archivos**, transformando estructuras jerárquicas complejas en archivos planos legibles para su posterior reconstrucción exacta y sin pérdida de datos.

</details>

---

## ⚖️ 2. Recorrido en Inorden / Enorden (IND)

<details>
<summary><b>Click para expandir la secuencia de Inorden</b></summary>
<br>

> **Principio de Operación:** Como su nombre lo indica, la raíz del árbol o subárbol bajo análisis se visita estrictamente en un punto intermedio, justo entre las evaluaciones de los subárboles izquierdo y derecho.

### 🛠️ Secuencia de Pasos Algorítmicos
```text
  [1] Procesar Subárbol Izquierdo (I) ➔ [2] Visitar Raíz (N) ➔ [3] Procesar Subárbol Derecho (D)
```

1. **Recorrer el subárbol Izquierdo (I):** Se desciende recursivamente por la rama izquierda hasta alcanzar la hoja más profunda.
2. **Visitar el nodo Raíz (N):** Se procesa el nodo base o padre de la subestructura actual.
3. **Recorrer el subárbol Derecho (D):** Se ejecuta el análisis recursivo sobre los elementos de la rama derecha.

* **💻 Aplicación en Computación:** Es fundamental para la gestión de **Árboles de Búsqueda Binaria (ABB)** debido a que este recorrido extrae los elementos de la estructura en un **orden lineal ascendente perfecto**. Su uso directo permite generar reportes limpios y listados ordenados directamente desde la base de datos sin gastar ciclos de procesamiento adicionales en algoritmos de ordenamiento externos.

</details>

---

## 🍂 3. Recorrido en Postorden (IDN)

<details>

<br>


<p align="right">
  <a href="../README.md"><code>◀ Regresar al Índice</code></a>
  <a href="#top"><code>▲ Subir</code></a>
</p>
<summary><b>Click para expandir la secuencia de Postorden</b></summary>
<br>

> **Principio de Operación:** En esta metodología, el nodo raíz es el último elemento absoluto en ser evaluado. Esto asegura de forma matemática que todas las ramificaciones, hojas e hijos inferiores sean procesados antes que sus respectivos nodos padres.

### 🛠️ Secuencia de Pasos Algorítmicos
```text
  [1] Procesar Subárbol Izquierdo (I) ➔ [2] Procesar Subárbol Derecho (D) ➔ [3] Visitar Raíz (N)
```

1. **Recorrer el subárbol Izquierdo (I):** Se evalúan recursivamente todos los nodos de la ramificación izquierda.
2. **Recorrer el subárbol Derecho (D):** Se evalúan recursivamente todos los nodos de la ramificación derecha.
3. **Visitar el nodo Raíz (N):** Finalmente, una vez liberadas las ramas inferiores, se procede a leer el nodo raíz.

* **💻 Aplicación en Computación:** Se utiliza de forma crítica para **liberar memoria física y destruir estructuras dinámicas de forma segura**, eliminando primero a los hijos para evitar la creación de "nodos huérfanos" y referencias rotas en el sistema operativo. Adicionalmente, es el estándar para la **evaluación de expresiones matemáticas en compiladores** mediante el uso de la Notación Polaca Inversa.

</details>

---

## 📊 Matriz de Resumen para el Portafolio

A continuación se presenta un cuadro técnico consolidado que compara los tres métodos de recorrido en memoria para una consulta rápida:

| Recorrido | Abreviación | Prioridad en Memoria | Uso Principal en Ingeniería |
| :---: | :---: | :---: | :--- |
| 🔲 **Preorden** | `N-I-D` | Raíz al inicio de la pila | Clonación estructural, copias de seguridad y serialización de archivos planos. |
| ⚖️ **Inorden** | `I-N-D` | Raíz en medio del proceso | Generación de reportes ordenados y validación analítica de Árboles de Búsqueda Binaria. |
| 🍂 **Postorden** | `I-D-N` | Raíz al final de la cola | Liberación de memoria ram, eliminación segura de datos y evaluación de fórmulas lógicas. |

---

