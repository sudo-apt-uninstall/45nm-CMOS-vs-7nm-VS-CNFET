# Investigation of VLSI Circuits Across Emerging Transistor Technologies

### A Comparative Study of 45nm CMOS and 7nm Virtual-Source Carbon Nanotube FET

<p align="center">
  <b>Cadence Virtuoso · Spectre · GPDK045 · Stanford VS-CNFET · Verilog-A</b>
</p>

<p align="center">
  <a href="#overview">Overview</a> •
  <a href="#methodology">Methodology</a> •
  <a href="#circuit-implementations">Circuits</a> •
  <a href="#performance-results">Results</a> •
  <a href="#key-findings">Key Findings</a> •
  <a href="docs/REFERENCES.md">References</a>
</p>

---

## Overview

Continued CMOS scaling is increasingly constrained by short-channel effects,
leakage, power density, and other physical limitations at aggressively scaled
technology nodes [[7]](docs/REFERENCES.md) [[9]](docs/REFERENCES.md).
Carbon Nanotube Field-Effect Transistors (CNFETs) have therefore been
investigated as a potential post-silicon device technology because of their
favorable electrostatic and carrier-transport characteristics
[[4]](docs/REFERENCES.md) [[5]](docs/REFERENCES.md).

The feasibility of complementary carbon-nanotube transistor technology has
also been demonstrated beyond individual devices and logic gates through the
construction of a functional CNT-based microprocessor
[[3]](docs/REFERENCES.md).

This project performs a circuit-level investigation of conventional
**45nm CMOS** and emerging **7nm Virtual-Source Carbon Nanotube FET
(VS-CNFET)** technologies.

Three digital circuits were designed, simulated, and characterized:

- CMOS inverter
- Conventional 38-transistor (38T) full adder
- 10-transistor (10T) pass-transistor-logic full adder

The study investigates two distinct optimization dimensions:

1. **Device technology** — 45nm CMOS vs. 7nm VS-CNFET
2. **Circuit topology** — conventional 38T logic vs. reduced-transistor-count 10T PTL

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
> advantage, while circuit topology strongly influences power and energy
> efficiency. The fastest device technology does not necessarily produce the
> lowest-energy circuit implementation.

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

The VS-CNFET implementation is based on the **Stanford Virtual-Source CNFET
compact model v1.0.1** [[1]](docs/REFERENCES.md), using the virtual-source
modeling framework developed for aggressively scaled CNFET devices
[[2]](docs/REFERENCES.md).

The 45nm CMOS implementations use Cadence GPDK045 as the conventional silicon
baseline. CMOS circuit design, switching, timing, and power-characterization
principles follow established digital VLSI methodology
[[7]](docs/REFERENCES.md) [[8]](docs/REFERENCES.md).

### Design and Characterization Flow

**Schematic Design → Testbench Construction → DC/Transient Simulation →
Delay & Power Extraction → PDP/EDP Calculation → Cross-Technology Analysis**

The inverter was characterized first to establish a device-level switching
baseline. The investigation was then extended to the 38T and 10T full-adder
architectures to evaluate how transistor technology interacts with logic
topology.

---

## Circuit Implementations

### 1. Inverter

The inverter provides the fundamental switching baseline for comparing the
45nm CMOS and 7nm VS-CNFET implementations.

#### Schematics

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
<td><img src="circuits/inverter/45nm-CMOS/cmos45-inverter-testbench.png" alt="45nm CMOS inverter testbench"></td>
<td><img src="circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-testbench.png" alt="7nm VS-CNFET inverter testbench"></td>
</tr>
</table>

#### DC Characteristics

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/inverter/45nm-CMOS/cmos45-inverter-dc-characteristics.png" alt="45nm CMOS inverter DC characteristics"></td>
<td><img src="circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-dc-characteristics.png" alt="7nm VS-CNFET inverter DC characteristics"></td>
</tr>
</table>

#### Propagation-Delay Measurement

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/inverter/45nm-CMOS/cmos45-inverter-propagation-delay.png" alt="45nm CMOS inverter propagation delay"></td>
<td><img src="circuits/inverter/7nm-VS-CNFET/vscnfet7-inverter-propagation-delay.png" alt="7nm VS-CNFET inverter propagation delay"></td>
</tr>
</table>

### Inverter Results

The 7nm VS-CNFET inverter achieved an average propagation delay of
**3.895 ps**, compared with **19.87 ps** for the 45nm CMOS implementation,
corresponding to approximately a **5.1× speed improvement**.

