# 16-bit-carry-save-multiplier-using-semi-custom
# 🎯 Aim

To design, synthesize, implement, and analyze a 16-bit Carry-Save Multiplier (CSM) using the semi-custom VLSI design approach, including RTL coding, functional verification, synthesis, floorplanning, placement, routing, and performance evaluation.

# ⚙️ Apparatus / Tools Used

Cadence Genus – Logic Synthesis

Cadence Innovus – Physical Design (Place & Route)

Verilog HDL Code – RTL Design of Multiplier

Testbench – Functional Verification

SDC File – Timing Constraints Definition

run.tcl – Design Flow Automation Script

Standard Cell Library – Technology-Dependent (90 nm CMOS)

# 🧠 Introduction

A Carry-Save Multiplier (CSM) is a fast and hardware-efficient architecture designed to perform multiplication using parallel addition of partial products. Instead of propagating carries immediately (as in conventional adders), it saves the carries for later addition, which reduces critical path delay and speeds up computation.

In VLSI systems, the Carry-Save approach is widely used for high-speed arithmetic circuits, especially in DSPs, ALUs, and MAC units, due to its ability to handle large bit-width operations efficiently.

In this project, the 16-bit Carry-Save Multiplier:

Minimizes carry propagation delay through parallel addition

Balances trade-offs between speed, power, and silicon area

Implements a complete semi-custom ASIC flow from RTL to GDSII

# ✨ Key Highlights

⚡ High-Speed Multiplication:
Implements carry-save addition to reduce critical path delay and accelerate partial product accumulation.

🧮 Parallel Computation:
Multiple additions occur simultaneously, minimizing overall latency.

💾 Hardware Efficiency:
Reduces logic depth and power consumption compared to ripple or array multipliers.

🏗️ Semi-Custom VLSI Flow:
Covers complete flow — RTL simulation, logic synthesis, floorplanning, placement, clock tree synthesis, routing, and sign-off verification.

📐 Optimized Design Metrics:
Achieves improved trade-off between speed, area, and power through optimized standard-cell mapping.

🔍 Scalable Architecture:
Easily extendable to 32-bit or 64-bit designs for use in modern digital signal processors or arithmetic cores.
A high-speed, area-efficient hardware multiplier designed using the Carry-Save Addition (CSA) technique, implemented and synthesized using the Cadence RTL-to-GDSII semi-custom VLSI design flow.

📌 This project implements and analyzes an optimized 16-bit Carry-Save Multiplier (CSM) with synthesis reports for Area, Timing, and Power — focusing on efficient partial product reduction and minimal carry propagation delay.

🎯 Project Objective

Design and synthesize a hardware-efficient 16×16 Carry-Save Multiplier targeting ASIC/VLSI applications, focusing on:

⚡ High speed → Reduced delay by parallel partial product addition

💾 Reduced area → Optimized adder usage and compact layout

🔋 Low power → Balanced logic depth and minimized switching activity

🧩 Stable implementation → Structured architecture for efficient routing and timing closure

# 🧠 About Carry-Save Multiplication

A Carry-Save Multiplier avoids long carry propagation chains by saving intermediate carries separately at each stage and combining them later using a final carry-propagate adder (CPA).
This allows multiple additions to happen in parallel, drastically improving computation speed.

Key Features
Feature	Explanation
Input size	16×16 multiplier
Partial products	256 bits (16 rows × 16 bits)
Technique	Carry-save addition tree
Adders used	Full adders and half adders in matrix form
Final stage	Carry Propagate Adder (CPA) for 2-row sum
Benefit	Faster than array multipliers, scalable, and layout-friendly
📌 Why Carry-Save Multiplier?

✅ Eliminates long carry chains
✅ Enables parallel addition for high speed
✅ Reduces overall computation time for large bit-width operations
✅ Balanced trade-off between speed, power, and area
✅ Ideal for VLSI / ASIC / DSP / ALU applications

⚖️ Comparison with Other Multipliers
Feature	Carry-Save Multiplier	Wallace Tree	Array Multiplier	Booth Multiplier
Key Idea	Saves carry bits for later propagation	Reduces all partial products aggressively	Direct array-based summation	Encodes multiplier bits to reduce partial products
Speed	High	Very High	Low	Medium
Hardware Usage	Moderate	High	Low	Medium
Area Requirement	Medium	High	Low	Medium
Power Consumption	Moderate (balanced switching)	Higher	Low	Medium
Layout Regularity	Excellent	Complex	Regular	Moderate
Best Use Case	Speed + Power balance (ASIC/VLSI)	Pure speed priority	Simple low-power design	Signed multiplication / DSP units
# ⚙️ Semi-Custom VLSI Design Flow
Step	Description
1. RTL Design	Verilog HDL coding for 16-bit CSM
2. Simulation	Functional verification using Cadence NCSim
3. Synthesis	Logic optimization and gate mapping in Cadence Genus
4. Floorplanning	Define chip area and power grid
5. Placement	Place standard cells and optimize timing
6. CTS	Build balanced clock tree for minimal skew
7. Routing	Automatic signal and power routing
8. Sign-off	Perform STA, DRC, LVS, and IR drop checks
9. GDSII Export	Generate final layout file for fabrication
   
 # Future Scope

