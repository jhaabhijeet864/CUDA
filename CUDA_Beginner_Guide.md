# CUDA Programming: A Comprehensive Beginner's Guide

## Table of Contents

1. Introduction to CUDA
2. Why Use CUDA?
3. GPU vs CPU: The Basics
4. Setting Up CUDA on Windows
5. Your First CUDA Program
6. Anatomy of a CUDA Program
7. Memory Management in CUDA
8. Thread Hierarchy: Grids, Blocks, and Threads
9. Synchronization and Race Conditions
10. Error Handling in CUDA
11. Advanced Topics
12. Useful Resources

---

## 1. Introduction to CUDA

CUDA (Compute Unified Device Architecture) is a parallel computing platform and programming model developed by NVIDIA. It allows developers to use NVIDIA GPUs for general purpose processing (GPGPU).

## 2. Why Use CUDA?

- Massive parallelism: Thousands of threads run concurrently.
- Speed: GPUs can be much faster than CPUs for certain tasks.
- Widely used in AI, scientific computing, graphics, and more.

## 3. GPU vs CPU: The Basics

- **CPU**: Few cores, optimized for sequential serial processing.
- **GPU**: Many cores, optimized for parallel processing.

## 4. Setting Up CUDA on Windows

1. Install the latest NVIDIA driver for your GPU.
2. Download and install the [CUDA Toolkit](https://developer.nvidia.com/cuda-downloads).
3. Install a C++ compiler (Visual Studio is recommended).
4. Set environment variables if needed.

## 5. Your First CUDA Program

Let's write a simple program that adds two arrays.

### File: `vector_add.cu`

```cpp
#include <iostream>
#define N 512

__global__ void vectorAdd(float *a, float *b, float *c) {
    int i = threadIdx.x;
    c[i] = a[i] + b[i];
}

int main() {
    float a[N], b[N], c[N];
    float *d_a, *d_b, *d_c;

    // Initialize arrays
    for (int i = 0; i < N; i++) {
        a[i] = i;
        b[i] = i * 2;
    }

    // Allocate memory on GPU
    cudaMalloc((void**)&d_a, N * sizeof(float));
    cudaMalloc((void**)&d_b, N * sizeof(float));
    cudaMalloc((void**)&d_c, N * sizeof(float));

    // Copy data to GPU
    cudaMemcpy(d_a, a, N * sizeof(float), cudaMemcpyHostToDevice);
    cudaMemcpy(d_b, b, N * sizeof(float), cudaMemcpyHostToDevice);

    // Launch kernel
    vectorAdd<<<1, N>>>(d_a, d_b, d_c);

    // Copy result back
    cudaMemcpy(c, d_c, N * sizeof(float), cudaMemcpyDeviceToHost);

    // Print first 10 results
    for (int i = 0; i < 10; i++)
        std::cout << c[i] << " ";
    std::cout << std::endl;

    // Free GPU memory
    cudaFree(d_a); cudaFree(d_b); cudaFree(d_c);
    return 0;
}
```

### How to Compile and Run

```
nvcc vector_add.cu -o vector_add
./vector_add
```

## 6. Anatomy of a CUDA Program

- **Host**: The CPU and its memory (RAM).
- **Device**: The GPU and its memory.
- **Kernel**: A function that runs on the GPU, called from the host.
- **Memory Transfers**: Data must be copied between host and device.

## 7. Memory Management in CUDA

- `cudaMalloc` allocates memory on the GPU.
- `cudaMemcpy` copies data between host and device.
- `cudaFree` releases GPU memory.

## 8. Thread Hierarchy: Grids, Blocks, and Threads

- **Grid**: Collection of blocks.
- **Block**: Collection of threads.
- **Thread**: Smallest unit of execution.

Example:

```cpp
__global__ void myKernel() {
    int blockId = blockIdx.x;
    int threadId = threadIdx.x;
    // ...
}
```

## 9. Synchronization and Race Conditions

- Use `__syncthreads()` to synchronize threads within a block.
- Avoid race conditions by careful memory access.

## 10. Error Handling in CUDA

Always check for errors:

```cpp
cudaError_t err = cudaMalloc(...);
if (err != cudaSuccess) {
    printf("CUDA error: %s\n", cudaGetErrorString(err));
}
```

## 11. Advanced Topics

- Shared memory
- Streams and concurrency
- Unified memory
- Profiling and optimization

## 12. Useful Resources

- [CUDA C Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html)
- [CUDA Toolkit Documentation](https://docs.nvidia.com/cuda/)
- [NVIDIA Developer Forums](https://forums.developer.nvidia.com/)

---

This guide provides a strong foundation for learning CUDA. Try modifying the example, experiment with thread/block sizes, and explore the official documentation for deeper understanding.
