---
layout: default
---
My name is Stanley Christopher West II, and I have spent the past few months in deep self-study of digital design and GPU engineering.

## Project 1: RISC-V Core

I created a 5-stage pipelined RV32I subset processor core with a UART Echo and VGA Pattern Generator expansion, along with 2-bit branch prediction and a D-cache memory hierarchy. I used Harris and Harris' Digital Design and Computer Architecture: RISC-V Edition for reference. 

While I wrote every line of the processor, I used AI to help benchmark and test it. The build passes 65/65 checks against I-type, R-type, B-type, S-type, and J-type instructions, and overcomes pipelining hazards with the use of forwarding, stalling, and flushing. 

Running on a 132-instruction loop benchmark, the 2-bit branch predictor brought cycles from 195 to 139, a 29% reduction, and mispredicts from 30 to 2. 

My D-cache, implemented as 8 sets, 2 ways, 4 words, write-through, no write-allocate, LRU, and behind a 15-cycle main memory brought a 2.12-6.17x speedup in cycles. Most importantly to note, the processor's memory is too small to test directly. The 15-cycle latency is arbitrary in order to test the D-cache against realistic circumstances. 

[RISC-V Core](https://github.com/StanleyCWestII/riscv-pipelined-core)

## Project 2: CUDA-Tiled SGEMM

I wrote and optimized a matmul kernel taking advantage of several CUDA techniques such as thread coarsening, float4, double buffering, and loop unrolling to achieve 81% of cuBLAS performance. I used Hwu, Kirk, and Hajj's Programming Massively Parallel Processors and Boehm's How to Optimize a CUDA Matmul Kernel for reference. 

[schristopherwest@gmail.com](mailto:schristopherwest@gmail.com)
---
[GitHub](https://github.com/StanleyCWestII)
---
[LinkedIn](https://www.linkedin.com/in/stanley-west-5759903b6)
---
