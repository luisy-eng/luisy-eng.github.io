---
layout: project
type: project
image: img/Cpu.png
title: "Pipelined Processor Desing"
date: 2023-10-05
published: True
labels:
  - Computer Engineering
  - Computer Architecture
  - System Verilog
summary: "This project implements a Reduced Instruction Set Computer (RISC) CPU with a 5-stage pipeline, designed in SystemVerilo."
---

<p align="center">
    <img src="https://www.researchgate.net/profile/Tadi-Chandrasekhar/publication/372100694/figure/fig3/AS:11431281172248033@1688478707679/Pipelined-MIPS-Architecture.ppm" alt="Pipelined MIPS Architecture" width="500">
</p>

<p align="center" style="font-size: 12px;">
    Image credit: <a href="https://www.researchgate.net/profile/Tadi-Chandrasekhar/publication/372100694/figure/fig3/AS:11431281172248033@1688478707679/Pipelined-MIPS-Architecture.ppm" target="_blank">Pipelined MIPS Architecture by Tadi Chandrasekhar</a>
</p>

### Simple Processor Design in Verilog

This project's goal is to implement and design a 5-stage pipelined CPU in Verilog. The project is divided into three stages, each building on the previous one to add more complex instruction sets and control logic.

**Stage 0:**  
Lays the foundation by implementing the logic for each pipeline stage, including instruction fetch (IF), instruction decode (ID), execute (EX), memory access (MEM), and write-back (WB). It also includes a basic controller that supports simple instructions like **ADDI** (Add Immediate) and **B** (Unconditional Branch).  
[View Stage 0 on EDA Playground](https://www.edaplayground.com/x/dNZ4)

**Stage 1:**  
Expands the instruction set to include **ADD** (Add), **SUBI** (Subtract Immediate), and **CBZ** (Compare and Branch if Zero), introducing more complex branching logic and enhanced control signal management.  
[View Stage 1 on EDA Playground](https://www.edaplayground.com/x/aijZ)

**Stage 2:**  
Further refines the design with support for **BL** (Branch and Link) and **BR** (Branch to Register), adding subroutine capabilities and more flexible control flow.  
[View Stage 2 on EDA Playground](https://www.edaplayground.com/x/9cb8)

Each stage includes a testbench for verifying functionality and performance, ensuring the processor can handle a wide range of instruction types while maintaining efficient pipeline flow.

#### Key Components:

**Register File:**

- Maintains a set of registers (`regFile`) for data storage.
- Utilizes read and write operations based on control signals.

<img width="300px" src = "../img/register-file.png" class="img-thumbnail" img>

**Data Memory:**

- Utilizes a data memory array (`DMem`) for storing and retrieving data.
- Supports memory write operations based on control signals.

<img width="300px" src = "../img/data-memory.png" class="img-thumbnail" img>

**ALU (Arithmetic Logic Unit):**

- Performs arithmetic and logic operations based on control signals.
- Outputs results to `aluResult` and evaluates a zero condition (`Zero`).

<img width="300px" src = "../img/alu.png" class="img-thumbnail" img>

**Program Counter Logic:**

- Manages the program counter (`pc`) based on control signals.
- Implements branching and program counter updates according to instruction types.

<img width="300px" src = "../img/pc.png" class="img-thumbnail" img>

**Controller:**

- Implements a `cpuControl` structure to manage control signals for various components.
- Decodes instruction opcodes to determine control signals.

<img width="300px" src = "../img/controller.png" class="img-thumbnail" img>

#### Instruction Set:

The project supports a set of instructions, including additions, subtractions, branches, loads, and stores. Each instruction is associated with specific control signals that guide the processor's behavior.

#### Overall Objective:

This project aims to demonstrate a basic processor design in Verilog, emphasizing the integration of critical components and effective control signal management for executing instructions.
