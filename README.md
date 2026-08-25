Design and Implementation of N-bit Multiplier with Binary-to-BCD Conversion using Verilog HDL on Nexys A7 FPGA
📌 Project Overview

This project presents the design and FPGA implementation of an N-bit binary multiplier with Binary-to-BCD conversion using Verilog HDL.

The multiplier performs binary multiplication of two N-bit input values. The resulting binary product is then converted into Binary-Coded Decimal (BCD) format so that the decimal result can be displayed on the 7-segment display of the Nexys A7 FPGA board.

The complete design was developed, simulated, synthesized, implemented, and tested using Xilinx Vivado and the Digilent Nexys A7 FPGA board.

🎯 Project Objectives
Design an N-bit binary multiplier using Verilog HDL.
Generate the binary multiplication result.
Convert the binary result into decimal digits using Binary-to-BCD conversion.
Implement the Double Dabble (Shift-and-Add-3) algorithm for BCD conversion.
Display the decimal result on the Nexys A7 7-segment display.
Verify the design through simulation and waveform analysis.
Implement and test the design on real FPGA hardware.
🏗️ Project Architecture
             ┌──────────────────┐
             │   Input A (N-bit)│
             └────────┬─────────┘
                      │
                      ▼
             ┌──────────────────┐
             │                  │
             │   N-bit          │
             │   Multiplier     │
             │                  │
             └────────┬─────────┘
                      │
                      │ Binary Product
                      ▼
             ┌──────────────────┐
             │  Binary-to-BCD   │
             │    Converter     │
             │  Double Dabble   │
             └────────┬─────────┘
                      │
                      │ BCD Digits
                      ▼
             ┌──────────────────┐
             │  7-Segment       │
             │    Display       │
             └──────────────────┘

             Input B (N-bit)
                  │
                  └──────► Multiplier
🧪 Simulation and Verification

The design was verified using a Verilog testbench in Xilinx Vivado.

Important test cases include:

Input A	Input B	Decimal Product
5	5	25
10	10	100
12	25	300
25	12	300

The simulation waveform can be included in the repository to demonstrate correct multiplication and Binary-to-BCD conversion.

🔌 Nexys A7 FPGA Implementation

The design was implemented on the Digilent Nexys A7 FPGA board.

Input

For an 8-bit × 8-bit implementation:

SW[7:0]   → Input A
SW[15:8]  → Input B
Output

The multiplication result is converted to BCD and displayed using the Nexys A7 seven-segment display.

The Nexys A7 provides 16 user switches and an eight-digit seven-segment display, making it suitable for demonstrating this project.

📷 Hardware Implementation

The design was programmed onto the Nexys A7 FPGA and tested using the physical switches and seven-segment display.

FPGA Hardware Output:<img width="720" height="1599" alt="WhatsApp Image 2026-08-25 at 11 02 44 PM" src="https://github.com/user-attachments/assets/4319f7f3-6c2d-4b89-9f28-e67d94926725" />


                  