Its PDP was also reduced from **118.29 aJ to 28.57 aJ**, although the simulated
dynamic power increased from **5.953 µW to 7.337 µW**.

![Inverter Delay Comparison](results/inverter/inverter-delay-comparison.png)

<details>
<summary><b>Additional inverter characterization</b></summary>

### Drive Current

![Drive Current Comparison](results/inverter/inverter-drive-current-comparison.png)

### Power-Delay Product

![Inverter PDP Comparison](results/inverter/inverter-pdp-comparison.png)

### Static Power

![Inverter Static Power Comparison](results/inverter/inverter-static-power-comparison.png)

### Noise Margin

![Inverter Noise Margin Comparison](results/inverter/inverter-noise-margin-comparison.png)

### Output Swing

![Inverter Output Swing Comparison](results/inverter/inverter-output-swing-comparison.png)

</details>

---

### 2. 38T Full Adder

The conventional 38T full adder was implemented in both technologies to
evaluate the influence of device technology while retaining a complementary,
full-swing logic architecture.

#### Schematics

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/full-adder-38T/45nm-CMOS/cmos45-full-adder-38t-schematic.png" alt="45nm CMOS 38T full adder schematic"></td>
<td><img src="circuits/full-adder-38T/7nm-VS-CNFET/vscnfet7-full-adder-38t-schematic.png" alt="7nm VS-CNFET 38T full adder schematic"></td>
</tr>
</table>

#### Transient Verification

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/full-adder-38T/45nm-CMOS/cmos45-full-adder-38t-transient.png" alt="45nm CMOS 38T full adder transient response"></td>
<td><img src="circuits/full-adder-38T/7nm-VS-CNFET/vscnfet7-full-adder-38t-transient.png" alt="7nm VS-CNFET 38T full adder transient response"></td>
</tr>
</table>

### 38T Results

The VS-CNFET implementation reduced average propagation delay from
**24.67 ps to 8.773 ps**, corresponding to approximately a **2.81× speed
improvement**.

However, the 45nm CMOS implementation consumed substantially less dynamic
power and achieved the lower PDP for this topology.

<table>
<tr>
<td><img src="results/full-adder-38T/full-adder-38t-delay-comparison.png" alt="38T delay comparison"></td>
<td><img src="results/full-adder-38T/full-adder-38t-average-power.png" alt="38T average power comparison"></td>
</tr>
</table>

<details>
<summary><b>Additional 38T power characterization</b></summary>

### Power-Delay Product

![38T PDP](results/full-adder-38T/full-adder-38t-pdp.png)

### Static Power

![38T Static Power](results/full-adder-38T/full-adder-38t-static-power.png)

</details>

---

### 3. 10T Pass-Transistor-Logic Full Adder

Reduced-transistor-count and pass-transistor full-adder architectures have
been extensively investigated as approaches to improving power and
power-delay characteristics
[[11]](docs/REFERENCES.md)
[[13]](docs/REFERENCES.md)
[[14]](docs/REFERENCES.md).

The 10T implementation in this study provides an additional dimension to the
comparison: whether **circuit-topology optimization can complement or outweigh
the benefits obtained purely from transistor scaling**.

#### Schematics

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/full-adder-10T/45nm-CMOS/cmos45-full-adder-10t-schematic.png" alt="45nm CMOS 10T full adder schematic"></td>
<td><img src="circuits/full-adder-10T/7nm-VS-CNFET/vscnfet7-full-adder-10t-schematic.png" alt="7nm VS-CNFET 10T full adder schematic"></td>
</tr>
</table>

#### Transient Verification

<table>
<tr>
<th align="center">45nm CMOS</th>
<th align="center">7nm VS-CNFET</th>
</tr>
<tr>
<td><img src="circuits/full-adder-10T/45nm-CMOS/cmos45-full-adder-10t-transient.png" alt="45nm CMOS 10T full adder transient response"></td>
<td><img src="circuits/full-adder-10T/7nm-VS-CNFET/vscnfet7-full-adder-10t-transient.png" alt="7nm VS-CNFET 10T full adder transient response"></td>
</tr>
</table>

### 10T Results

The 7nm VS-CNFET implementation reduced average propagation delay from
**18.791 ps to 10.14 ps**, corresponding to approximately a **1.85× speed
improvement**.

However, the **45nm CMOS 10T implementation achieved a PDP of only
3.462 aJ**, the lowest PDP among all evaluated full-adder implementations.

