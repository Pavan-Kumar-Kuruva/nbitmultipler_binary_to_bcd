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

## 🏗️ Project Architecture
```text
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
             │   7-Segment      │
             │     Display      │
             └──────────────────┘

             Input B (N-bit)
                  │
                  └──────► Multiplier
```

📌 FPGA Constraint Information

The Nexys A7 50T uses an Artix-7 FPGA. The official Digilent master XDC provides the board's pin assignments for the clock, switches, LEDs, seven-segment display, and buttons.

For an 8-bit × 8-bit implementation, a typical top-level interface can be:

module top_fpga (
    input        CLK100MHZ,
    input  [15:0] SW,
    output [6:0]  SEG,
    output [7:0]  AN,
    output        DP
);
Example Nexys A7 XDC
### ⏱️ Clock Constraint

```tcl
## Clock
set_property -dict { PACKAGE_PIN E3 IOSTANDARD LVCMOS33 } [get_ports { CLK100MHZ }]
create_clock -add -name sys_clk_pin -period 10.00 -waveform {0 5} [get_ports {CLK100MHZ}]
```

### 🎚️ Switch Constraints

The 16 switches are used as inputs for the multiplier.

```tcl
## Switches

set_property -dict { PACKAGE_PIN J15 IOSTANDARD LVCMOS33 } [get_ports { SW[0] }]
set_property -dict { PACKAGE_PIN L16 IOSTANDARD LVCMOS33 } [get_ports { SW[1] }]
set_property -dict { PACKAGE_PIN M13 IOSTANDARD LVCMOS33 } [get_ports { SW[2] }]
set_property -dict { PACKAGE_PIN R15 IOSTANDARD LVCMOS33 } [get_ports { SW[3] }]
set_property -dict { PACKAGE_PIN R17 IOSTANDARD LVCMOS33 } [get_ports { SW[4] }]
set_property -dict { PACKAGE_PIN T18 IOSTANDARD LVCMOS33 } [get_ports { SW[5] }]
set_property -dict { PACKAGE_PIN U18 IOSTANDARD LVCMOS33 } [get_ports { SW[6] }]
set_property -dict { PACKAGE_PIN R13 IOSTANDARD LVCMOS33 } [get_ports { SW[7] }]

set_property -dict { PACKAGE_PIN T8 IOSTANDARD LVCMOS18 } [get_ports { SW[8] }]
set_property -dict { PACKAGE_PIN U8 IOSTANDARD LVCMOS18 } [get_ports { SW[9] }]
set_property -dict { PACKAGE_PIN R16 IOSTANDARD LVCMOS33 } [get_ports { SW[10] }]
set_property -dict { PACKAGE_PIN T13 IOSTANDARD LVCMOS33 } [get_ports { SW[11] }]
set_property -dict { PACKAGE_PIN H6 IOSTANDARD LVCMOS33 } [get_ports { SW[12] }]
set_property -dict { PACKAGE_PIN U12 IOSTANDARD LVCMOS33 } [get_ports { SW[13] }]
set_property -dict { PACKAGE_PIN U11 IOSTANDARD LVCMOS33 } [get_ports { SW[14] }]
set_property -dict { PACKAGE_PIN V10 IOSTANDARD LVCMOS33 } [get_ports { SW[15] }]
```

### 🔢 Seven-Segment Display Constraints

The seven-segment display is used to display the decimal BCD output.

```tcl
## Seven Segment

set_property -dict { PACKAGE_PIN T10 IOSTANDARD LVCMOS33 } [get_ports { SEG[0] }]
set_property -dict { PACKAGE_PIN R10 IOSTANDARD LVCMOS33 } [get_ports { SEG[1] }]
set_property -dict { PACKAGE_PIN K16 IOSTANDARD LVCMOS33 } [get_ports { SEG[2] }]
set_property -dict { PACKAGE_PIN K13 IOSTANDARD LVCMOS33 } [get_ports { SEG[3] }]
set_property -dict { PACKAGE_PIN P15 IOSTANDARD LVCMOS33 } [get_ports { SEG[4] }]
set_property -dict { PACKAGE_PIN T11 IOSTANDARD LVCMOS33 } [get_ports { SEG[5] }]
set_property -dict { PACKAGE_PIN L18 IOSTANDARD LVCMOS33 } [get_ports { SEG[6] }]
set_property -dict { PACKAGE_PIN H15 IOSTANDARD LVCMOS33 } [get_ports { DP }]
```

### 💡 Seven-Segment Anode Constraints

The anode signals select which seven-segment digit is active.

```tcl
## Seven Segment Anodes

set_property -dict { PACKAGE_PIN J17 IOSTANDARD LVCMOS33 } [get_ports { AN[0] }]
set_property -dict { PACKAGE_PIN J18 IOSTANDARD LVCMOS33 } [get_ports { AN[1] }]
set_property -dict { PACKAGE_PIN T9 IOSTANDARD LVCMOS33 } [get_ports { AN[2] }]
set_property -dict { PACKAGE_PIN J14 IOSTANDARD LVCMOS33 } [get_ports { AN[3] }]
set_property -dict { PACKAGE_PIN P14 IOSTANDARD LVCMOS33 } [get_ports { AN[4] }]
set_property -dict { PACKAGE_PIN T14 IOSTANDARD LVCMOS33 } [get_ports { AN[5] }]
set_property -dict { PACKAGE_PIN K2 IOSTANDARD LVCMOS33 } [get_ports { AN[6] }]
set_property -dict { PACKAGE_PIN U13 IOSTANDARD LVCMOS33 } [get_ports { AN[7] }]
```

These pin assignments are based on Digilent's official Nexys A7-50T Master XDC.

Important: The XDC port names must exactly match the ports in your top-level Verilog module. If your code uses names such as a, b, seg, or an instead of SW, SEG, and AN, change the [get_ports {...}] names accordingly.
                  
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


                  
