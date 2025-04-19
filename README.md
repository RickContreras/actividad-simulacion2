# 🚀 MLFQ Scheduler Simulation Activity Report

![GitHub](https://img.shields.io/badge/GitHub-RickContreras%20%7C%20Sag0719-181717?style=for-the-badge&logo=github)
![Platform](https://img.shields.io/badge/Platform-Python-3776AB?style=for-the-badge&logo=python)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![Version](https://img.shields.io/badge/Version-1.0-blue?style=for-the-badge)
|Integrante|Correo|Usuario GitHub|
|---|---|---|
| Ricardo Contreras Garzón | ricardo.contreras1@udea.edu.co | [RickContreras](https://github.com/RickContreras) |
| Santiago Arenas Gómez | santiago.arenas1@udea.edu.co |[Sag0719](https://github.com/Sag0719)

## 📋 Índice
- [📚 Introducción](#-introducción)
- [🔬 Simulaciones y Respuestas](#-simulaciones-y-respuestas)
  - [1️⃣ Ejecución con 2 trabajos y 2 colas sin I/O](#1️⃣-ejecución-con-2-trabajos-2-colas-y-sin-io)
  - [2️⃣ Reproducción de ejemplos del capítulo](#2️⃣-reproducción-de-ejemplos-del-capítulo)
  - [3️⃣ Configuración como Round-Robin](#3️⃣-configuración-como-round-robin)
  - [4️⃣ Aprovechamiento de reglas 4a y 4b](#4️⃣-aprovechamiento-de-reglas-4a-y-4b)
  - [5️⃣ Prioridad mínima garantizada y Boost](#5️⃣-prioridad-mínima-garantizada-y-boost)
  - [6️⃣ Efecto de la posición después de I/O](#6️⃣-efecto-de-la-posición-después-de-io)
- [💡 Conclusiones](#-conclusiones)
- [📚 Referencias](#-referencias)

## 📚 Introducción

Esta actividad presenta los resultados de simulaciones utilizando el programa `mlfq.py`, que implementa el algoritmo de planificación **Multi-Level Feedback Queue (MLFQ)**. A través de diferentes configuraciones y escenarios, se analizan las características fundamentales de este importante algoritmo de planificación y se observa cómo responde ante distintas cargas de trabajo.

![MLFQ Diagram](https://img.shields.io/badge/MLFQ-Scheduler-orange?style=flat-square&logo=buffer)

El planificador MLFQ es ampliamente utilizado en sistemas operativos modernos debido a su capacidad para balancear eficiencia y equidad, favoreciendo a procesos interactivos sin penalizar excesivamente a los procesos por lotes. Las simulaciones realizadas nos permiten visualizar y comprender el comportamiento práctico de los conceptos teóricos estudiados sobre este algoritmo.

   <details>
   <summary> ⚙️ Instalación y Configuración </summary>

   ### 1️⃣ Requisitos previos
   Asegúrate de tener instalado:
   - **Python 3.12.1** o superior
   - **pip 25.0.1** o superior (Opcional)

   Verifica las versiones instaladas ejecutando:
   ```bash
   python3 --version
   pip3 --version
   ```

   ### 2️⃣ Clonar el repositorio

   Clona este repositorio en tu máquina local:
   ```bash
   git clone https://github.com/RickContreras/mlfq-scheduler-simulation
   cd mlfq-scheduler-simulation
   ```

   ### 3️⃣ Ejecutar el simulador

   Ejecuta el simulador con el siguiente comando:

   ```bash
   python3 mlfq.py [opciones]
   ```

   ### 4️⃣ Opciones comunes

   Algunas opciones útiles para el simulador:

   - `-j`: Número de trabajos.
   - `-n`: Número de colas.
   - `-q`: Quantum para cada cola.
   - `-B`: Intervalo de boost (en ms).
   - `-I`: Priorizar trabajos que terminan I/O.

   Consulta la ayuda completa con:

   ```bash
   python3 mlfq.py --help
   ```

   </details>
   <br>

## 🔬 Simulaciones y Respuestas

### 1️⃣ Ejecución con 2 trabajos, 2 colas y sin I/O.

   <details>
   <summary>Solución</summary>

   > **Objetivo**: Ejecutar problemas generados aleatoriamente con solo dos trabajos y dos colas, calculando la traza de ejecución MLFQ para cada uno.

   **Comando utilizado:**
   ```bash
   python3 mlfq.py -j 2 -n 2 -m 20 -M 0
   ```

   **Parámetros:**
   - `-j 2`: 2 trabajos
   - `-n 2`: 2 colas
   - `-m 20`: Tiempo máximo de ejecución de 20ms
   - `-M 0`: Sin operaciones de I/O

   <details>
   <summary><b>Ver detalles de la configuración y trabajos</b></summary>

   <table>
   <tr>
      <th colspan="2">Configuración del Simulador</th>
   </tr>
   <tr>
      <td>Trabajos</td>
      <td>2</td>
   </tr>
   <tr>
      <td>Colas</td>
      <td>2</td>
   </tr>
   <tr>
      <td>Asignación para cola 1</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 1</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Asignación para cola 0</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 0</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Boost</td>
      <td>0 (desactivado)</td>
   </tr>
   <tr>
      <td>Tiempo de I/O</td>
      <td>5ms</td>
   </tr>
   <tr>
      <td>Mantener prioridad después de I/O</td>
      <td>No</td>
   </tr>
   <tr>
      <td>Priorizar trabajos que terminan I/O</td>
      <td>No</td>
   </tr>
   </table>

   <table>
   <tr>
      <th colspan="4">Lista de Trabajos</th>
   </tr>
   <tr>
      <th>Trabajo</th>
      <th>Tiempo de inicio</th>
      <th>Tiempo de ejecución</th>
      <th>Frecuencia I/O</th>
   </tr>
   <tr>
      <td>Job 0</td>
      <td>0</td>
      <td>17ms</td>
      <td>0 (sin I/O)</td>
   </tr>
   <tr>
      <td>Job 1</td>
      <td>0</td>
      <td>8ms</td>
      <td>0 (sin I/O)</td>
   </tr>
   </table>
   </details>

   **Análisis:**

   En esta simulación inicial, analizamos el comportamiento del planificador MLFQ con dos trabajos sencillos sin operaciones de I/O:

   1. Ambos trabajos inician al mismo tiempo (t=0) y en la cola de mayor prioridad (1)
   2. Como Job 0 tiene mayor tiempo de CPU requerido (17ms), el planificador:
      - Ejecuta Job 0 durante su quantum completo (10ms)
      - Desciende Job 0 a la cola de menor prioridad (0)
      - Cambia a Job 1 y lo ejecuta durante 8ms (completándolo)
      - Regresa a Job 0 para finalizar los 7ms restantes

   Esta simulación ilustra el principio básico de funcionamiento del MLFQ: penalizar a los trabajos intensivos en CPU bajándolos de prioridad y favorecer a los trabajos más cortos.
   </details>
   <br>

### 2️⃣ Reproducción de ejemplos del capítulo
   <details>
   <summary>Solución</summary>
   
   > **Objetivo**: Configurar el simulador para reproducir ejemplos específicos del capítulo sobre MLFQ.

   **Comando utilizado:**
   ```bash
   python3 mlfq.py --jlist 0,180,0:100,20,0 -q 10
   ```

   **Parámetros:**
   - `--jlist 0,180,0:100,20,0`: Define dos trabajos específicos:
   - Job 0: comienza en tiempo 0, necesita 180ms de CPU, sin I/O
   - Job 1: comienza en tiempo 100, necesita 20ms de CPU, sin I/O
   - `-q 10`: Quantum de 10ms para todas las colas

   <details>
   <summary><b>Ver detalles de la configuración y trabajos</b></summary>

   <table>
   <tr>
      <th colspan="2">Configuración del Simulador</th>
   </tr>
   <tr>
      <td>Trabajos</td>
      <td>2</td>
   </tr>
   <tr>
      <td>Colas</td>
      <td>3</td>
   </tr>
   <tr>
      <td>Asignación para cola 2</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 2</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Asignación para cola 1</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 1</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Asignación para cola 0</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 0</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Boost</td>
      <td>0 (desactivado)</td>
   </tr>
   <tr>
      <td>Tiempo de I/O</td>
      <td>5ms</td>
   </tr>
   <tr>
      <td>Mantener prioridad después de I/O</td>
      <td>No</td>
   </tr>
   <tr>
      <td>Priorizar trabajos que terminan I/O</td>
      <td>No</td>
   </tr>
   </table>

   <table>
   <tr>
      <th colspan="4">Lista de Trabajos</th>
   </tr>
   <tr>
      <th>Trabajo</th>
      <th>Tiempo de inicio</th>
      <th>Tiempo de ejecución</th>
      <th>Frecuencia I/O</th>
   </tr>
   <tr>
      <td>Job 0</td>
      <td>0</td>
      <td>180ms</td>
      <td>0 (sin I/O)</td>
   </tr>
   <tr>
      <td>Job 1</td>
      <td>100</td>
      <td>20ms</td>
      <td>0 (sin I/O)</td>
   </tr>
   </table>
   </details>

   **Análisis:**

   Esta configuración reproduce un escenario similar al de la Figura 8.3 del capítulo sobre MLFQ. La simulación demuestra la capacidad del algoritmo para priorizar trabajos cortos recién llegados:

   1. Job 0 se inicia en t=0 y comienza a ejecutarse en la cola de mayor prioridad
   2. Después de consumir su quantum (10ms), Job 0 desciende a la siguiente cola
   3. Job 0 continúa ejecutándose, bajando de prioridad con cada quantum consumido
   4. Cuando Job 1 ingresa al sistema en t=100:
      - Obtiene la mayor prioridad (cola 2)
      - Preempta a Job 0 (que estará en una cola inferior)
      - Se ejecuta completamente (20ms) antes de que Job 0 pueda continuar

   Este comportamiento resalta la capacidad de MLFQ para favorecer procesos interactivos o de corta duración, mejorando la experiencia del usuario.
   </details>
   <br>

### 3️⃣ Configuración como Round-Robin
   <details>
   <summary>Solución</summary>

   > **Objetivo**: Configurar el planificador MLFQ para que se comporte exactamente como un planificador Round-Robin.

   **Comando utilizado:**
   ```bash
   python3 mlfq.py -n 1 -q 10
   ```

   **Parámetros:**
   - `-n 1`: Una sola cola
   - `-q 10`: Quantum de 10ms

   <details>
   <summary><b>Ver detalles de la configuración y trabajos</b></summary>

   <table>
   <tr>
      <th colspan="2">Configuración del Simulador</th>
   </tr>
   <tr>
      <td>Trabajos</td>
      <td>3</td>
   </tr>
   <tr>
      <td>Colas</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Asignación para cola 0</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 0</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Boost</td>
      <td>0 (desactivado)</td>
   </tr>
   <tr>
      <td>Tiempo de I/O</td>
      <td>5ms</td>
   </tr>
   <tr>
      <td>Mantener prioridad después de I/O</td>
      <td>No</td>
   </tr>
   <tr>
      <td>Priorizar trabajos que terminan I/O</td>
      <td>No</td>
   </tr>
   </table>

   <table>
   <tr>
      <th colspan="4">Lista de Trabajos</th>
   </tr>
   <tr>
      <th>Trabajo</th>
      <th>Tiempo de inicio</th>
      <th>Tiempo de ejecución</th>
      <th>Frecuencia I/O</th>
   </tr>
   <tr>
      <td>Job 0</td>
      <td>0</td>
      <td>84ms</td>
      <td>7ms</td>
   </tr>
   <tr>
      <td>Job 1</td>
      <td>0</td>
      <td>42ms</td>
      <td>3ms</td>
   </tr>
   <tr>
      <td>Job 2</td>
      <td>0</td>
      <td>51ms</td>
      <td>4ms</td>
   </tr>
   </table>
   </details>

   **Análisis:**

   Para convertir el MLFQ en un planificador Round-Robin puro, simplemente configuramos el sistema con una única cola:

   1. Al eliminar la estructura multinivel, todos los trabajos permanecen siempre en la misma cola
   2. Con un quantum de 10ms, el planificador alterna cíclicamente entre los tres trabajos
   3. La secuencia de ejecución sigue el patrón: Job 0 → Job 1 → Job 2 → Job 0 → ...
   4. Las operaciones de I/O interrumpen este ciclo, pero una vez que un trabajo finaliza su I/O, vuelve a la única cola existente

   Este ejemplo demuestra la flexibilidad del MLFQ: con la configuración adecuada, puede comportarse como otros algoritmos de planificación más simples.

   ![Round Robin](https://img.shields.io/badge/Round_Robin-Simulation-brightgreen?style=flat-square&logo=clockify)
   </details>
   <br>

### 4️⃣ Aprovechamiento de reglas 4a y 4b

   <details>
   <summary>Solución</summary>

   > **Objetivo**: Crear una carga de trabajo que aproveche las reglas antiguas 4a y 4b para "engañar" al planificador y obtener casi todo el tiempo de CPU.

   **Comando utilizado:**
   ```bash
   python3 mlfq.py --jlist 0,100,10:0,100,0 -n 2 -q 10 -S
   ```

   **Parámetros:**
   - `--jlist 0,100,10:0,100,0`: Define dos trabajos específicos:
   - Job 0: comienza en tiempo 0, necesita 100ms de CPU, realiza I/O cada 10ms
   - Job 1: comienza en tiempo 0, necesita 100ms de CPU, sin I/O
   - `-n 2`: 2 colas
   - `-q 10`: Quantum de 10ms para todas las colas
   - `-S`: Activa las reglas 4a y 4b (mantiene el trabajo en la misma cola después de I/O)

   <details>
   <summary><b>Ver detalles de la configuración y trabajos</b></summary>

   <table>
   <tr>
      <th colspan="2">Configuración del Simulador</th>
   </tr>
   <tr>
      <td>Trabajos</td>
      <td>2</td>
   </tr>
   <tr>
      <td>Colas</td>
      <td>2</td>
   </tr>
   <tr>
      <td>Asignación para cola 1</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 1</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Asignación para cola 0</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 0</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Boost</td>
      <td>0 (desactivado)</td>
   </tr>
   <tr>
      <td>Tiempo de I/O</td>
      <td>5ms</td>
   </tr>
   <tr>
      <td>Mantener prioridad después de I/O</td>
      <td>Sí</td>
   </tr>
   <tr>
      <td>Priorizar trabajos que terminan I/O</td>
      <td>No</td>
   </tr>
   </table>

   <table>
   <tr>
      <th colspan="4">Lista de Trabajos</th>
   </tr>
   <tr>
      <th>Trabajo</th>
      <th>Tiempo de inicio</th>
      <th>Tiempo de ejecución</th>
      <th>Frecuencia I/O</th>
   </tr>
   <tr>
      <td>Job 0</td>
      <td>0</td>
      <td>100ms</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Job 1</td>
      <td>0</td>
      <td>100ms</td>
      <td>0 (sin I/O)</td>
   </tr>
   </table>
   </details>

   **Análisis:**

   Esta simulación expone una vulnerabilidad en la implementación original del MLFQ (reglas 4a y 4b) que permite a un trabajo astuto "engañar" al planificador:

   1. Job 0 realiza I/O estratégicamente cada 10ms (justo antes de agotar su quantum)
   2. Con la bandera `-S` activada, Job 0 permanece en la cola de mayor prioridad después de cada I/O
   3. Mientras tanto, Job 1 agota su quantum completo y desciende a la cola de menor prioridad
   4. Como resultado, Job 0 obtiene ≈99% del tiempo de CPU, ya que siempre tiene mayor prioridad

   Este comportamiento abusivo ilustra por qué las reglas del MLFQ fueron modificadas posteriormente en implementaciones modernas: para evitar que procesos maliciosos o mal diseñados monopolicen los recursos del sistema.

   ![Gaming the Scheduler](https://img.shields.io/badge/Gaming_the_Scheduler-Detected-red?style=flat-square&logo=gamepad)
   </details>
   <br>

### 5️⃣ Prioridad mínima garantizada y Boost

   <details>
   <summary>Solución</summary>

   > **Objetivo**: Determinar la frecuencia de boost necesaria para garantizar que un trabajo de larga duración obtenga al menos el 5% del CPU.

   **Comando utilizado:**
   ```bash
   python3 mlfq.py -n 3 -q 10 -B 200
   ```

   **Parámetros:**
   - `-n 3`: 3 colas
   - `-q 10`: Quantum de 10ms para todas las colas
   - `-B 200`: Boost cada 200ms (restablece todos los trabajos a la cola de mayor prioridad)

   <details>
   <summary><b>Ver detalles de la configuración y trabajos</b></summary>

   <table>
   <tr>
      <th colspan="2">Configuración del Simulador</th>
   </tr>
   <tr>
      <td>Trabajos</td>
      <td>3</td>
   </tr>
   <tr>
      <td>Colas</td>
      <td>3</td>
   </tr>
   <tr>
      <td>Asignación para cola 2</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 2</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Asignación para cola 1</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 1</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Asignación para cola 0</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 0</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Boost</td>
      <td>200</td>
   </tr>
   <tr>
      <td>Tiempo de I/O</td>
      <td>5ms</td>
   </tr>
   <tr>
      <td>Mantener prioridad después de I/O</td>
      <td>No</td>
   </tr>
   <tr>
      <td>Priorizar trabajos que terminan I/O</td>
      <td>No</td>
   </tr>
   </table>

   <table>
   <tr>
      <th colspan="4">Lista de Trabajos</th>
   </tr>
   <tr>
      <th>Trabajo</th>
      <th>Tiempo de inicio</th>
      <th>Tiempo de ejecución</th>
      <th>Frecuencia I/O</th>
   </tr>
   <tr>
      <td>Job 0</td>
      <td>0</td>
      <td>84ms</td>
      <td>7ms</td>
   </tr>
   <tr>
      <td>Job 1</td>
      <td>0</td>
      <td>42ms</td>
      <td>3ms</td>
   </tr>
   <tr>
      <td>Job 2</td>
      <td>0</td>
      <td>51ms</td>
      <td>4ms</td>
   </tr>
   </table>
   </details>

   **Análisis:**

   Para prevenir la inanición de procesos de larga duración, el mecanismo de boost periódico es esencial:

   1. Con un quantum de 10ms en la cola más alta y un requisito de 5% del CPU para cualquier trabajo:
      - Necesitamos que el proceso obtenga al menos 10ms cada 200ms (10/200 = 5%)
   2. Configurando el boost cada 200ms (`-B 200`), garantizamos que:
      - Todos los trabajos son elevados a la cola más alta periódicamente
      - Cada trabajo tendrá la oportunidad de ejecutar al menos un quantum completo
      - Ningún trabajo puede sufrir inanición indefinida

   Este mecanismo proporciona una garantía de servicio mínimo para todos los procesos, independientemente de su comportamiento o tipo, lo que es crucial para la estabilidad del sistema.

   ![Priority Boost](https://img.shields.io/badge/Priority_Boost-Anti--Starvation-blue?style=flat-square&logo=arrow-up)
   </details>
   <br>

### 6️⃣ Efecto de la posición después de I/O

   <details>
   <summary>Solución</summary>

   > **Objetivo**: Investigar el efecto de cambiar la posición donde se añaden los trabajos que acaban de terminar operaciones de I/O.

   **Comando utilizado:**
   ```bash
   python3 mlfq.py --jlist 0,50,10:10,50,10 -n 2 -q 10 -I
   ```

   **Parámetros:**
   - `--jlist 0,50,10:10,50,10`: Define dos trabajos específicos:
   - Job 0: comienza en tiempo 0, necesita 50ms de CPU, realiza I/O cada 10ms
   - Job 1: comienza en tiempo 10, necesita 50ms de CPU, realiza I/O cada 10ms
   - `-n 2`: 2 colas
   - `-q 10`: Quantum de 10ms para todas las colas
   - `-I`: Los trabajos que terminan I/O se colocan al frente de la cola

   <details>
   <summary><b>Ver detalles de la configuración y trabajos</b></summary>

   <table>
   <tr>
      <th colspan="2">Configuración del Simulador</th>
   </tr>
   <tr>
      <td>Trabajos</td>
      <td>2</td>
   </tr>
   <tr>
      <td>Colas</td>
      <td>2</td>
   </tr>
   <tr>
      <td>Asignación para cola 1</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 1</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Asignación para cola 0</td>
      <td>1</td>
   </tr>
   <tr>
      <td>Quantum para cola 0</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Boost</td>
      <td>0 (desactivado)</td>
   </tr>
   <tr>
      <td>Tiempo de I/O</td>
      <td>5ms</td>
   </tr>
   <tr>
      <td>Mantener prioridad después de I/O</td>
      <td>No</td>
   </tr>
   <tr>
      <td>Priorizar trabajos que terminan I/O</td>
      <td>Sí</td>
   </tr>
   </table>

   <table>
   <tr>
      <th colspan="4">Lista de Trabajos</th>
   </tr>
   <tr>
      <th>Trabajo</th>
      <th>Tiempo de inicio</th>
      <th>Tiempo de ejecución</th>
      <th>Frecuencia I/O</th>
   </tr>
   <tr>
      <td>Job 0</td>
      <td>0</td>
      <td>50ms</td>
      <td>10ms</td>
   </tr>
   <tr>
      <td>Job 1</td>
      <td>10</td>
      <td>50ms</td>
      <td>10ms</td>
   </tr>
   </table>
   </details>

   **Análisis:**

   La bandera `-I` (iobump) modifica significativamente el comportamiento del planificador al dar preferencia a los trabajos que terminan operaciones de I/O:

   1. Normalmente, los trabajos que completan I/O se colocan al final de su cola actual
   2. Con `-I` activado, estos trabajos se colocan al frente de su cola
   3. Este cambio beneficia a procesos que realizan I/O frecuentemente:
      - Se les da servicio más rápidamente después de cada operación de I/O
      - Se genera un comportamiento de "ping-pong" entre trabajos con I/O frecuente
      - Mejora la interactividad percibida del sistema

   Este parámetro es especialmente útil para sistemas interactivos donde la respuesta rápida a eventos de I/O (como entrada de teclado, mouse o interfaces de red) es más importante que la eficiencia global.

   ![I/O Priority](https://img.shields.io/badge/I/O_Priority-Enhanced_Interactivity-purple?style=flat-square&logo=input-output)
   </details>
   <br>

## 💡 Conclusiones

Tras analizar los resultados de las diversas simulaciones realizadas con el planificador MLFQ, podemos destacar las siguientes conclusiones:

1. **🔄 Flexibilidad adaptativa**: MLFQ demuestra una notable capacidad para adaptarse a diferentes cargas de trabajo. Puede configurarse para comportarse como un planificador Round-Robin simple o implementar un sofisticado sistema de prioridades dinámicas que favorece trabajos cortos e interactivos.

2. **⚖️ Balance entre equidad y rendimiento**: El algoritmo busca un equilibrio eficaz entre ser justo con todos los procesos y optimizar el rendimiento del sistema, favoreciendo ciertos tipos de trabajos sin penalizar excesivamente a otros.

3. **🛡️ Prevención de inanición**: El mecanismo de boost periódico es fundamental para garantizar que todos los procesos reciban una parte mínima del tiempo de CPU, previniendo la inanición de procesos de larga duración.

4. **🔒 Seguridad mejorada**: Las vulnerabilidades del diseño original (reglas 4a y 4b) han sido corregidas en implementaciones modernas, evitando que procesos maliciosos puedan manipular el planificador para obtener recursos desproporcionados.

5. **⚡ Gestión optimizada de I/O**: La estrategia para manejar procesos que completan operaciones de I/O tiene un impacto significativo en la interactividad del sistema. La colocación de estos procesos al frente de sus colas respectivas mejora la capacidad de respuesta percibida.

6. **🧩 Ajuste preciso**: Los parámetros del planificador (quantum, número de colas, frecuencia de boost, etc.) pueden ajustarse con precisión para optimizar el comportamiento del sistema según las necesidades específicas de cada entorno.

7. **📊 Versatilidad comprobada**: La amplia adopción de algoritmos basados en MLFQ en sistemas operativos modernos confirma su versatilidad y efectividad para gestionar eficientemente una amplia variedad de cargas de trabajo.

Estas simulaciones demuestran que MLFQ es un algoritmo de planificación robusto, adaptable y eficiente, capaz de ofrecer un buen rendimiento en entornos de computación complejos y diversos.

## 📚 Referencias

- Documentación del simulador MLFQ (proporcionada en la actividad)
- [Scheduling: Introduction (OS: Three Easy Pieces)](https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-sched.pdf)

![Footer](https://img.shields.io/badge/Universidad_de_Antioquia-Sistemas_Operativos-yellow?style=for-the)