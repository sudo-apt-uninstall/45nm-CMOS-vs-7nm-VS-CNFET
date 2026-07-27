# Investigation of VLSI Circuits Across Emerging Transistor Technologies

### Comparative Study of 45nm CMOS and 7nm Virtual-Source Carbon Nanotube FET

<p align="center">
  <b>Cadence Virtuoso · Spectre · GPDK045 · Stanford VS-CNFET · Verilog-A</b>
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#methodology">Methodology</a> •
  <a href="#circuit-implementations">Circuits</a> •
  <a href="#performance-results">Results</a> •
  <a href="#key-findings">Key Findings</a>
</p>

---

## Overview

This project investigates the performance of digital VLSI circuits implemented
using conventional **45nm CMOS** and emerging **7nm Virtual-Source Carbon
Nanotube FET (VS-CNFET)** technologies.

Three fundamental digital circuits were designed, simulated, and characterized:

- CMOS inverter
- Conventional 38-transistor (38T) full adder
- 10-transistor (10T) pass-transistor-logic full adder

The study examines both **device-technology scaling** and **circuit-topology
optimization**, rather than treating transistor technology as the sole
determinant of circuit performance.

Performance was evaluated using:

`Propagation Delay` · `Dynamic Power` · `Static Power` · `PDP` · `EDP` ·
`Drive Current` · `Noise Margin` · `Output Swing` · `Maximum Frequency`

---

## Performance at a Glance

| Circuit | Technology | Avg. Delay | Dynamic Power | PDP |
|---|---|---:|---:|---:|
| Inverter | 45nm CMOS | 19.87 ps | **5.953 µW** | 118.29 aJ |
| Inverter | **7nm VS-CNFET** | **3.895 ps** | 7.337 µW | **28.57 aJ** |
| 38T Full Adder | 45nm CMOS | 24.67 ps | **1.573 µW** | **38.80 aJ** |
| 38T Full Adder | **7nm VS-CNFET** | **8.773 ps** | 11.80 µW | 103.517 aJ |
| 10T PTL Full Adder | **45nm CMOS** | 18.791 ps | **184.23 nW** | **3.462 aJ** |
| 10T PTL Full Adder | 7nm VS-CNFET | **10.14 ps** | 784.96 nW | 7.960 aJ |

> **Central observation:** VS-CNFET provides a substantial switching-speed
> advantage, while circuit topology strongly influences power and
> energy efficiency. The fastest device technology does not necessarily
> produce the lowest-energy circuit implementation.

---

## Methodology

### Technology Platforms

| Parameter | 45nm CMOS | 7nm VS-CNFET |
|---|---|---|
| Device technology | Silicon CMOS | Carbon Nanotube FET |
| Technology node | 45nm | 7nm study configuration |
| Model / PDK | Cadence GPDK045 | Stanford VS-CNFET v1.0.1 |
| Supply voltage | 1.0 V | 0.71 V |
| Simulator | Cadence Spectre | Cadence Spectre |
| Design environment | Cadence Virtuoso | Cadence Virtuoso |
| Model implementation | PDK device models | Verilog-A |

### Design Flow

**Schematic Design → Testbench Construction → DC/Transient Simulation →
Delay & Power Extraction → PDP/EDP Calculation → Cross-Technology Analysis**

The inverter was first characterized to establish device-level switching
behavior. The investigation was then extended to 38T and 10T full-adder
architectures to study the interaction between **transistor technology and
logic topology**.

---

## Circuit Implementations

### 1. Inverter

The inverter provides the baseline comparison between 45nm CMOS and 7nm
VS-CNFET switching characteristics.

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/inverter/45nm-CMOS/cmos45-inverter-schematic.png" alt="45nm CMOS inverter schematic"></td>
<td><img src="circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-schematic.png" alt="7nm VS-CNFET inverter schematic"></td>
</tr>
</table>

#### Simulation Testbenches

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/inverter/45nm-CMOS/cmos45-inverter-testbench.png"></td>
<td><img src="circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-testbench.png"></td>
</tr>
</table>

