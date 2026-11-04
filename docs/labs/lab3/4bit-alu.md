# 4-Bit ALU: RTL Design to Physical Implementation

## Overview

In this project, you will design and implement a 4-bit Arithmetic Logic Unit (ALU) using Verilog, Yosys, OpenLane, and the SKY130 Process Design Kit (PDK).

An ALU is a digital circuit that performs arithmetic and logical operations based on a control signal (opcode).

This is an **optional advanced project** intended for students with prior experience in circuit design, digital logic design or Verilog/VHDL.

The goal is to complete the RTL-to-GDSII design flow, from hardware description and verification to physical implementation.

---

## ALU Design Specifications

Design a 4-bit ALU with the following inputs and outputs:

| Signal | Width | Description |
|---|---|---|
| `A` | 4 bits | First operand |
| `B` | 4 bits | Second operand |
| `opcode` | 3 bits | Operation selector |
| `result` | 4 bits | ALU output |

### Supported Operations

The ALU should support eight operations selected by a 3-bit opcode.

For the examples below, assume `A = 0101` (5) and `B = 0011` (3).

| Opcode | Operation | Example Result |
|---|---|---|
| `000` | ADD | `1000` (8) |
| `001` | SUB | `0010` (2) |
| `010` | AND | `0001` (1) |
| `011` | OR | `0111` (7) |
| `100` | XOR | `0110` (6) |
| `101` | NOT A | `1010` (10) |
| `110` | Shift Left A | `1010` (10) |
| `111` | Shift Right A | `0010` (2) |

### Important Design Considerations

- **ADD and SUB:** Use a shared 4-bit ripple-carry adder with two's complement for subtraction.
- **AND, OR, XOR, NOT:** Implement using bitwise logic operations.
- **Shift Left and Right:** Perform fixed one-bit logical shifts, filling empty positions with zeros.
- **Opcode:** The 3-bit control signal selects one of the eight operations.
- **Output:** The result is limited to 4 bits. Carry-out or overflow beyond four bits can be discarded.

---

## Part 1: RTL Design and Verification

### Step 1: Define the ALU Architecture

Before writing Verilog/VHDL:

1. Identify the arithmetic and logic operations.
2. Define the inputs, outputs, and control signals.
3. Develop a block diagram showing how the arithmetic and logic units connect.

### Step 2: Implement the ALU in Verilog/VHDL

1. Design a 1-bit full adder.
2. Connect four full adders to create a 4-bit ripple-carry adder.
3. Implement arithmetic and logic operations.
4. Integrate all components into a top-level ALU module.

### Step 3: Develop a Testbench

1. Create a Verilog testbench.
2. Test all eight operations.
3. Verify the outputs for different combinations of A and B.
4. Display print messages for each test.

### Step 4: Synthesize the Design

1. Verify and debug your RTL.
2. Use Yosys to perform logic synthesis.
3. Review the synthesized netlist and cell statistics.

---

## Part 2: Physical Implementation

### Step 5: Configure OpenLane

1. Set up the OpenLane environment with the SKY130 PDK.
2. Prepare the ALU RTL files and design configuration.
3. Define the required timing constraints.

### Step 6: Run the Physical Design Flow

Using OpenLane, perform:

1. Logic synthesis
2. Floorplanning
3. Placement
4. Routing
5. Design Rule Checking (DRC)
6. Layout Versus Schematic (LVS) 

NOTE: This ALU is a combinational circuit, so clock tree synthesis is not required unless registers are added.

## Additional Challenge

Explore how changing the adder architecture, such as replacing the ripple-carry adder with a carry-lookahead adder, affects the ALU's area and timing.

