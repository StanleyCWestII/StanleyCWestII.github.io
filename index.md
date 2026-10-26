---
layout: default
---
My name is Stanley Christopher West II, and I have spent the past few months in deep self-study of digital design and GPU engineering.

## Project 1: RISC-V Core

I created a 5-stage pipelined RV32I processor core with a UART Echo and VGA Pattern Generator expansion, along with 2-bit branch prediction, a branch target buffer, a return address stack, an I-cache, and a D-cache. It runs on a Nexys A7 FPGA. I used Harris and Harris' Digital Design and Computer Architecture: RISC-V Edition for reference. 

While I wrote every line of the processor, I used AI to help benchmark and test it. The build passes 176/176 checks across 22 test programs and 40/40 of the official rv32ui tests (excluding fence_i and ma_data), and overcomes pipelining hazards with the use of forwarding, stalling, and flushing. On the board, the UART echo returned 760/760 bytes with zero errors (tested on the pre-cache build). The VGA generator is verified in simulation only. 

On the T8 loop benchmark, branch prediction brought cycles from 291 to 174 and mispredicts from 30 to 1. That is a 40.2% reduction against an always-taken baseline, or 33.8% against not-taken (263 cycles). 

My D-cache, implemented as 8 sets, 4 ways, 16 words, write-back, write-allocate, tree-based pseudo-LRU, and behind a 15-cycle main memory brought a 3.32-7.49x speedup in cycles. Most importantly to note, the processor's memory is too small to test directly. The 15-cycle latency is arbitrary in order to test the D-cache against realistic circumstances. 

[RISC-V Core](https://github.com/StanleyCWestII/riscv-pipelined-core)

## Project 2: CUDA-Tiled SGEMM

I wrote and optimized a matmul kernel taking advantage of several CUDA techniques such as thread coarsening, float4, double buffering, and loop unrolling to achieve 44,110 GFLOP/s, 79.8% of cuBLAS performance, on an RTX 4090. I used Hwu, Kirk, and Hajj's Programming Massively Parallel Processors and Boehm's How to Optimize a CUDA Matmul Kernel for reference. 

[CUDA Tiled SGEMM](https://github.com/StanleyCWestII/cuda-tiled-sgemm)

## Project 3: FlashAttention

I wrote a FlashAttention forward pass from scratch in CUDA. It tiles keys and values through shared memory, uses an online softmax, and never materializes the T x T score matrix. It matches a CPU reference on 16 sequence lengths from T = 1 to T = 512, and runs at 4,665 GFLOP/s at T = 4096 on an RTX 4090. One shared-memory read per multiply-add caps this kernel shape near 20 TFLOP/s (a static estimate), and one thread per query row is the main limiter I want to fix next.

[FlashAttention](https://github.com/StanleyCWestII/flashattention-cuda)

- [schristopherwest@gmail.com](mailto:schristopherwest@gmail.com)
- [GitHub](https://github.com/StanleyCWestII)
- [LinkedIn](https://www.linkedin.com/in/stanley-west-5759903b6)