Extend to 32-bit and 64-bit CSM designs

Integrate into RISC-V ALU or DSP cores

Explore power optimization using clock gating

Implement with 45 nm / 28 nm libraries

Compare CSM vs Dadda / Wallace for large data paths


# ⚙️ Block Diagram
<img width="622" height="657" alt="Screenshot 2025-11-05 160404" src="https://github.com/user-attachments/assets/39d8c9f1-c415-4840-855d-2092ae85a6f3" />
# ⚙️ Carry-Save Multiplier Overview

The Carry-Save Multiplier (CSM) efficiently performs high-speed multiplication by eliminating the need to propagate carries at every addition stage. Instead, it stores the carry bits separately and adds them later using a final Carry Propagate Adder (CPA).

This technique significantly improves computation speed for larger bit-widths such as 16-bit or 32-bit, making it ideal for semi-custom VLSI implementations.

# 🧩 Key Registers and Signals
| Symbol | Description                                         |
| ------ | --------------------------------------------------- |
| A      | Multiplicand input (16 bits)                        |
| B      | Multiplier input (16 bits)                          |
| PP[i]  | Partial products generated by bitwise AND operation |
| SUM    | Sum output from CSA stage                           |
| CARRY  | Carry output from CSA stage                         |
| P      | Final Product (32 bits) after CPA addition          |

# 🔢 Functional Operation Table
| Operation Stage                | Description                                                                                                                     |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| Partial Product Generation     | AND each bit of `A` with each bit of `B` to form a matrix of partial products.                                                  |
| Carry-Save Addition (CSA Tree) | Add multiple partial products simultaneously without propagating carries. Each adder outputs a SUM and CARRY to the next stage. |
| Final Carry Propagation        | The last two rows (SUM and CARRY) are added using a standard adder (CPA) to produce the final 32-bit product.                   |
# ✅ Advantages of Carry-Save Multiplier
| Feature                    | Advantage Description                                                                                  |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| **High-Speed Computation** | Avoids carry propagation delay during intermediate additions, significantly improving speed.           |
| **Parallel Processing**    | Multiple adders operate simultaneously in the CSA tree, allowing faster reduction of partial products. |
| **Hardware Efficiency**    | Requires fewer logic levels than array multipliers, resulting in reduced propagation delay.            |
| **Scalable Architecture**  | Easily extended for 8, 16, 32, or higher bit-width multipliers without redesigning the full logic.     |
| **VLSI Friendly**          | Well-suited for semi-custom ASIC design flows (synthesis → place & route → GDS export).                |
| **Power Optimization**     | Reduced switching activity per stage improves dynamic power efficiency.                                |
# ❌ Disadvantages of Carry-Save Multiplier
| Limitation                   | Explanation                                                                                        |
| ---------------------------- | -------------------------------------------------------------------------------------------------- |
| **Area Overhead**            | Requires multiple full adders and half adders in each CSA stage, increasing transistor count.      |
| **Complex Wiring**           | Routing of sum and carry bits through multiple levels can increase layout complexity.              |
| **Final Adder Delay**        | The final CPA stage still introduces some delay for carry propagation.                             |
| **Power at High Bit Widths** | For 32-bit and higher designs, the number of partial products grows, increasing power consumption. |
| **Limited Sequential Reuse** | Purely combinational design—does not reuse hardware resources like serial multipliers do.          |
# General Comparison of Multipliers
| Multiplier Type                      | Signed Number Support  | Partial Product Count | Hardware Complexity       | Efficiency |
| ------------------------------------ | ---------------------- | --------------------- | ------------------------- | ---------- |
| Array Multiplier                     | ✖ Requires Extra Logic | ❗ High                | 🔧 High (Many Adders)     | ⭐⭐☆☆☆      |
| Carry Save Multiplier (This Project) | ✖ Not Direct           | ⚖ Medium              | 🔧 High (Multiple Stages) | ⭐⭐⭐⭐☆      |
| Booth Multiplier                     | ✅ Yes – Direct Support | ✅ Reduced             | ⚙ Moderate                | ⭐⭐⭐⭐⭐      |
# Speed, Area, and Power Analysis
| Multiplier                           | Operational Speed | Area Utilization               | Power Consumption | Target Applications          |
| ------------------------------------ | ----------------- | ------------------------------ | ----------------- | ---------------------------- |
| Array Multiplier                     | ⚡ Medium          | 🧱 High (Dense Logic)          | 🔥 High           | Small Bit-Width Designs      |
| Wallace Tree Multiplier              | ⚡⚡ Very High      | 🔩 High (Complex Interconnect) | ⚡ Medium          | High-Performance DSP/CPU     |
| Carry Save Multiplier (This Project) | ⚡⚡ High           | ✅ Low–Medium (Optimized)       | 🌱 Low            | Low-Power & VLSI ASIC Design |
# Behavioral & Algorithmic Performance
| Condition                 | Array Multiplier        | Wallace Tree Multiplier   | Carry Save Multiplier (This Project) |
| ------------------------- | ----------------------- | ------------------------- | ------------------------------------ |
| Signed Number Handling    | ❌ Needs Sign Correction | ❌ Needs Extra Logic       | ⚠ Needs Additional Logic             |
| Partial Product Reduction | 😐 Serial Addition      | ✅ Fast Parallel Reduction | ✅ Parallel Reduction (CSA Tree)      |
| Carry Propagation         | 😐 After Each Stage     | ⚡ Partial                 | ✅ Only at Final Stage                |
| Implementation Complexity | ⭐ Easy                  | 🔧 Very Complex           | ⚙ Moderate + Optimized               |
# Conclusion
The 16-bit Carry Save Multiplier (CSM) provides an excellent balance between speed, area, and power, making it ideal for ASIC and SoC applications where high-speed arithmetic operations are required.
By employing carry-save addition, it eliminates carry propagation delays during intermediate stages, allowing faster accumulation of partial products.
The design achieves high throughput with moderate hardware complexity, suitable for low-power VLSI and high-performance digital signal processing (DSP) applications.
# Working Principle
Let:

