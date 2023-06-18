<div width="100%" height="100%" align="center">
  
<h1 align="center">
  <p align="center">Computer Organization and Design RISC-V Edition</p>
  <a href="https://www.elsevier.com/books/computer-organization-and-design-risc-v-edition/patterson/978-0-12-812275-4">
    <img width="50%" src="cover.jpg" />
  </a>
</h1>
  
<b>David Patterson, John Hennessy 저</b></br>
Elsevier · 2017년 4월 13일 출시</b> 

</div>

## :bulb: 목표

- **컴퓨터 구조를 공부한다.**

  > RISC-V 컴퓨터 하드웨어, 소프트웨어 인터페이스를 자세히 공부한다.

<br/>

## 🚩 정리한 문서 목록

### 📔 Computer Abstractions

 - [Computer Abstractions and Technology](https://github.com/erectbranch/Computer_Organization_and_Design/tree/master/ch01)

   > response time(execution time): wall clock time(elapsed time), CPU time, clock rate, clock period, CPI(Clock cycles Per Instruction), Effective CPI, MIPS

   > Power Wall, multicore processor, parallel programming, Amdahl's Law

### ⚙️ RISC-V

 - [RISC-V Instructions(RV64I)](https://github.com/erectbranch/Computer_Organization_and_Design/tree/master/ch02/summary01)

   > CISC vs RISC, general purpose register(register file), register operands, data alignment(MIPS vs RISC-V), byte addressing, little/big Endian, register spilling, bit extension

   > R-format instructions(arithmetic), I-format instructions(load, immediate arithmetic), S-format instructions(stores)

   > addressing mode(immediate, register, base, PC-relative), logical operations(shift, and, or, xor)

 - [Conditional Operation, Branch](https://github.com/erectbranch/Computer_Organization_and_Design/tree/master/ch02/summary02)

   > branch instructions(if-else, while example), procedure calling, procedure call instructions, memory layout, stack, leaf procedure, non-leaf procedure(factorial example), string copy example

 - [wide, branch instructions, data race](https://github.com/erectbranch/Computer_Organization_and_Design/tree/master/ch02/summary03)

   > wide immediate operands, branch addressing, SB-format, branching far away

   > data race, synchronization, atomic swap, mutex lock

### 🎛 RISC-V Processor

 - [RISC-V Processor datapath](https://github.com/erectbranch/Computer_Organization_and_Design/tree/master/ch04/summary01)

   > instruction execution: IF(Instruction Fetch), ID(Instruction Decode/register file read), EX(Execute/address calculation), MEM(Memory access), WB(Write Back)

   > combinational element, state element, sequential elements, multiplexer, control unit(function unit, control line)

 - [RISC-V Pipelining](https://github.com/erectbranch/Computer_Organization_and_Design/tree/master/ch04/summary02)

   > single-cycle vs pipelined performance, pipeline bubble, steady state

   > pipeline hazard: structural hazard, data hazard(forwarding, code scheduling), control hazard(static/dynamic branch prediction)

### 🪜 Cache

- [memory hierarchy, direct mapped cache](https://github.com/erectbranch/Computer_Organization_and_Design/tree/master/ch05/summary01)

   > SRAM, DRAM, temporary locality, spatial locality

   > hit ratio, miss ratio, direct mapped cache(tag, valid bit, address subdivision), block size considerations

- [cache miss, cache write, set-associative cache](https://github.com/erectbranch/Computer_Organization_and_Design/tree/master/ch05/summary02)

   > cache miss(compulsory/capacity/conflict misses), cache write(write-through, write buffer, write-back, write allocation)

   > N-way set-associative cache(miss rate and associativity), fully-associative cache, replacement policy(LRU, random)

   > split cache(instruction cache, data cache), cache performance(memory-stall clock cycles, AMAT), multilevel caches(primary cache, secondary cache)

<br/>

## :mag: 목차

### 1. Computer Abstractions and Technology

### 2. Instructions: Language of the Computer

### 3. Arithmetic for Computers

### 4. The RISC-V Processor

### 5. Large and Fast: Exploiting Memory Hierarchy

### 6. Parallel Processors from Client to Cloud

### A. The Basics of Logic Design

### B. Graphics and Computing GPUs

### C. Mapping Control to Hardware

### D. A Survey of RISC Architectures