<table>
<tr>
<td><img src="results/full-adder-10T/full-adder-10t-delay-comparison.png" alt="10T delay comparison"></td>
<td><img src="results/full-adder-10T/full-adder-10t-average-power.png" alt="10T average power comparison"></td>
</tr>
</table>

<details>
<summary><b>Additional 10T power characterization</b></summary>

### Power-Delay Product

![10T PDP](results/full-adder-10T/full-adder-10t-pdp.png)

### Static Power

![10T Static Power](results/full-adder-10T/full-adder-10t-static-power.png)

</details>

---

## Performance Results

### Architecture vs. Technology

![Architecture vs Technology](results/comparative-analysis/architecture-vs-technology-delay.png)

The results reveal two distinct optimization mechanisms:

- **Technology scaling:** the evaluated 7nm VS-CNFET implementations
  consistently reduce propagation delay.
- **Topology optimization:** the 10T PTL architecture substantially reduces
  dynamic power and PDP relative to the conventional 38T implementation.

### Power–Delay Design Space

![Power Delay Pareto](results/comparative-analysis/power-delay-pareto.png)

The power-delay design space demonstrates why no single implementation is
universally optimal. Designs optimized for maximum switching speed occupy a
different region from designs optimized for low power or minimum PDP.

### Normalized Performance

![Normalized Performance](results/comparative-analysis/normalized-performance.png)

<details>
<summary><b>Additional cross-technology analysis</b></summary>

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

1. **VS-CNFET demonstrated a substantial switching-speed advantage.**  
   The inverter achieved approximately **5.1×**, the 38T full adder **2.81×**,
   and the 10T full adder **1.85×** higher switching speed relative to the
   corresponding 45nm CMOS implementations.

2. **Higher device speed did not automatically produce better power efficiency.**  
   The evaluated VS-CNFET full adders consumed more dynamic power than their
   CMOS counterparts under the simulated operating conditions.

3. **Circuit topology had a major influence on overall performance.**  
   Reducing the full-adder implementation from 38T complementary logic to
   10T pass-transistor logic produced substantial reductions in dynamic power.

4. **The 45nm CMOS 10T full adder achieved the lowest full-adder PDP.**  
   Its **3.462 aJ** PDP demonstrates that topology-level optimization can
   compensate for some performance limitations of an older technology node.

5. **Technology and architecture must be co-optimized.**  
   The results do not support treating either CNFET or CMOS as universally
   superior. The preferred implementation depends on whether the design
   objective prioritizes speed, power, energy efficiency, output integrity,
   or another system-level constraint.

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

## References and Technical Background

The device models, circuit architectures, characterization methodology, and
technology context used in this investigation are supported by established
literature covering **CMOS VLSI, CNFET compact modeling, carbon-nanotube
electronics, and low-power full-adder design**.

Key references include:

- Stanford Virtual-Source CNFET model documentation [[1]](docs/REFERENCES.md)
- Sub-10nm VS-CNFET compact-model research [[2]](docs/REFERENCES.md)
- Complementary CNT microprocessor demonstration by Hills *et al.* [[3]](docs/REFERENCES.md)
- Standard CMOS VLSI references [[7]](docs/REFERENCES.md) [[8]](docs/REFERENCES.md)
- Full-adder and PTL literature [[11]](docs/REFERENCES.md)–[[15]](docs/REFERENCES.md)
- Related CNFET circuit research [[16]](docs/REFERENCES.md) [[17]](docs/REFERENCES.md)

### **[View the complete bibliography →](docs/REFERENCES.md)**

---

## Repository Structure

```text
.
├── circuits/
│   ├── inverter/
│   │   ├── 45nm-CMOS/
│   │   └── 7nm-VS-CNFET/
│   │
│   ├── full-adder-38T/
│   │   ├── 45nm-CMOS/
│   │   └── 7nm-VS-CNFET/
│   │
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
├── docs/
│   └── REFERENCES.md
│
├── .gitignore
└── README.md
```

---

## Reproducibility

This repository contains selected circuit schematics, simulation outputs, and
characterization results used to document the investigation.

The **Cadence GPDK045 PDK and Stanford VS-CNFET model files are not
redistributed** in this repository. Reproducing the simulations therefore
requires authorized access to the corresponding technology/model resources
and a compatible Cadence simulation environment.

See [`docs/REFERENCES.md`](docs/REFERENCES.md) for the VS-CNFET model
documentation and technical literature used by the study.

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

---

<p align="center">
  <b>45nm CMOS · 7nm VS-CNFET · Digital VLSI · Emerging Transistor Technologies</b>
</p>