A = Multiplicand (16-bit)

B = Multiplier (16-bit)

PP[i] = Partial Product of A and B

CSA Tree = Network of Carry Save Adders

CPA = Final Carry Propagate Adder

Operation Steps:

Generate all partial products by ANDing each bit of B with all bits of A.

Feed partial products into the Carry Save Adder Tree.

Each CSA takes three inputs (A, B, C) and produces two outputs: Sum and Carry without carry propagation.

Intermediate sum and carry outputs are passed to the next stage of the CSA tree.

Finally, a Carry Propagate Adder (CPA) adds the last sum and carry vectors to generate the final 32-bit product.

This method ensures that carry signals are saved (not propagated) in intermediate stages, thus minimizing delay and maximizing speed.

# 🚀 Future Scope
1. Higher Bit-Width Extension

The present 16-bit design can be extended to 32-bit, 64-bit, or even 128-bit versions for advanced processors and cryptographic units requiring higher precision.

2. Pipelined Carry Save Multiplier

Introducing pipeline stages between CSA layers can further boost performance, enabling higher clock frequencies and increased throughput.

3. Integration into ALU / Processor Core

The CSM can be integrated into Arithmetic Logic Units (ALUs) or DSP blocks, forming part of complex computation units in embedded and SoC architectures.

4. Low-Power Optimization

By applying clock gating, operand isolation, and multi-threshold voltage (multi-Vt) techniques, the design can be optimized for ultra-low-power applications.

5. Hybrid Multiplier Architecture

Combining Carry Save Addition with Wallace Tree or Dadda Tree structures can further reduce partial product reduction delay for high-performance processors.

6. FPGA / ASIC Implementation

The design can be verified on FPGA platforms (like Xilinx/Intel) for real-time testing and later fabricated as an ASIC for commercial or research purposes.

7. Fault-Tolerant Design

In safety-critical systems (aerospace, medical), error detection and correction schemes can be added to ensure reliable multiplier operation.

8. Design Automation

Custom TCL scripting and constraint-driven optimization can automate the full synthesis-to-GDSII flow for improved productivity in large-scale VLSI projects.

# Procedure

Design Entry:
Write the RTL code for the 16-bit Carry Save Multiplier using Verilog HDL.

Functional Verification:
Simulate the design with a testbench to verify correct multiplication output for multiple test cases.

Synthesis:
Use Cadence Genus to synthesize the Verilog design, apply .sdc constraints, and generate the gate-level netlist.

