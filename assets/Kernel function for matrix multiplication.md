- CUDA-specific keyword “__global__” in front of the declaration of `MatrixMulKernel()`.
- This keyword indicates that the function is a kernel and that it can be called from a host functions to generate a grid of threads on a device.
- The __device__ keyword indicates that the function being declared is a CUDA device function.
![[Pasted image 20250601145154.png]]
- Device functions can have neither recursive function calls nor indirect function calls through pointers in them.
- By default, all functions in a CUDA program are host functions if they do not have any of the CUDA keywords in their declaration.
- Different threads will see different values in their `threadIdx.x` and `threadIdx.y` variables. For simplicity, we will refer to a thread as Thread `threadIdx.x`, `threadIdx.y`. Note that the coordinates reflect a multidimensional organization for the threads.
- [[CPU-only matrix multiplication]] has only one loop, which corresponds to the innermost loop. 
- One should ask where the other two levels of outer loops go. The answer is that the outer two loop levels are now replaced with the grid of threads. 
- The entire grid forms the equivalent of the two-level loop. Each thread in the grid corresponds to one of the iterations of the original two-level loop. 
- The original loop variables `i` and `j` are now replaced with `threadIdx.x` and `threadIdx.y`. 
- Instead of having the loop increment the values of `i` and `j` for use in each loop iteration, the CUDA threading hardware generates all of the `threadIdx.x` and `threadIdx.y` values for each thread.
- Threads in a grid are organized into a two-level hierarchy. 
![[Pasted image 20250601151802.png]]