#### DC Characteristics

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/inverter/45nm-CMOS/cmos45-inverter-dc-characteristics.png"></td>
<td><img src="circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-dc-characteristics.png"></td>
</tr>
</table>

#### Propagation-Delay Measurement

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/inverter/45nm-CMOS/cmos45-inverter-propagation-delay.png"></td>
<td><img src="circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-propagation-delay.png"></td>
</tr>
</table>

The VS-CNFET inverter achieved an average propagation delay of **3.895 ps**
compared with **19.87 ps** for 45nm CMOS — approximately a **5.1× speed
improvement**.

![Inverter Delay Comparison](results/inverter/inverter-delay-comparison.png)

<details>
<summary><b>Additional inverter characterization</b></summary>

### Drive Current

![Drive Current](results/inverter/inverter-drive-current-comparison.png)

### Power-Delay Product

![Inverter PDP](results/inverter/inverter-pdp-comparison.png)

### Static Power

![Static Power](results/inverter/inverter-static-power-comparison.png)

### Noise Margin

![Noise Margin](results/inverter/inverter-noise-margin-comparison.png)

### Output Swing

![Output Swing](results/inverter/inverter-output-swing-comparison.png)

</details>

---

### 2. 38T Full Adder

The conventional 38T full adder was implemented in both technologies to
evaluate device-level performance while retaining a full-swing complementary
logic topology.

#### Schematics

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/full-adder-38T/45nm-CMOS/cmos45-full-adder-38t-schematic.png"></td>
<td><img src="circuits/full-adder-38T/7nm-VS-CNFET/vscnfet7-full-adder-38t-schematic.png"></td>
</tr>
</table>

#### Transient Verification

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/full-adder-38T/45nm-CMOS/cmos45-full-adder-38t-transient.png"></td>
<td><img src="circuits/full-adder-38T/7nm-VS-CNFET/vscnfet7-full-adder-38t-transient.png"></td>
</tr>
</table>

The VS-CNFET implementation reduced average propagation delay from
**24.67 ps to 8.773 ps**, corresponding to approximately **2.81× higher
speed**. However, the CMOS implementation demonstrated lower dynamic power
and PDP for this topology.

<table>
<tr>
<td><img src="results/full-adder-38T/full-adder-38t-delay-comparison.png"></td>
<td><img src="results/full-adder-38T/full-adder-38t-average-power.png"></td>
</tr>
</table>

<details>
<summary><b>38T power characterization</b></summary>

![38T PDP](results/full-adder-38T/full-adder-38t-pdp.png)

![38T Static Power](results/full-adder-38T/full-adder-38t-static-power.png)

</details>

---

### 3. 10T Pass-Transistor-Logic Full Adder

The 10T implementation investigates whether **logic-topology optimization**
can complement or outweigh the benefits obtained from transistor scaling.

#### Schematics

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/full-adder-10T/45nm-CMOS/cmos45-full-adder-10t-schematic.png"></td>
<td><img src="circuits/full-adder-10T/7nm-VS-CNFET/vscnfet7-full-adder-10t-schematic.png"></td>
</tr>
</table>

#### Transient Verification

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/full-adder-10T/45nm-CMOS/cmos45-full-adder-10t-transient.png"></td>
<td><img src="circuits/full-adder-10T/7nm-VS-CNFET/vscnfet7-full-adder-10t-transient.png"></td>
</tr>
</table>

The VS-CNFET implementation achieved approximately **1.85× higher speed**.
However, the **45nm CMOS 10T full adder achieved a PDP of only 3.462 aJ**,
the lowest PDP among the evaluated full-adder implementations.

<table>
<tr>
<td><img src="results/full-adder-10T/full-adder-10t-delay-comparison.png"></td>
<td><img src="results/full-adder-10T/full-adder-10t-average-power.png"></td>
</tr>
</table>

<details>
<summary><b>10T power characterization</b></summary>

