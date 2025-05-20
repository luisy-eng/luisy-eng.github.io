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

**Program Counter Logic:**

<p align="center">
    <img width="300px" src="../img/IF.png" class="img-thumbnail">
</p>
This section of the code implements the **Program Counter (PC)** logic for the **Instruction Fetch (IF)** stage in the pipelined CPU. The PC is responsible for tracking the address of the next instruction to be fetched from memory. It is updated on each clock cycle and plays a critical role in managing the flow of the program.

There are several key components to the **Program Counter Logic**, which are expanded in later stages of the project. However, in this stage, we focus on two main features:

- **Reset Handling:**

  - If the **reset** signal is high, the PC is reset to **0**, restarting the program from the beginning.

- **Branch Handling:**
  - The PC can be updated based on branch instructions, including **B** (Unconditional Branch) and **CBZ** (Compare and Branch if Zero). This allows the CPU to change the execution flow based on the results of prior instructions.

This foundational logic sets the stage for more complex control flow in later stages, including support for subroutine calls and conditional branching.

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

**Controller:**

- Implements a `cpuControl` structure to manage control signals for various components.
- Decodes instruction opcodes to determine control signals.

<img width="300px" src = "../img/controller.png" class="img-thumbnail" img>

#### Instruction Set:

The project supports a set of instructions, including additions, subtractions, branches, loads, and stores. Each instruction is associated with specific control signals that guide the processor's behavior.

#### Overall Objective:

This project aims to demonstrate a basic processor design in Verilog, emphasizing the integration of critical components and effective control signal management for executing instructions.
