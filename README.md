\# Investigation of VLSI Circuits Across Emerging Transistor Technologies



\### A Comparative Study of 45nm CMOS and 7nm Carbon Nanotube FET



A circuit-level investigation of conventional \*\*45nm CMOS\*\* and emerging

\*\*7nm Virtual-Source Carbon Nanotube FET (VS-CNFET)\*\* technologies through

the design, simulation, and characterization of digital VLSI circuits.



The study evaluates how transistor technology and circuit topology influence

\*\*propagation delay, power consumption, power-delay product (PDP), energy-delay

product (EDP), drive current, noise margins, output swing, and maximum operating

frequency\*\*.



\---



\## Overview



Continued transistor scaling presents increasing challenges involving leakage

current, short-channel effects, power density, and performance. Carbon Nanotube

Field-Effect Transistors (CNFETs) are a promising emerging-device technology

for extending digital circuit performance beyond conventional silicon CMOS.



This project investigates these trade-offs through circuit-level simulations of:



\- CMOS inverter

\- 38-transistor (38T) full adder

\- 10-transistor (10T) pass-transistor-logic full adder



Each circuit was implemented using both:



| Technology | Technology Node | Supply Voltage |

|---|---:|---:|

| CMOS | 45nm | 1.0 V |

| VS-CNFET | 7nm | 0.71 V |



The CMOS implementations use \*\*Cadence GPDK045\*\*, while the CNFET

implementations use the \*\*Stanford Virtual-Source CNFET model (v1.0.1)\*\*.



\---



\## Tools and Technologies



\- Cadence Virtuoso

\- Cadence Spectre

\- GPDK045

\- Stanford Virtual-Source CNFET Model v1.0.1

\- Verilog-A

\- CMOS Digital VLSI Design

\- Carbon Nanotube FET (CNFET)

\- Pass-Transistor Logic (PTL)

\- Circuit Characterization

\- Power and Delay Analysis



\---



\# 1. Inverter Characterization



The inverter provides a device-level baseline for comparing the switching

behavior of the two transistor technologies.



\## 45nm CMOS Inverter



\### Schematic



!\[45nm CMOS inverter schematic](circuits/inverter/45nm-CMOS/cmos45-inverter-schematic.png)



\### Simulation Testbench



!\[45nm CMOS inverter testbench](circuits/inverter/45nm-CMOS/cmos45-inverter-testbench.png)



\### DC Characteristics



!\[45nm CMOS inverter DC characteristics](circuits/inverter/45nm-CMOS/cmos45-inverter-dc-characteristics.png)



\### Propagation Delay



!\[45nm CMOS inverter propagation delay](circuits/inverter/45nm-CMOS/cmos45-inverter-propagation-delay.png)



\---



\## 7nm VS-CNFET Inverter



\### Schematic



!\[7nm VS-CNFET inverter schematic](circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-schematic.png)



\### Simulation Testbench



!\[7nm VS-CNFET inverter testbench](circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-testbench.png)



\### DC Characteristics



!\[7nm VS-CNFET inverter DC characteristics](circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-dc-characteristics.png)



\### Propagation Delay



!\[7nm VS-CNFET inverter propagation delay](circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-propagation-delay.png)



\---



\## Inverter Results



| Metric | 45nm CMOS | 7nm VS-CNFET |

|---|---:|---:|

| Average propagation delay | 19.87 ps | \*\*3.895 ps\*\* |

| Dynamic power | \*\*5.953 µW\*\* | 7.337 µW |

| PDP | 118.29 aJ | \*\*28.57 aJ\*\* |



The 7nm VS-CNFET inverter achieves approximately \*\*5.1× lower propagation

delay\*\*, demonstrating the substantial switching-speed advantage of the

scaled CNFET implementation.



!\[Inverter delay comparison](results/inverter/inverter-delay-comparison.png)



!\[Inverter PDP comparison](results/inverter/inverter-pdp-comparison.png)



!\[Inverter drive current comparison](results/inverter/inverter-drive-current-comparison.png)



\---



\# 2. 38T Full Adder



A conventional 38-transistor full-adder architecture was implemented in both

technologies to evaluate the effect of device technology while retaining a

full-swing complementary circuit topology.



\## 45nm CMOS



\### Schematic



!\[45nm CMOS 38T full adder](circuits/full-adder-38T/45nm-CMOS/cmos45-full-adder-38t-schematic.png)



\### Transient Response



!\[45nm CMOS 38T transient response](circuits/full-adder-38T/45nm-CMOS/cmos45-full-adder-38t-transient.png)



\## 7nm VS-CNFET



\### Schematic



!\[7nm VS-CNFET 38T full adder](circuits/full-adder-38T/7nm-VS-CNFET/vscnfet7-full-adder-38t-schematic.png)



\### Transient Response



!\[7nm VS-CNFET 38T transient response](circuits/full-adder-38T/7nm-VS-CNFET/vscnfet7-full-adder-38t-transient.png)



\## Results



| Metric | 45nm CMOS | 7nm VS-CNFET |

|---|---:|---:|

| Average propagation delay | 24.67 ps | \*\*8.773 ps\*\* |

| Average dynamic power | \*\*1.573 µW\*\* | 11.80 µW |

| PDP | \*\*38.80 aJ\*\* | 103.517 aJ |



