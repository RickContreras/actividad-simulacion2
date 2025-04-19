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

3. How would you configure the scheduler parameters to behave just like a round-robin scheduler?

   <details>
   <summary>Answer</summary>
   Coloque aqui su respuerta
   </details>
   <br>

4. Craft a workload with two jobs and scheduler parameters so that one job takes advantage of the older Rules 4a and 4b (turned on
with the -S flag) to game the scheduler and obtain 99% of the CPU over a particular time interval.

   <details>
   <summary>Answer</summary>
   Coloque aqui su respuerta
   </details>
   <br>

5. Given a system with a quantum length of 10 ms in its highest queue, how often would you have to boost jobs back to the highest priority level (with the `-B` flag) in order to guarantee that a single longrunning (and potentially-starving) job gets at least 5% of the CPU?

   <details>
   <summary>Answer</summary>
   Coloque aqui su respuerta
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