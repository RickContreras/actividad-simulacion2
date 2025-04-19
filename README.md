# 🚀 MLFQ Scheduler Simulation Activity Report

![GitHub](https://img.shields.io/badge/GitHub-RickContreras%20%7C%20Sag0719-181717?style=for-the-badge&logo=github)
![Platform](https://img.shields.io/badge/Platform-Python-3776AB?style=for-the-badge&logo=python)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)
![Version](https://img.shields.io/badge/Version-1.0-blue?style=for-the-badge)
|Integrante|Correo|Usuario GitHub|
|---|---|---|
| Ricardo Contreras Garzón | ricardo.contreras1@udea.edu.co | [RickContreras](https://github.com/RickContreras) |
| Santiago Arenas Gómez | santiago.arenas1@udea.edu.co |[Sag0719](https://github.com/Sag0719)|

## 📚 Introducción

Esta actividad presenta los resultados de simulaciones utilizando el programa `mlfq.py`, que implementa el algoritmo de planificación **Multi-Level Feedback Queue (MLFQ)**. A través de diferentes configuraciones y escenarios, se analizan las características fundamentales de este importante algoritmo de planificación y se observa cómo responde ante distintas cargas de trabajo.

![MLFQ Diagram](https://img.shields.io/badge/MLFQ-Scheduler-orange?style=flat-square&logo=buffer)

El planificador MLFQ es ampliamente utilizado en sistemas operativos modernos debido a su capacidad para balancear eficiencia y equidad, favoreciendo a procesos interactivos sin penalizar excesivamente a los procesos por lotes. Las simulaciones realizadas nos permiten visualizar y comprender el comportamiento práctico de los conceptos teóricos estudiados sobre este algoritmo.

This program, [mlfq.py](mlfq.py), allows you to see how the MLFQ scheduler presented in this chapter behaves. See the [README](https://github.com/remzi-arpacidusseau/ostep-homework/blob/master/cpu-sched-mlfq/README.md) for details.


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

6. One question that arises in scheduling is which end of a queue to add a job that just finished I/O; the -I flag changes this behavior
for this scheduling simulator. Play around with some workloads and see if you can see the effect of this flag.

   <details>
   <summary>Answer</summary>
   Coloque aqui su respuerta
   </details>
   <br>

## 💡 Conclusiones

Coloque aqui las conclusiones...

## 📚 Referencias

- Documentación del simulador MLFQ (proporcionada en la actividad)
- [Scheduling: Introduction (OS: Three Easy Pieces)](https://pages.cs.wisc.edu/~remzi/OSTEP/cpu-sched.pdf)

![Footer](https://img.shields.io/badge/Universidad_de_Antioquia-Sistemas_Operativos-yellow?style=for-the)