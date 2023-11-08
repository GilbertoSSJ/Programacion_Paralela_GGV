### sumArrayZerocpy
~~~
==1049== NVPROF is profiling process 1049, command: ./sumArrayZerocpy
==1049== Warning: Unified Memory Profiling is not supported on the current configuration because a pair of devices without peer-to-peer support is detected on this multi-GPU setup. When peer mappings are not available, system falls back to using zero-copy memory. It can cause kernels, which access unified memory, to run slower. More details can be found at: http://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#um-managed-memory
==1049== Profiling application: ./sumArrayZerocpy
==1049== Profiling result:
            Type  Time(%)      Time     Calls       Avg       Min       Max  Name
 GPU activities:   33.33%  3.5200us         1  3.5200us  3.5200us  3.5200us  sumArraysZeroCopy(float*, float*, float*, int)
                   22.73%  2.4000us         2  1.2000us  1.1840us  1.2160us  [CUDA memcpy DtoH]
                   22.12%  2.3360us         1  2.3360us  2.3360us  2.3360us  sumArrays(float*, float*, float*, int)
                   21.82%  2.3040us         2  1.1520us     864ns  1.4400us  [CUDA memcpy HtoD]
      API calls:   94.24%  583.14ms         3  194.38ms  1.8000us  583.14ms  cudaMalloc
                    5.09%  31.475ms         1  31.475ms  31.475ms  31.475ms  cudaDeviceReset
                    0.35%  2.1756ms         1  2.1756ms  2.1756ms  2.1756ms  cuDeviceGetPCIBusId
                    0.16%  988.60us         2  494.30us  3.8000us  984.80us  cudaHostAlloc
                    0.06%  368.90us         2  184.45us  4.5000us  364.40us  cudaFreeHost
                    0.06%  358.00us         4  89.500us  33.100us  129.40us  cudaMemcpy
                    0.04%  218.20us         3  72.733us  2.5000us  208.10us  cudaFree
                    0.01%  60.300us         2  30.150us  28.600us  31.700us  cudaLaunchKernel
                    0.00%  14.900us       101     147ns     100ns  1.0000us  cuDeviceGetAttribute
                    0.00%  6.2000us         1  6.2000us  6.2000us  6.2000us  cudaSetDevice
                    0.00%  2.3000us         1  2.3000us  2.3000us  2.3000us  cudaGetDeviceProperties
                    0.00%  2.1000us         2  1.0500us     600ns  1.5000us  cudaHostGetDevicePointer
                    0.00%  1.6000us         3     533ns     200ns  1.0000us  cuDeviceGetCount
                    0.00%  1.1000us         2     550ns     200ns     900ns  cuDeviceGet
                    0.00%     700ns         1     700ns     700ns     700ns  cuDeviceGetName
                    0.00%     300ns         1     300ns     300ns     300ns  cuDeviceTotalMem
                    0.00%     200ns         1     200ns     200ns     200ns  cuDeviceGetUuid
~~~


En particular, la función "sumArraysZeroCopy" en la GPU realiza los cálculos de manera eficiente en microsegundos, mientras que otras tareas, como la asignación de memoria en el procesador, no son significativamente lentas. El uso del bus PCIe para la transferencia de datos contribuye al equilibrio general de tareas y mejora el rendimiento en comparación con enfoques convencionales.


### SimpleMathAoS 
~~~
==1011== NVPROF is profiling process 1011, command: ./simpleMathAoS
==1011== Warning: Unified Memory Profiling is not supported on the current configuration because a pair of devices without peer-to-peer support is detected on this multi-GPU setup. When peer mappings are not available, system falls back to using zero-copy memory. It can cause kernels, which access unified memory, to run slower. More details can be found at: http://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#um-managed-memory
==1011== Profiling application: ./simpleMathAoS
==1011== Profiling result:
            Type  Time(%)      Time     Calls       Avg       Min       Max  Name
 GPU activities:   80.19%  23.304ms         2  11.652ms  8.6804ms  14.623ms  [CUDA memcpy DtoH]
                   18.05%  5.2457ms         1  5.2457ms  5.2457ms  5.2457ms  [CUDA memcpy HtoD]
                    0.88%  256.10us         1  256.10us  256.10us  256.10us  warmup(innerStruct*, innerStruct*, int)
                    0.88%  255.85us         1  255.85us  255.85us  255.85us  testInnerStruct(innerStruct*, innerStruct*, int)
      API calls:   88.83%  566.38ms         2  283.19ms  376.90us  566.01ms  cudaMalloc
                    5.61%  35.742ms         1  35.742ms  35.742ms  35.742ms  cudaDeviceReset
                    4.90%  31.267ms         3  10.422ms  6.6946ms  15.576ms  cudaMemcpy
                    0.34%  2.1562ms         1  2.1562ms  2.1562ms  2.1562ms  cuDeviceGetPCIBusId
                    0.19%  1.2200ms         2  610.00us  446.90us  773.10us  cudaFree
                    0.11%  669.90us         2  334.95us  334.90us  335.00us  cudaDeviceSynchronize
                    0.03%  161.60us         2  80.800us  63.500us  98.100us  cudaLaunchKernel
                    0.00%  14.600us       101     144ns     100ns  1.3000us  cuDeviceGetAttribute
                    0.00%  6.1000us         1  6.1000us  6.1000us  6.1000us  cudaSetDevice
                    0.00%  5.8000us         2  2.9000us  2.6000us  3.2000us  cudaGetLastError
                    0.00%  4.7000us         1  4.7000us  4.7000us  4.7000us  cudaGetDeviceProperties
                    0.00%  1.4000us         3     466ns     200ns  1.0000us  cuDeviceGetCount
                    0.00%     800ns         2     400ns     100ns     700ns  cuDeviceGet
                    0.00%     600ns         1     600ns     600ns     600ns  cuDeviceGetName
                    0.00%     400ns         1     400ns     400ns     400ns  cuDeviceTotalMem
                    0.00%     200ns         1     200ns     200ns     200ns  cuDeviceGetUuid
~~~


El código realiza operaciones sencillas con un arreglo de estructuras y se enfoca en tres funciones principales. "cudaMalloc" se utiliza dos veces para asignar memoria en la memoria global. Luego, "cudaMemcpy" se emplea para transferir datos del dispositivo al host, consumiendo la mayor parte del tiempo de ejecución en la GPU, aproximadamente el 80% del tiempo total, con una duración de 23.304 ms. El proceso inverso, que implica copiar datos del host al dispositivo, consume la mayoría del tiempo restante en la GPU, con un tiempo de 5.2 ms.

En el lado del procesador, la asignación de memoria representa la mayor parte del tiempo, alrededor del 88% del tiempo total de ejecución, con un tiempo de 566.38 ms. Las funciones "cudaDeviceReset," que limpian los procesos de la GPU, y "cudaMemcpy," que involucra el intercambio de datos con la GPU, también consumen un tiempo significativo de 35.7 ms y 31.2 ms, respectivamente. El resto de los procesos disminuyen en tiempo de ejecución significativo en comparación con los mencionados anteriormente. En resumen, los intercambios de datos son las operaciones que más tiempo consumen tanto en la GPU como en el procesador.