The VS-CNFET implementation provides approximately \*\*2.81× higher speed\*\*,

while the CMOS implementation retains a significant power and PDP advantage

for this topology.



!\[38T delay comparison](results/full-adder-38T/full-adder-38t-delay-comparison.png)



!\[38T average power comparison](results/full-adder-38T/full-adder-38t-average-power.png)



!\[38T PDP comparison](results/full-adder-38T/full-adder-38t-pdp.png)



\---



\# 3. 10T Pass-Transistor Full Adder



The 10T implementation investigates the interaction between \*\*device

technology and circuit topology\*\*. Reducing the transistor count through

pass-transistor logic significantly changes the power-performance trade-off.



\## 45nm CMOS



\### Schematic



!\[45nm CMOS 10T full adder](circuits/full-adder-10T/45nm-CMOS/cmos45-full-adder-10t-schematic.png)



\### Transient Response



!\[45nm CMOS 10T transient response](circuits/full-adder-10T/45nm-CMOS/cmos45-full-adder-10t-transient.png)



\## 7nm VS-CNFET



\### Schematic



!\[7nm VS-CNFET 10T full adder](circuits/full-adder-10T/7nm-VS-CNFET/vscnfet7-full-adder-10t-schematic.png)



\### Transient Response



!\[7nm VS-CNFET 10T transient response](circuits/full-adder-10T/7nm-VS-CNFET/vscnfet7-full-adder-10t-transient.png)



\## Results



| Metric | 45nm CMOS | 7nm VS-CNFET |

|---|---:|---:|

| Average propagation delay | 18.791 ps | \*\*10.14 ps\*\* |

| Average dynamic power | \*\*184.23 nW\*\* | 784.96 nW |

| PDP | \*\*3.462 aJ\*\* | 7.960 aJ |



The VS-CNFET implementation provides approximately \*\*1.85× higher speed\*\*.

However, the 45nm CMOS 10T implementation achieves the \*\*lowest PDP among

the evaluated full-adder configurations\*\*.



!\[10T delay comparison](results/full-adder-10T/full-adder-10t-delay-comparison.png)



!\[10T average power comparison](results/full-adder-10T/full-adder-10t-average-power.png)



!\[10T PDP comparison](results/full-adder-10T/full-adder-10t-pdp.png)



\---



\# Comparative Analysis



The results demonstrate that transistor technology alone does not determine

the optimum digital circuit implementation.



\*\*VS-CNFET provides a strong speed advantage\*\*, particularly at the inverter

level, while the CMOS implementations exhibit favorable power characteristics

for the evaluated operating conditions.



Circuit topology also has a substantial effect. The 10T PTL architecture

significantly reduces dynamic power compared with the conventional 38T

architecture, demonstrating that architectural optimization can be as

important as device scaling.



!\[Architecture vs technology delay](results/comparative-analysis/architecture-vs-technology-delay.png)



!\[Normalized performance](results/comparative-analysis/normalized-performance.png)



!\[Power-delay Pareto analysis](results/comparative-analysis/power-delay-pareto.png)



!\[Energy-delay comparison](results/comparative-analysis/edp-comparison.png)



!\[Maximum operating frequency](results/comparative-analysis/maximum-frequency-comparison.png)



\---



\## Key Findings



\- The \*\*7nm VS-CNFET inverter\*\* achieved approximately \*\*5.1× lower propagation delay\*\* than the 45nm CMOS inverter.

\- The \*\*7nm VS-CNFET 38T full adder\*\* achieved approximately \*\*2.81× higher speed\*\* than its CMOS counterpart.

\- The \*\*7nm VS-CNFET 10T full adder\*\* achieved approximately \*\*1.85× higher speed\*\* than the corresponding CMOS implementation.

\- The \*\*45nm CMOS 10T PTL full adder\*\* achieved the lowest PDP among the evaluated full-adder configurations.

\- Reduced transistor count substantially improved power efficiency in the 10T architecture.

\- The results demonstrate a fundamental \*\*speed-power trade-off\*\* between the evaluated CMOS and VS-CNFET implementations.

\- Both \*\*device technology and circuit topology\*\* must therefore be considered when optimizing digital VLSI circuits.



\---



\## Repository Structure



```text

.

├── circuits/

│   ├── inverter/

│   │   ├── 45nm-CMOS/

│   │   └── 7nm-VS-CNFET/

│   ├── full-adder-38T/

│   │   ├── 45nm-CMOS/

│   │   └── 7nm-VS-CNFET/

│   └── full-adder-10T/

│       ├── 45nm-CMOS/

│       └── 7nm-VS-CNFET/

│

├── results/

│   ├── inverter/

│   ├── full-adder-38T/

│   ├── full-adder-10T/

│   └── comparative-analysis/

│

└── README.md


Model and Reproducibility Note

This repository documents circuit implementations, simulation outputs, and
characterization results from the study.

The Cadence GPDK045 PDK and third-party device-model files are not
redistributed in this repository. Users wishing to reproduce the simulations
should obtain the required PDK and Stanford VS-CNFET model from their
respective authorized sources and comply with the applicable licensing terms.

Author

Deepesh J
B.Tech Electronics and Communication Engineering
SRM Institute of Science and Technology, Vadapalani

Acknowledgements

This project was carried out as part of academic work in VLSI design and
emerging semiconductor technologies at SRM Institute of Science and
Technology.

