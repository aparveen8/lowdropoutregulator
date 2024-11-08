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


## A Glance at block diagram of Proposed LDO
Below is a simplified block diagram of the LDO circuit, showing the key components:
<p align="center">
  <img src="block4.png" alt="LDO Block Diagram"/>
</p>

---

## LDO Design Perforance Parameters

| **Parameter**         | **Description**                                           | **Design I** | **Design II** | **Unit** | **Condition**                                             |
|----------------------|-----------------------------------------------------------|--------------|---------------|----------|----------------------------------------------------------|
| **Technology**        | Process                                                   | 0.18 µm CMOS | 0.18 µm CMOS  | -        | -                                                        |
| **Output Voltage**    | Regulated Output voltage                                   | 2.4V         | 1.5V          | V        | -                                                        |
| **R_FB1**              | Feedback resistor 1                                       | 150kΩ         | 150kΩ           | Ω        | -                                                        |
| **RFB2**               | Feedback resistor 2                                       | 150kΩ         | 600kΩ          | Ω        | -                                                        |
| **CL**                 | Load capacitance                                          | 10pF         | 10pF          | pF       | -                                                        |
| **Line Reg.**         | Line regulation (voltage change per unit supply voltage) | 3.311        | 3.365           | mV/V       | VDD=3.3V, T=27°C                                          |
| **Error Tolerance**   | Tolerance in output voltage variation                    | ±0.75%        | ±.8%         | %        | Over supply voltage variations           |
| **VDD min**   | minimum supply voltgae                   | 2.5     |    2.8    | V       | For regulated output under given error limit            |
| **VDD max**   | maximum supply voltgae                   |  6.2    |   6.7541     | V       | For regulated output under given error limit           |
| **VDO **    | Drop Out Voltage (difference between Vdd and Vout)      |  0.9         |     1.8    |    |     @Vdd=3.3V                                         |
| **PSRR @100kHz **    | Power Supply Rejection Ratio at specified frequency       | 50           | 60            | dB       | at 100 kHz                                                  |
| **PSRR @0Hz   **    | Power Supply Rejection Ratio at specified frequency       | 50           | 60            | dB       | at DC                                                 |


---

## Circuit Schematic
The following schematic illustrates the dual-mode LDO circuit, supporting both 1.2V and 1.8V supply configurations.
<p align="center">
  <img src="schematic.png" alt="LDO Block Diagram"/>
</p>
---

## Simulation Results (For Vreg=2.4)

### Line Regulation
<p align="center">
  <img src="line1.png" alt="line"/>
</p>

### Transient Line Regulation
<p align="center">
  <img src="linetran1.png" alt="linet1"/>
</p>

### Operating Point Analysis
<p align="center">
  <img src="op1.png" alt="op1"/>
</p>

### PSRR
<p align="center">
  <img src="psrr1.png" alt="ps1"/>
</p>
---
## Simulation Results (For Vreg=1.5)

### Line Regulation
<p align="center">
  <img src="line2.png" alt="line2"/>
</p>

### Transient Line Regulation
<p align="center">
  <img src="linetran2.png" alt="linet2"/>
</p>

### Operating Point Analysis
<p align="center">
  <img src="op2.png" alt="op2"/>
</p>

### PSRR
<p align="center">
  <img src="psrr2.png" alt="ps2"/>
</p>
---



# References
[1]	Jung Sik Kim, Khurram Javed, and Jeongjin Roh, “Design of a low-power and area-efficient ldo regulator using a negative-r-assisted technique,” IEEE Trans. Circuits Syst. II, vol. 70, no. 10, pp. 3892– 3896, Oct 2023.
[2]	Javed S Gaggatur and et.al, “A 0.009mm2 , 0-230mA Wide-range Load Current Output Capacitor-less Low Dropout Regulator for High Bandwidth Memory parallel IOs,” in 2022 35th International Conference on VLSI Design (VLSID), 2022, pp. 6–10. 
[3] M. Reza, N. Alam and S. J. Gaggatur, "A 0-24mA, 1.2V/1.8V Dual Mode Low Dropout Regulator Design for Efficient Power Management in Battery-Powered Systems," 2024 28th International Symposium on VLSI Design and Test (VDAT), Vellore, India, 2024, pp. 1-6, doi: 10.1109/VDAT63601.2024.10705731.


# Acknowledgments

- Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd., [kunalpghosh@gmail.com](mailto:kunalpghosh@gmail.com)
- Prof. Naushad Alam, Department of Electronics Engineering, Aligarh Muslim University
- Sumanto Kar, eSim Team, FOSSEE
- - FOSSEE, [https://fossee.in/](https://fossee.in/)
- Spoken Tutorial, [https://spoken-tutorial.org/](https://spoken-tutorial.org/)
- VLSI System Design, [https://www.vlsisystemdesign.com/](https://www.vlsisystemdesign.com/)
  
# Author

**Ayesha Parveen**,  
B.Tech Electronics Engineering,  
Zakir Husain College of Engineering and Technology (ZHCET),  
Aligarh Muslim University (AMU), Aligarh.