![10T PDP](results/full-adder-10T/full-adder-10t-pdp.png)

![10T Static Power](results/full-adder-10T/full-adder-10t-static-power.png)

</details>

---

## Performance Results

### Architecture vs. Technology

![Architecture vs Technology](results/comparative-analysis/architecture-vs-technology-delay.png)

The results show two distinct optimization dimensions:

- **Technology scaling:** 7nm VS-CNFET consistently reduces propagation delay.
- **Topology optimization:** the 10T PTL architecture substantially reduces
  power consumption and PDP relative to the conventional 38T implementation.

### Power–Delay Design Space

![Power Delay Pareto](results/comparative-analysis/power-delay-pareto.png)

The Pareto analysis illustrates why there is no universally superior
implementation: designs optimized for maximum speed occupy a different region
of the power-delay space from designs optimized for energy efficiency.

### Normalized Performance

![Normalized Performance](results/comparative-analysis/normalized-performance.png)

<details>
<summary><b>Additional cross-technology results</b></summary>

### Energy-Delay Product

![EDP Comparison](results/comparative-analysis/edp-comparison.png)

### Energy Efficiency

![Energy Efficiency](results/comparative-analysis/energy-efficiency-comparison.png)

### Maximum Operating Frequency

![Maximum Frequency](results/comparative-analysis/maximum-frequency-comparison.png)

### Technology Speedup

![Speedup](results/comparative-analysis/speedup-comparison.png)

### Static Power

![Static Power](results/comparative-analysis/static-power-comparison.png)

</details>

---

## Key Findings

1. **VS-CNFET demonstrated a substantial speed advantage.**  
   The inverter achieved approximately **5.1×**, the 38T full adder **2.81×**,
   and the 10T full adder **1.85×** higher switching speed relative to their
   45nm CMOS counterparts.

2. **Higher device speed did not automatically produce better energy efficiency.**  
   The evaluated VS-CNFET full adders consumed more power than their CMOS
   counterparts under the simulated conditions.

3. **Circuit topology strongly influenced the final result.**  
   Reducing the full-adder implementation from 38T complementary logic to
   10T pass-transistor logic produced substantial power savings.

4. **The 45nm CMOS 10T full adder achieved the lowest full-adder PDP.**  
   Its **3.462 aJ** PDP demonstrates that architectural optimization can
   compensate for the performance limitations of an older technology node.

5. **Technology and architecture must be co-optimized.**  
   VS-CNFET is particularly attractive for speed-critical designs, while
   optimized CMOS/PTL implementations can remain highly competitive for
   energy-constrained applications.

---

## Tools & Skills

| Category | Technologies / Concepts |
|---|---|
| EDA | Cadence Virtuoso, Cadence Spectre |
| Device Technologies | 45nm CMOS, CNFET, VS-CNFET |
| Models | GPDK045, Stanford VS-CNFET v1.0.1, Verilog-A |
| Circuit Design | CMOS Logic, Inverter Design, Full Adders, PTL |
| Characterization | Transient Analysis, DC Analysis, Propagation Delay |
| Power Analysis | Dynamic Power, Static Power, PDP, EDP |
| Performance | Drive Current, Noise Margin, Output Swing, Maximum Frequency |
| Domain | Digital VLSI Design, Nanoelectronics, Emerging Transistor Technologies |

---

## Repository Structure

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
```

---

## Reproducibility

This repository contains the circuit schematics, simulation outputs, and
characterization results used to document the study.

The **Cadence GPDK045 PDK and third-party VS-CNFET model files are not
redistributed**. Reproduction therefore requires authorized access to the
corresponding PDK/model resources and a compatible Cadence simulation
environment.

---

## Author

**Deepesh J**  
B.Tech — Electronics and Communication Engineering  
SRM Institute of Science and Technology, Vadapalani

---

## Acknowledgements

This investigation was conducted as part of academic work in **VLSI design
and emerging semiconductor technologies** at SRM Institute of Science and
Technology.