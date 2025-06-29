# 32-bit Single-Cycle MIPS CPU (Verilog)

A practical implementation of a 32-bit single-cycle MIPS processor, crafted in Verilog HDL. This project demonstrates the essentials of CPU architecture, including datapath construction and control logic, as part of a computer architecture curriculum.

## Overview

- **Architecture:** 32-bit MIPS (subset of ISA)
- **Execution Model:** Single-cycle per instruction
- **Design:** Modular (ALU, Control, Register File, Memory, etc.)
- **Verification:** Comprehensive testbench included

## Contents

- [Highlights](#highlights)
- [Block Diagram & Modules](#block-diagram--modules)
- [Directory Layout](#directory-layout)
- [How to Run](#how-to-run)
- [Supported MIPS Instructions](#supported-mips-instructions)
- [Documentation](#documentation)

## Highlights

- **Full 32-bit Data Path:** Handles all data and addresses as 32 bits.
- **Single-Cycle Execution:** Each instruction completes in one clock cycle.
- **Component-Based:** Major processor functions are separated into reusable modules.
- **Testbench Provided:** Functional simulation via `mips_processor_tb.v`.

## Block Diagram & Modules

The processor is built from the following main building blocks:

| Component             | Source File              | Functionality                                           |
|-----------------------|--------------------------|--------------------------------------------------------|
| Processor Top         | `mips_processor.v`       | Integrates all modules into a working CPU              |
| Control Logic         | `control_unit.v`         | Decodes opcodes, generates control signals             |
| Arithmetic Logic Unit | `alu.v`                  | Executes arithmetic and logical operations             |
| ALU Decoder           | `alu_control.v`          | Interprets funct field for ALU operation selection     |
| Register File         | `register_file.v`        | 32 registers (`$0`–`$31`) for general-purpose storage  |
| Instruction Memory    | `instruction_memory.v`   | Stores the program instructions                        |
| Data Memory           | `data_memory.v`          | Memory for load/store operations                       |
| Program Counter       | `pc.v`                   | Holds the address of the current instruction           |
| Sign Extender         | `sign_extend.v`          | Converts 16-bit immediates to 32 bits                  |
| Multiplexer           | `mux2.v`                 | Input selection throughout the datapath                |

*For a visual schematic, refer to the project documentation.*

## Directory Layout

```
project-root/
│
├── .gitignore
├── README.md
├── code/
│ ├── alu.v
│ ├── alu_control.v
│ ├── control_unit.v
│ ├── data_memory.v
│ ├── instruction_memory.v
│ ├── mips_processor.v
│ ├── mux2.v
│ ├── pc.v
│ ├── register_file.v
│ └── sign_extend.v
└── testbench/
└── mips_processor_tb.v
├── Project Report.pdf
```
- **code/**: Synthesizable Verilog modules (main CPU logic)
- **testbench/**: Testbenches and simulation files

## How to Run

### Prerequisites

- Any Verilog simulator (e.g., Icarus Verilog, ModelSim, Vivado)
- Waveform viewer (e.g., GTKWave)

### Steps

1. **Clone the repository:**
    ```
    git clone <your-repo-url>
    cd <project-root>
    ```

2. **Compile the design and testbench:**
    ```
    iverilog -o mips_sim sim/mips_processor_tb.v rtl/*.v
    ```

3. **Simulate:**
    ```
    vvp mips_sim
    ```

4. **View simulation results:**
    ```
    gtkwave mips_processor_tb.vcd
    ```

*Note: You may need to initialize the instruction memory with your own test program.*

## Supported MIPS Instructions

| Type   | Instructions                        |
|--------|-------------------------------------|
| R-Type | `add`, `sub`, `and`, `or`, `slt`   |
| I-Type | `lw`, `sw`, `beq`                  |
| J-Type | `j`                                 |

*Additional instructions can be added by extending the control logic and datapath.*

## Documentation

A comprehensive report is available in the repository, covering:

- Datapath diagrams and architectural details
- Module-wise implementation notes
- Simulation methodology and results



