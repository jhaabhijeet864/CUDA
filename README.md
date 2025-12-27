<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/sco/2/21/Nvidia_logo.svg" width="280" alt="NVIDIA Logo">
</p>

<h1 align="center">CUDA & GPU Programming</h1>

<p align="center">
  <strong>High-performance parallel computing with NVIDIA CUDA</strong>
</p>

<p align="center">
  <a href="https://developer.nvidia.com/cuda-toolkit"><img src="https://img.shields.io/badge/CUDA-Toolkit-76B900?style=for-the-badge&logo=nvidia&logoColor=white" alt="CUDA Toolkit"></a>
  <a href="https://docs.nvidia.com/cuda/"><img src="https://img.shields.io/badge/CUDA-C%2B%2B-76B900?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="CUDA C++"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-76B900?style=for-the-badge" alt="MIT License"></a>
</p>

---

## Overview

This repository contains my CUDA projects, code samples, and GPU programming experiments. It serves as both a learning resource and a portfolio of parallel computing work using NVIDIA's CUDA platform.

**What's inside:**
- Foundational CUDA kernels and memory management examples
- Performance optimization techniques
- Real-world GPU-accelerated applications
- Beginner-friendly documentation and guides

---

## Getting Started

### Prerequisites

- NVIDIA GPU with CUDA support
- [CUDA Toolkit](https://developer.nvidia.com/cuda-downloads) (11.0+)
- C++ compiler (GCC/Clang/MSVC)

### Installation

```bash
git clone https://github.com/jhaabhijeet864/CUDA.git
cd CUDA
```

### Build & Run

```bash
nvcc vector_add.cu -o vector_add
./vector_add
```

---

## Repository Structure

```
CUDA/
├── CUDA_Beginner_Guide.md    # Getting started with CUDA
├── vector_add.cu             # Basic vector addition kernel
├── matrix_mul.cu             # Matrix multiplication
├── shared_memory/            # Shared memory examples
├── streams/                  # CUDA streams & async
└── README.md
```

---

## Why CUDA?

CUDA enables developers to harness the massive parallelism of NVIDIA GPUs. With thousands of cores working simultaneously, tasks that take minutes on a CPU can complete in seconds.

**Key advantages:**
- Massive parallel execution across GPU cores
- Direct memory management for optimal data transfer
- Industry-standard for AI/ML, scientific computing, and graphics
- Extensive tooling: profilers, debuggers, and libraries

---

## Learning Resources

| Resource | Description |
|----------|-------------|
| [CUDA Beginner Guide](CUDA_Beginner_Guide.md) | Start here if you're new to CUDA |
| [CUDA C Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/) | Official NVIDIA documentation |
| [CUDA Samples](https://github.com/NVIDIA/cuda-samples) | NVIDIA's official code samples |
| [Nsight Systems](https://developer.nvidia.com/nsight-systems) | Performance analysis tool |

---

## Topics Covered

- **Kernel Basics** — Thread hierarchy, grid/block configuration
- **Memory Model** — Global, shared, constant, and texture memory
- **Synchronization** — Thread barriers, atomic operations
- **Streams** — Concurrent kernel execution, async transfers
- **Optimization** — Coalesced access, occupancy tuning, warp efficiency
- **cuBLAS/cuDNN** — Leveraging NVIDIA's optimized libraries

---

## Contributing

Contributions are welcome! If you'd like to add examples, fix bugs, or improve documentation:

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/new-example`)
3. Commit your changes (`git commit -m 'Add new kernel example'`)
4. Push to the branch (`git push origin feature/new-example`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

<p align="center">
  <img src="https://img.shields.io/badge/NVIDIA-76B900?style=flat-square&logo=nvidia&logoColor=white" alt="NVIDIA">
  <img src="https://img.shields.io/badge/CUDA-000000?style=flat-square&logo=nvidia&logoColor=76B900" alt="CUDA">
  <img src="https://img.shields.io/badge/C%2B%2B-00599C?style=flat-square&logo=c%2B%2B&logoColor=white" alt="C++">
</p>

<p align="center">
  <sub>Built with 💚 by <a href="https://github.com/jhaabhijeet864">@jhaabhijeet864</a></sub>
</p>