Floorplanning:
Import the synthesized netlist into Cadence Innovus and perform floorplanning—define core, die area, and power rings.

Placement:
Place standard cells optimally to minimize wirelength and meet timing constraints.

Clock Tree Synthesis (CTS):
Build and balance the clock tree to ensure low skew and uniform timing distribution.

Routing:
Route the interconnections between placed cells and optimize for signal integrity and timing closure.

Physical Verification:
Perform DRC (Design Rule Check) and LVS (Layout vs. Schematic) to ensure correctness of the layout.

GDS-II Generation:
Export the final GDS-II file for fabrication or further analysis.

Performance Analysis:
Evaluate area, timing, and power metrics to ensure design meets the desired specifications.
# Write RTL code for Booth’s Multiplier in Verilog.
```// =============================================================
// 16-bit Carry-Save Multiplier (Structural CSA Design)
// =============================================================
`timescale 1ns/1ps
module csa_multiplier_16bit (
    input  [15:0] A, B,
    output [31:0] P
);

wire [15:0] pp [15:0];

// Generate Partial Products
genvar i,j;
generate
for(i=0;i<16;i=i+1) begin
    for(j=0;j<16;j=j+1) begin
        assign pp[i][j] = A[j] & B[i];
    end
end
endgenerate

// Align & Expand to 32 bit
wire [31:0] pp_ext [15:0];
generate
for(i=0;i<16;i=i+1) begin
    assign pp_ext[i] = { {16-i{1'b0}}, pp[i], {i{1'b0}} };
end
endgenerate

// CSA stages
wire [31:0] sum[14:0], carry[14:0];

CSA_32bit csa0 (pp_ext[0], pp_ext[1], pp_ext[2], sum[0], carry[0]);

generate
for(i = 1; i < 14; i=i+1) begin
    CSA_32bit csa (sum[i-1], carry[i-1]<<1, pp_ext[i+2], sum[i], carry[i]);
end
endgenerate

// Final CPA
assign P = sum[13] + (carry[13] << 1);

endmodule


// =================== 32-bit CSA block =======================
module CSA_32bit(input [31:0] x, y, z,
                 output [31:0] sum, carry);
genvar k;
generate
for(k=0;k<32;k=k+1) begin
    assign sum[k]   = x[k] ^ y[k] ^ z[k];
    assign carry[k] = (x[k] & y[k]) | (y[k] & z[k]) | (x[k] & z[k]);
end
endgenerate
endmodule
```
# Develop a testbench and perform functional simulation.
```
`timescale 1ns/1ps
module csa_multiplier_16bit_tb;

reg  [15:0] a, b;       // 16-bit inputs
wire [31:0] p;          // 32-bit product

csa_multiplier_16bit uut(.A(a), .B(b), .P(p));

initial begin
    $monitor("Time=%0t | A=%d | B=%d | P=%d", $time, a, b, p);

    a = 3;          b = 5;          #10;
    a = 1000;       b = 2000;       #10;
    a = 16'hFFFF;   b = 16'hFFFF;   #10;
    a = 12345;      b = 54321;      #10;
    a = 16'h00F0;   b = 16'h000F;   #10;

    $finish;
end

endmodule
```
# Provide timing constraints using .sdc.
```
# Create clock 'clk' with 10 ns period (100 MHz)
create_clock -name clk -period 10.0 [get_ports clk]

# Set input delay of 2 ns relative to clock 'clk'
set_input_delay -clock clk 2.0 [get_ports *]

# Set output delay of 2 ns relative to clock 'clk'
set_output_delay -clock clk 2.0 [get_ports *]

# Set clock uncertainty (jitter) of 0.1 ns for 'clk'
set_clock_uncertainty 0.1 [get_clocks clk]
```
# Run.TCL Code
```
set_db init_lib_search_path /home/install/FOUNDRY/digital/90nm/dig/lib/
set_db library slow.lib
set_db init_hdl_search_path {./csa_multiplier_16bit.v}
read_hdl csa_multiplier_16bit.v
elaborate csa_multiplier_16bit
read_sdc csa_multiplier_16bit.sdc
syn_generic
syn_map
syn_opt
write_hdl > outputs/csa_multiplier_16bit.v
write_sdf > outputs/csa_multiplier_16bit.sdf
write_sdc > outputs/csa_multiplier_16bit_syn.sdc
report_area > reports/area.rpt
report_timing > reports/timing.rpt
report_power > reports/power.rpt
gui_show
```
# Provide timing constraints using .sdc.
# Perform:
1.Floorplanning

2.Placement

3.Clock Tree Synthesis

4.Routing

