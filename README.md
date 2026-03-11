# Parallel Computing with OpenMP and CUDA

## Descripción del Proyecto
Este repositorio contiene la implementación y análisis de dos problemas clásicos de computación numérica utilizando diferentes modelos de ejecución: secuencial, paralelización en CPU mediante OpenMP y paralelización en GPU mediante CUDA.

El proyecto fue desarrollado en C como parte de una práctica académica de computación paralela, con el objetivo de comparar el comportamiento y rendimiento de distintas arquitecturas de ejecución en cargas de cálculo intensivo.

Los dos problemas abordados son:
* Aproximación numérica de una integral definida mediante la regla del trapecio.
* Producto matriz-vector (MxV) ejecutado repetidamente para simular una carga de cálculo intensiva.

El proyecto incluye la implementación completa de las versiones secuenciales y paralelas, así como el análisis de rendimiento obtenido en cada caso.

---

## Arquitectura y Paralelización

El proyecto implementa tres modelos de ejecución diferentes para cada problema computacional:

* **Ejecución Secuencial:** Implementación base en CPU sin paralelización, utilizada como referencia para medir el rendimiento.
* **Paralelización con OpenMP:** Uso de directivas `#pragma omp` para distribuir el trabajo entre múltiples hilos de CPU, permitiendo aprovechar arquitecturas multinúcleo.
* **Paralelización con CUDA:** Implementación mediante kernels GPU donde el trabajo se distribuye entre bloques e hilos, explotando el paralelismo masivo de la arquitectura CUDA.

El diseño permite comparar directamente las tres estrategias de ejecución sobre los mismos algoritmos.

---

## Problemas Computacionales Implementados

### Aproximación de Integrales
La integral definida en el intervalo `[0,100]` se aproxima mediante la **regla del trapecio**, dividiendo el intervalo en \(2^n\) subintervalos.

Las versiones paralelas distribuyen el cálculo de los trapecios entre múltiples hilos (OpenMP) o entre bloques e hilos en GPU (CUDA), reduciendo posteriormente los resultados parciales.

---

### Producto Matriz-Vector (MxV)
Se implementa el cálculo de un producto matriz-vector \(A \cdot x\) donde:

* \(A\) es una matriz cuadrada de tamaño \(N \times N\)
* \(x\) es un vector de tamaño \(N\)

Para simular una carga de cálculo intensiva, el producto se repite múltiples veces.

En la versión paralela:

* **OpenMP** distribuye las filas de la matriz entre hilos de CPU.
* **CUDA** asigna cada componente del vector resultado a un hilo GPU.

---

## Evaluación del Rendimiento
El proyecto compara el tiempo de ejecución de las implementaciones secuenciales y paralelas para diferentes tamaños de problema.

Los resultados permiten analizar:

* Speedup obtenido mediante paralelización
* Escalabilidad con el tamaño del problema
* Diferencias entre paralelismo en CPU (OpenMP) y GPU (CUDA)

Este tipo de análisis es fundamental en computación de alto rendimiento (HPC) para determinar qué arquitectura resulta más eficiente en cada tipo de carga.

---

## Estructura de Archivos
* `integral.c` – Implementación secuencial de la aproximación de la integral.
* `integralp.c` – Versión paralela utilizando OpenMP.
* `integralc.cu` – Implementación paralela utilizando CUDA.

* `mxv.c` – Implementación secuencial del producto matriz-vector.
* `mxvp.c` – Versión paralela con OpenMP.
* `mxvc.cu` – Implementación paralela con CUDA.

* `Trabajo SPD - OpenMP y Cuda.pdf` – Memoria técnica del proyecto con análisis experimental y resultados obtenidos.

---

## Stack Tecnológico
* **Lenguaje:** C
* **Paralelización CPU:** OpenMP
* **Paralelización GPU:** CUDA
* **Paradigma:** Computación Paralela / High Performance Computing (HPC)
