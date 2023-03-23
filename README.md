# README

This repository contains multiple small CPUs, simulated in Logisim.
**I abandoned this in favor of [this](https://gitlab.com/ChUrl/quartus-8-bit-cpu).**

## Models

### cpu8_v1

Extremely simple 8-bit CPU with 6 arithmetic (ADD, SUB) and logical (AND, OR, NAND, NOR) operations, conditional jumps are also supported.

The CPU has 6 Registers:
- 1x Constant loading
- 2x ALU operand
- 1x ALU result
- 2x General purpose

The program is read from a readonly memory (ROM).

#### Instruction Reference:

The Instruction/Data share 8-bit, the instruction mode is specified by bits 6 and 7, so there is a total of 4 modes:

| Bit | Value  | Description           |
|-----|--------|-----------------------|
| 6:7 | 00     | Constant loading mode |
| 0:5 | xxxxxx | Number value          |

| Bit | Value                                  | Description                            |
|-----|----------------------------------------|----------------------------------------|
| 6:7 | 01                                     | ALU mode                               |
| 3:5 | 000                                    | Reserved                               |
| 0:2 | 000<br>001<br>010<br>011<br>100<br>101 | And<br>Or<br>Nand<br>Nor<br>Add<br>Sub |

| Bit | Value | Description               |
|-----|-------|---------------------------|
| 6:7 | 10    | Copy mode                 |
| 3:5 | xxx   | Source register or input  |
| 0:2 | xxx   | Target register or output |

| Bit | Value                                                | Description                                                     |
|-----|------------------------------------------------------|-----------------------------------------------------------------|
| 6:7 | 11                                                   | Jump mode                                                       |
| 3:5 | 000                                                  | Reserved                                                        |
| 0:2 | 000<br>001<br>010<br>011<br>100<br>101<br>110<br>111 | Never<br>== 0<br><  0<br><= 0<br>Always<br>!= 0<br>>  0<br>>= 0 |

## Programming

In [this repository](https://gitlab.com/ChUrl/logisim-assembler) I implemented a simple assembler, to make programming the CPUs easier.
The assembler versions (branches) match with the CPU names.
