# Programacion_Paralela_GGV



 # Investigación CUDA Cores, Threads, Blocks and Grids
## Cuda Core
Una matriz es una estructura de datos bidimensional compuesta por filas y columnas. Se puede representar matemáticamente como una matriz A con dimensiones m × n, donde m es el número de filas y n es el número de columnas. Cada elemento de la matriz se denomina "entrada" y se identifica mediante su posición en la fila y la columna.

## Thread
Un hilo en el contexto de CUDA es una secuencia de instrucciones que se ejecuta en un núcleo CUDA. Los hilos son las unidades más pequeñas de trabajo que se pueden asignar a un núcleo CUDA.

Los hilos son especialmente útiles para dividir tareas en partes más pequeñas y ejecutarlas en paralelo en múltiples núcleos CUDA. Esto permite un procesamiento masivamente paralelo y un rendimiento mejorado.


## Block
Un bloque en CUDA es un grupo de hilos que se ejecutan en el mismo multiprocesador de la GPU. Los bloques se utilizan para dividir y organizar el trabajo en grupos más manejables.

Los hilos dentro de un bloque pueden cooperar y compartir datos a través de una memoria compartida local, lo que facilita la comunicación entre los hilos del mismo bloque.


## Grid
Un grid en CUDA es una colección de bloques. Los bloques dentro de un grid pueden ejecutarse en paralelo, pero los bloques en sí pueden no necesariamente ejecutarse al mismo tiempo.

Los grids se utilizan para organizar y coordinar el trabajo en una GPU, especialmente cuando se trabaja con grandes cantidades de datos o tareas complejas que requieren múltiples bloques.



## Conclusion
En conclusión estos conceptos son fundamentales para comprender y aprovechar el poder de las GPU en la programación paralela. CUDA Cores son las unidades de procesamiento básicas en una GPU, Threads son las unidades de trabajo individuales, Blocks agrupan hilos para la ejecución eficiente y Grids organizan múltiples bloques para tareas más amplias. Estos conceptos permiten a los desarrolladores diseñar y ejecutar algoritmos altamente paralelos, acelerando significativamente el procesamiento de datos en una variedad de aplicaciones

## Fuentes y Referencias

https://hardzone.es/marcas/nvidia/nucleos-cuda/

https://hardwaresfera.com/articulos/hablamos-profundidad-los-nvidia-cuda-core/

https://www.youtube.com/watch?v=4vHvmSB-NMQ&ab_channel=Pepelpro




