# README

This repository contains multiple small CPUs, simulated in Logisim.

## Models

### cpu8_v1

Extremely simple 8-bit CPU with 6 arithmetic (ADD, SUB) and logical (AND, OR, NAND, NOR) operations, conditional jumps are also supported.

The CPU has 6 Registers:
- 1x Constant loading
- 2x ALU operand
- 1x ALU result
- 2x General purpose

The program is read from a readonly memory (ROM).

## Programming

In [this repository](https://gitlab.com/ChUrl/logisim-assembler) I implemented a simple assembler, to make programming the CPUs easier.
The assembler versions (branches) match with the CPU names.