5.Timing Sign-off

6.Generate layout view and performance reports.
# RTL simulation :
![WhatsApp Image 2025-11-05 at 15 48 49_518c96bc](https://github.com/user-attachments/assets/698b0b4b-21d8-4753-a42f-11f4751a1078)

![WhatsApp Image 2025-11-05 at 15 48 21_17367183](https://github.com/user-attachments/assets/cce03853-8fed-42d7-826e-c90b4a1b2b2b)

# Synthesized Gate-Level Schematic
<img width="1920" height="1080" alt="Screenshot from 2025-10-31 17-48-40" src="https://github.com/user-attachments/assets/4f893d41-7e95-44e0-8248-9b221771a667" />



# Timing Report Interpretation
![WhatsApp Image 2025-11-05 at 15 39 25_130278b9](https://github.com/user-attachments/assets/4d6bce30-5440-4798-8b15-38681673af56)
![WhatsApp Image 2025-11-05 at 15 39 25_22ad200e](https://github.com/user-attachments/assets/83014e19-a2d5-4e5c-b1dc-b8e1bb0c3c27)
![WhatsApp Image 2025-11-05 at 15 39 25_057dd1f9](https://github.com/user-attachments/assets/d0f9ee6f-f263-4726-9079-d85c1b51e331)
# Layout Results
<img width="1920" height="1080" alt="Screenshot from 2025-10-31 20-25-42" src="https://github.com/user-attachments/assets/6ee87227-2b2b-4f39-8c98-7d7e3051e38d" />
# 3D Layout View
<img width="1920" height="1080" alt="Screenshot from 2025-10-31 20-28-50" src="https://github.com/user-attachments/assets/8382b88e-7600-4843-a22b-7ebffd7b3099" />

<img width="1920" height="1080" alt="Screenshot from 2025-10-31 20-29-37" src="https://github.com/user-attachments/assets/f04e74ac-059a-48ae-8706-58a7a36cf8de" />

# Result

The 16-bit Carry Save Multiplier was successfully designed, synthesized, placed, and routed. It meets timing, power, and area constraints, making it suitable for VLSI implementation. The design efficiently performs large-bit-width multiplications with reduced propagation delay due to carry-save addition.
# Tools and Technologies
| Category                      | Tools / Technologies                              |
| ----------------------------- | ------------------------------------------------- |
| Hardware Description Language | Verilog HDL (2001 Standard)                       |
| Simulation                    | Cadence NCSim / NCLaunch                          |
| Logic Synthesis               | Cadence Genus Synthesis Solution                  |
| Place & Route                 | Cadence Innovus Implementation System             |
| Technology Node               | 90 nm CMOS Standard Cell Library                  |
| Verification                  | Functional Simulation, STA (Setup/Hold), DRC, LVS |
| Reports & Debugging           | Waveforms, Timing Reports, Area/Power Analysis    |
| GDS Export                    | Innovus Stream Out (GDSII Generation)             |
# Conclusion
The 16-bit Carry Save Multiplier (CSM) significantly reduces the critical path delay in multiplication by using carry-save adders to handle partial sums and carries simultaneously. Through a semi-custom VLSI design flow, the multiplier was converted from Verilog RTL to final layout, demonstrating the complete IC design cycle and performance validation. This project highlights how hardware-level parallelism and efficient adder architectures improve speed, area, and power consumption for large-bit-width multipliers.

# Course Information

Course: VLSI System Design Practice (EC-307)

Faculty: Dr. P. Ranga Babu

Department: Electronics and Communication Engineering

Institution: Indian Institute of Information Technology Design and Manufacturing, Kurnool

Academic Year: 2025-2026 (Semester-5)

# Research References

“Implementation of 16‑Bit Vedic Multiplier Using Modified CSA” by B. Vanitha, S. Nagaraj & B. Sai Kumar (2023) — This paper describes a 16 × 16 Vedic multiplier using CSA and modified CSA architectures. 
Atlantis Press

  Link: PDF

Parhami, B., "Computer Arithmetic: Algorithms and Hardware Designs", Oxford University Press, 2010

Huang & Ercegovac, "High-Performance Multipliers", IEEE, 1988

Comparison of Multipliers for VLSI Application
Link

Acknowledgments

This project was completed with support and guidance from:

Dr. P. Ranga Babu — Course Instructor & Project Guide, Dept. of ECE, IIITDM Kurnool

IIITDM Kurnool — For providing computational resources and infrastructure

Cadence Design Systems — For access to industry-standard EDA tools

Open-Source Community — For educational resources and documentation

Research Community — For foundational work in processor and VLSI architectures













