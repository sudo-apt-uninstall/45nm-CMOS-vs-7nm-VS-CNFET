# References

This bibliography contains the principal literature, compact-model documentation,
and circuit-design references used for the project:

**Investigation of VLSI Circuits Across Emerging Transistor Technologies:
A Comparative Study of 45nm CMOS and 7nm Carbon Nanotube FET**

[← Back to main project page](../README.md)

---

## CNFET Technology and Device Modeling

### [1] Stanford Virtual-Source CNFET Model

C.-S. Lee and H.-S. P. Wong,  
**“Stanford Virtual-Source Carbon Nanotube Field-Effect Transistors Model — Technical User Manual, Version 1.0.1,”**  
Stanford University, Stanford, CA, USA, 2015.

This is the primary compact-model documentation for the VS-CNFET devices used
in this project.

---

### [2] Virtual-Source Compact Model

C.-S. Lee *et al.*,  
**“A Compact Virtual-Source Model for Carbon Nanotube FETs in the Sub-10-nm Regime—Part I: Intrinsic Elements,”**  
*IEEE Transactions on Electron Devices*, vol. 62, no. 9, pp. 3061–3069, Sep. 2015.

This work describes the virtual-source modeling framework used for compact
simulation of aggressively scaled CNFET devices.

---

### [3] Complementary CNT Microprocessor

G. Hills, C. Lau, A. Wright *et al.*,  
**“Modern microprocessor built from complementary carbon nanotube transistors,”**  
*Nature*, vol. 572, pp. 595–602, 2019.

This work demonstrates system-level feasibility of complementary carbon
nanotube transistor technology through a functional microprocessor.

---

### [4] Carbon-Based Electronics

P. Avouris, Z. Chen, and V. Perebeinos,  
**“Carbon-based electronics,”**  
*Nature Nanotechnology*, vol. 2, pp. 605–615, 2007.

---

### [5] Carbon Nanotube Electronics

P. Avouris, J. Appenzeller, R. Martel, and S. J. Wind,  
**“Carbon Nanotube Electronics,”**  
*Proceedings of the IEEE*, vol. 91, no. 11, pp. 1772–1784, Nov. 2003.

---

### [6] CNTFET Review

A. Zahoor *et al.*,  
**“Carbon Nanotube Field-Effect Transistor (CNTFET): A Review,”**  
*Micromachines*, vol. 12, no. 11, Art. no. 1288, 2021.  
DOI: 10.3390/mi12111288

---

## CMOS and Digital VLSI

### [7] CMOS VLSI Design

N. H. E. Weste and D. M. Harris,  
**CMOS VLSI Design: A Circuits and Systems Perspective**, 4th ed.  
Boston, MA, USA: Addison-Wesley/Pearson, 2010.

This text provides the conventional CMOS design, timing, power, and scaling
background used throughout the study.

---

### [8] Digital Integrated Circuits

J. M. Rabaey, A. Chandrakasan, and B. Nikolić,  
**Digital Integrated Circuits: A Design Perspective**, 2nd ed.  
Upper Saddle River, NJ, USA: Prentice Hall, 2003.

---

### [9] Advanced CMOS Scaling

M. Vinet *et al.*,  
**“Challenges and Opportunities in CMOS Scaling Below 3nm,”**  
*Nature Electronics*, 2022.

This work provides background on the physical and technological challenges
associated with continued CMOS scaling.

---

### [10] Predictive Advanced-Node Technology

L. T. Clark, V. Vashishtha, L. Shifren *et al.*,  
**“ASAP7: A 7-nm FinFET Predictive Process Design Kit,”**  
*Microelectronics Journal*, vol. 53, pp. 105–115, 2016.

---

## Full-Adder and Low-Power Circuit Design

### [11] High-Performance CMOS Full Adder

A. M. Shams and M. A. Bayoumi,  
**“A novel high-performance CMOS 1-bit full adder cell,”**  
*IEEE Transactions on Circuits and Systems II: Analog and Digital Signal Processing*,  
vol. 47, no. 5, pp. 478–481, 2000.

This work is an important reference for reduced-transistor-count and
high-performance full-adder architectures.

---

### [12] CNFET Full-Adder Design

A. T. Mahani and P. Keshavarzian,  
**“A Novel Energy-Efficient and High-Performance Full Adder Cells Based on
Carbon Nanotube FET for VLSI Arithmetic,”**  
*Microelectronics Journal*, vol. 68, pp. 142–152, 2017.

---

### [13] 10T Pass-Transistor Full Adder

P. Palaniappan, S. Suresh, and C. Arun,  
**“Implementation of 10 Transistor Full Adder Using Pass Transistor Logic,”**  
*International Journal of Engineering Science Invention*,  
vol. 6, no. 5, pp. 29–33, 2017.

---

### [14] Low-Power 8T and 10T Full Adders

N. Ibrahim *et al.*,  
**“Analysis and Design of Low Power 8T and 10T Full Adder CMOS Technology,”**  
in *Proceedings of the IEEE 13th Annual Information Technology, Electronics
and Mobile Communication Conference (IEMCON)*, Vancouver, Canada, 2022,
pp. 1–6.

---

### [15] Low-Power Full Adder at 45nm

B. Priyadharshini, R. Sathiyapriya, C. Kalpana, and T. Kayalvizhi,  
**“Design and Analysis of Low Power 14-Transistor Full Adder in 45nm Technology,”**  
*International Journal of Engineering Research and Technology*,  
vol. 10, no. 5, 2021.

---

## Related CNFET Circuit Research

### [16] CNFET Low-Power Digital Circuits

S. Sharma and R. Raj,  
**“Low-Power Digital Circuit Design Using Carbon Nanotube Field Effect
Transistors,”**  
*VLSI Design*, vol. 2021, Article ID 5541589, 2021.

---

### [17] CNFET Sequential Logic

P. Nagarajan, A. Dinesh Babu, P. Kabilamani, M. Mahita,
Manoj K., and Abdul Salam,  
**“Design and Implementation of Sequential Element Based on CNFET Using
Multi-threshold Style for Low Power and High-Performance VLSI Architectures,”**  
2025.

---

## PDK and Model Availability

The following technology resources were used during circuit simulation but are
**not redistributed in this repository**:

- Cadence GPDK045
- Stanford Virtual-Source CNFET model files
- Cadence proprietary simulation/model resources

Users seeking to reproduce the simulations should obtain these resources from
their respective authorized sources and comply with the applicable licensing
and distribution terms.

---

## Citation Note

Reference numbering in the main [`README.md`](../README.md) corresponds to the
numbering used in this document.

The bibliography is provided for academic attribution and technical context.
For authoritative device parameters, equations, model limitations, and
experimental results, consult the original publications and model
documentation.