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

# RTL simulation :
![WhatsApp Image 2025-11-05 at 15 48 49_518c96bc](https://github.com/user-attachments/assets/698b0b4b-21d8-4753-a42f-11f4751a1078)


![WhatsApp Image 2025-11-05 at 15 48 21_17367183](https://github.com/user-attachments/assets/cce03853-8fed-42d7-826e-c90b4a1b2b2b)


# ⚙️ Block Diagram
<img width="622" height="657" alt="Screenshot 2025-11-05 160404" src="https://github.com/user-attachments/assets/39d8c9f1-c415-4840-855d-2092ae85a6f3" />
# ⚙️ Carry-Save Multiplier Overview

The Carry-Save Multiplier (CSM) efficiently performs high-speed multiplication by eliminating the need to propagate carries at every addition stage. Instead, it stores the carry bits separately and adds them later using a final Carry Propagate Adder (CPA).

This technique significantly improves computation speed for larger bit-widths such as 16-bit or 32-bit, making it ideal for semi-custom VLSI implementations.

# 🧩 Key Registers and Signals
Symbol	Description
A	Multiplicand input (16 bits)
B	Multiplier input (16 bits)
PP[i]	Partial products generated by bitwise AND operation
SUM	Sum output from CSA stage
CARRY	Carry output from CSA stage
P	Final Product (32 bits) after CPA addition






