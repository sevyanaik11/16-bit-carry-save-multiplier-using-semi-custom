# 16-bit-carry-save-multiplier-using-semi-custom
A high-speed, area-efficient hardware multiplier designed using the Carry-Save Addition (CSA) technique, implemented and synthesized using the Cadence RTL-to-GDSII semi-custom VLSI design flow.

📌 This project implements and analyzes an optimized 16-bit Carry-Save Multiplier (CSM) with synthesis reports for Area, Timing, and Power — focusing on efficient partial product reduction and minimal carry propagation delay.

🎯 Project Objective

Design and synthesize a hardware-efficient 16×16 Carry-Save Multiplier targeting ASIC/VLSI applications, focusing on:

⚡ High speed → Reduced delay by parallel partial product addition

💾 Reduced area → Optimized adder usage and compact layout

🔋 Low power → Balanced logic depth and minimized switching activity

🧩 Stable implementation → Structured architecture for efficient routing and timing closure

🧠 About Carry-Save Multiplication

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
⚙️ Semi-Custom VLSI Design Flow
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
🧩 Performance Analysis (Typical 90nm Technology)
Parameter	Pre-Layout	Post-Layout	Unit
Technology Node	90 nm	90 nm	—
Area	18,900	19,400	μm²
Power	7.8	8.2	mW
Delay	5.5	5.9	ns
Frequency	180	170	MHz
Cell Count	1400	1472	—
🔬 Simulation & Verification

RTL-level simulation validated multiplication correctness.

Waveforms confirmed carry-save behavior (no carry rippling).

Post-layout verification achieved zero setup and hold violations.

DRC and LVS checks clean (Calibre / Innovus Signoff).

🧰 Tools and Environment
Category	Tool Used
HDL Language	Verilog HDL
Simulation	Cadence NCSim
Synthesis	Cadence Genus
Floorplanning & Routing	Cadence Innovus
Sign-off	STA, DRC, LVS, IR Drop
Technology	90 nm CMOS Library
Final Output	GDSII Layout
