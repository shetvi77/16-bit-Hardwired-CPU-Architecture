# 16-bit-Hardwired-CPU-Architecture
Design of a 16-bit Hardwired CPU Architecture using Logisim 


This repository contains the design and simulation files for a **16-bit basic CPU** implemented using **Logisim Evolution**. The processor is based on the basic computer architecture described in *Computer System Architecture* by **M. Morris Mano**.

## Project Overview

This project demonstrates the design and simulation of a 16-bit hardwired CPU capable of executing basic memory-reference and register-reference instructions.

The processor follows the complete:

**Fetch → Decode → Execute**

instruction cycle using clock-driven timing signals and combinational control logic.

The architecture includes:

- A 16-bit Arithmetic Logic Unit
- Hardwired control unit
- Instruction decoder
- Sequence counter and timing generator
- Processor registers
- 16-bit common data bus
- Main memory
- Clock-based instruction sequencing

The project focuses on understanding fundamental processor architecture and control-unit design. Advanced concepts such as pipelining, interrupts, cache memory, and complex I/O systems are not implemented.

## Objectives

- Design a complete 16-bit processor datapath
- Implement the fetch-decode-execute instruction cycle
- Generate timing signals using a sequence counter
- Decode instructions using combinational logic
- Generate control signals for register and ALU operations
- Implement memory-reference and register-reference instructions
- Validate CPU operation through simulation in Logisim Evolution
- Understand the interaction between datapath and control-unit components

## System Architecture

The CPU consists of the following major components:

### Registers

- **AR – Address Register**
- **PC – Program Counter**
- **DR – Data Register**
- **AC – Accumulator**
- **IR – Instruction Register**
- **TR – Temporary Register**
- **SC – Sequence Counter**

Each register is connected to the common data bus and controlled through timing and instruction-decoding signals.

### Arithmetic Logic Unit

The 16-bit ALU performs arithmetic and logical operations such as:

- Addition
- AND operation
- Complement
- Increment
- Data transfer
- Accumulator operations

The result of the selected operation is stored in the accumulator or another destination register depending on the instruction.

### Control Unit

The processor uses a **hardwired control unit**.

The control unit generates control signals based on:

- Instruction opcode
- Indirect-addressing bit
- Timing signals
- Register conditions
- ALU status

These signals control register loading, incrementing, clearing, memory access, bus selection, and ALU operation.

### Instruction Decoder

A **3-to-8 decoder** decodes the three-bit opcode field and generates instruction-selection signals.

The decoded instruction and timing signals are combined to perform the required sequence of micro-operations.

### Sequence Counter and Timing Signals

The sequence counter generates timing steps used to control the instruction cycle.

Typical timing signals include:

- `T0`
- `T1`
- `T2`
- `T3`
- Subsequent execution timing states

At the end of instruction execution, the sequence counter is cleared so that the next instruction begins from `T0`.

### Common Data Bus

A 16-bit common bus connects the processor registers, memory, and ALU.

The control unit selects which register places data on the bus and which destination register receives the data.

### Memory

The system uses:

- **4096 × 16-bit memory**
- 12-bit memory addressing
- Separate memory read and write control signals

Memory stores both instructions and data.

## 🧾 Instruction Format

The 16-bit instruction format contains:

- **1 indirect-addressing bit**
- **3-bit opcode**
- **12-bit address or control field**

```text
-------------------------------------------------
| I | Opcode |        Address / Function        |
-------------------------------------------------
  1     3                 12 bits
