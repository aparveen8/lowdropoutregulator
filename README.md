# Low Dropout Regulator Design for Efficient Power Management in Battery-Powered Systems

This design presents a dual-mode LDO for battery-powered systems, implemented using SKY130 PDK with open source tool, esim. This dual-mode LDO addresses the requirements for blocks needing programmable outputs, 1.2V (low-power core logic) and 2.4V (IO interfaces blocks), offering flexibility in delivering optimized voltage for different functional requirements within the SoC. This adaptability allows for efficient power distribution, minimizes noise in sensitive blocks, and supports stable operation across varying supply.

## Table of Contents
- [Block Diagram](#block-diagram)
- [Dual Mode Design Parameters](#dual-mode-design-parameters)
- [Circuit Schematic](#circuit-schematic)
- [Software Used](#software-used)
- [Simulation Results](#simulation-results)
  - [PSRR Analysis](#psrr-analysis)
  - [Load and Line Regulation](#load-and-line-regulation)
- [Netlists](#netlists)
- [Steps to Run NgVeri Model](#steps-to-run-ngveri-model)
- [Steps to Run this Project](#steps-to-run-this-project)
- [References](#references)
- [Acknowledgments](#acknowledgments)
- [Author](#author)

---


## A Glance at block diagram of LDO
Below is a simplified block diagram of the LDO circuit, showing the key components:
<p align="center">
  <img src="images/dual_mode_LDO_block_diagram.png" alt="LDO Block Diagram"/>
</p>

---

## Dual Mode Design Parameters

| Parameter        | Design I       | Design II     | Units |
|------------------|----------------|---------------|-------|
| V<sub>Supply</sub>     | 1.8V           | 1.2V          | V     |
| V<sub>OUT</sub>        | 1.5V           | 1.1V          | V     |
| V<sub>REF</sub>        | 1.2V           | 1.0V          | V     |
| R1               | 10kΩ           | 4kΩ           | Ω     |
| R2               | 40kΩ           | 40kΩ          | Ω     |
| W<sub>M1</sub>         | 2.5mm          | 2.5mm         | mm    |
| C<sub>LOAD</sub>       | 10pF           | 10pF          | pF    |
| I<sub>LOAD</sub>       | 0 - 24mA       | 0 - 24mA      | mA    |

---

## Circuit Schematic
The following schematic illustrates the dual-mode LDO circuit, supporting both 1.2V and 1.8V supply configurations.
<p align="center">
  <img src="images/dual_mode_LDO_schematic.png" alt="Dual Mode LDO Schematic"/>
</p>

---

## Software Used
- **eSim**: Open-source EDA tool by FOSSEE, IIT Bombay, combining NgSpice and KiCAD.
- **NgSpice**: For SPICE simulations of analog and mixed-signal designs.
- **Makerchip**: Web IDE for Verilog/SystemVerilog simulations.
- **Verilator**: Verilog-to-C++ converter for high-performance simulation.

---

## Simulation Results

### PSRR Analysis
The Power Supply Rejection Ratio (PSRR) of this LDO is measured at -29.8 dB at 100 kHz, effectively filtering power supply noise to protect sensitive analog blocks.

### Load and Line Regulation
- **Load Regulation**: 0.34 µV/mA across a 0-24mA load, ensuring output stability under changing loads.
- **Line Regulation**: Maintains stable output voltage with a line regulation of 0.3 mV/V.

---

## Netlists
- [LDO Circuit Netlist](LDO/LDO.cir.out)
- [Error Amplifier Netlist](LDO/Error_Amp.cir.out)
- [Pass Transistor Netlist](LDO/Pass_Transistor.cir.out)

---

## Steps to Run NgVeri Model
1. Open eSim.
2. Run NgVeri-Makerchip.
3. Add the top-level Verilog file in Makerchip.
4. Go to the NgVeri tab.
5. Add dependency files.
6. Run the Verilog to NgSpice converter.
7. Debug any errors for successful model creation.

---

## Steps to Run this Project
1. Clone this repository:
   ```bash
   git clone https://github.com/aparveen8/LDO_design.git
