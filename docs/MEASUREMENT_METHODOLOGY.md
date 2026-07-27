# Simulation and Measurement Methodology

[← Back to README](../README.md)

This document describes the simulation conditions, measurement definitions
and derived metrics used for the comparative investigation of **45nm CMOS**
and **7nm VS-CNFET** digital circuits.

The numerical results reported in this repository are derived from the
Cadence/Spectre simulation outputs.

---

## Evidence Priority

Results in this repository are interpreted using the following hierarchy:

1. Cadence/Spectre simulation outputs
2. Values extracted from the simulation outputs
3. Metrics calculated from those values
4. Netlist and model configuration
5. Literature and explanatory discussion

Literature is therefore used for model provenance and technical context, not
as a replacement for measured simulation results.

---

## Simulation Environment

| Parameter | 45nm CMOS | 7nm VS-CNFET |
|---|---|---|
| Design environment | Cadence Virtuoso | Cadence Virtuoso |
| Simulator | Cadence Spectre | Cadence Spectre |
| Device model | GPDK045 | Stanford VS-CNFET v1.0.1 |
| Model interface | Cadence PDK | Verilog-A |
| Supply voltage | 1.0 V | 0.71 V |

See [`MODEL_CONFIGURATION.md`](MODEL_CONFIGURATION.md) for the final VS-CNFET
parameters.

---

# Inverter Characterization

## Testbench Conditions

The inverter uses a transient pulse input and a **1 fF output load**.

| Parameter | 45nm CMOS | 7nm VS-CNFET |
|---|---:|---:|
| Logic low | 0 V | 0 V |
| Logic high | 1.0 V | 0.71 V |
| Period | 200 ps | 200 ps |
| Initial delay | 50 ps | 50 ps |
| Rise time | 10 ps | 10 ps |
| Fall time | 10 ps | 10 ps |
| Pulse width | 90 ps | 90 ps |
| Output load | 1 fF | 1 fF |

The pulse timing and output loading are identical. The logic-high voltage
changes according to the supply used by each technology.

---

## DC Characterization

The inverter input is swept to obtain the voltage-transfer characteristic
(VTC).

The DC characterization is used to evaluate quantities including:

- switching threshold `Vm`;
- `VIL`;
- `VIH`;
- low noise margin `NML`;
- high noise margin `NMH`;
- output swing.

Noise margins are defined as:

```text
NML = VIL - VOL
NMH = VOH - VIH
```

---

## Propagation Delay

Propagation delay is measured using the **50% voltage-crossing convention**.

### High-to-Low Delay

`tpHL` is measured between the 50% input crossing and the corresponding
50% high-to-low output crossing.

### Low-to-High Delay

`tpLH` is measured between the 50% input crossing and the corresponding
50% low-to-high output crossing.

Average propagation delay:

```text
tpd = (tpHL + tpLH) / 2
```

### Measured Inverter Delay

| Technology | `tpHL` | `tpLH` | Average `tpd` |
|---|---:|---:|---:|
| 45nm CMOS | 17.22 ps | 22.52 ps | 19.87 ps |
| 7nm VS-CNFET | 3.895 ps | 3.894 ps | 3.895 ps |

The delay ratio is:

```text
19.87 / 3.895 ≈ 5.1
```

---

## Peak Current

Peak transient current was extracted from the inverter simulation.

| Technology | Peak current |
|---|---:|
| 45nm CMOS | 41.1 µA |
| 7nm VS-CNFET | 493.4 µA |

The substantially larger simulated VS-CNFET peak current accompanies the
lower measured switching delay.

---

## Dynamic Power

Measured inverter dynamic power:

| Technology | Dynamic power |
|---|---:|
| 45nm CMOS | 5.953 µW |
| 7nm VS-CNFET | 7.337 µW |

The lower VS-CNFET delay therefore does not correspond to lower measured
dynamic power in this inverter configuration.

---

## Leakage Characterization

Leakage was evaluated at three DC operating points:

1. `Vin = 0`
2. `Vin = Vm`
3. `Vin = VDD`

| Bias condition | 45nm CMOS | 7nm VS-CNFET |
|---|---:|---:|
| `Vin = 0` | 9.47 pW | 20.20 pW |
| `Vin = Vm` | 537.93 nW | 107.75 µW |
| `Vin = VDD` | 3.47 pW | 20.20 pW |

The operating point is explicitly retained because midpoint current and
off-state leakage describe different device conditions.

---

## Power-Delay Product

Power-delay product is calculated as:

```text
PDP = Pavg × tpd
```

Measured inverter PDP:

| Technology | PDP |
|---|---:|
| 45nm CMOS | 118.29 aJ |
| 7nm VS-CNFET | 28.57 aJ |

---

# Full-Adder Characterization

## Functional Verification

The full-adder circuits implement:

```text
Sum  = A ⊕ B ⊕ Cin
Cout = AB + Cin(A ⊕ B)
```

The input waveforms exercise all eight combinations of:

```text
A, B, Cin
```

and the corresponding `Sum` and `Cout` waveforms are inspected using
transient simulation.

---

## 38T Static Full Adder

### Delay

| Technology | `tpHL` | `tpLH` | Average `tpd` |
|---|---:|---:|---:|
| 45nm CMOS | 22.57 ps | 26.78 ps | 24.67 ps |
| 7nm VS-CNFET | 8.302 ps | 9.243 ps | 8.773 ps |

Delay ratio:

```text
24.67 / 8.773 ≈ 2.81
```

### Power and Energy

| Metric | 45nm CMOS | 7nm VS-CNFET |
|---|---:|---:|
| Dynamic power | 1.573 µW | 11.80 µW |
| Static power | 137.99 pW | 262.86 nW |
| PDP | 38.80 aJ | 103.517 aJ |
| EDP | 957.3 × 10⁻³⁰ J·s | 908.2 × 10⁻³⁰ J·s |

---

## 10T PTL Full Adder

The 10T design consists of:

```text
8T differential XOR-MUX Sum network
+
2T Cout transmission-gate network
```

### Delay

| Technology | `tpHL` | `tpLH` | Average `tpd` |
|---|---:|---:|---:|
| 45nm CMOS | 18.806 ps | 18.775 ps | 18.791 ps |
| 7nm VS-CNFET | 7.648 ps | 12.632 ps | 10.14 ps |

Delay ratio:

```text
18.791 / 10.14 ≈ 1.85
```

### Power and Energy

| Metric | 45nm CMOS | 7nm VS-CNFET |
|---|---:|---:|
| Dynamic power | 184.23 nW | 784.96 nW |
| Static power | 45.50 pW | 80.87 nW |
| PDP | 3.462 aJ | 7.960 aJ |
| EDP | 65.05 × 10⁻³⁰ J·s | 80.71 × 10⁻³⁰ J·s |

---

# Derived Metrics

## Energy-Delay Product

Energy-delay product is calculated from energy and propagation delay:

```text
EDP = PDP × tpd
```

| Architecture | Technology | EDP |
|---|---|---:|
| 38T | 45nm CMOS | 957.3 × 10⁻³⁰ J·s |
| 38T | 7nm VS-CNFET | 908.2 × 10⁻³⁰ J·s |
| 10T | 45nm CMOS | 65.05 × 10⁻³⁰ J·s |
| 10T | 7nm VS-CNFET | 80.71 × 10⁻³⁰ J·s |

---

## Maximum-Frequency Estimate

The comparative frequency estimate is derived from average propagation delay:

```text
fmax = 1 / (2 × tpd)
```

This produces:

| Architecture | Technology | `fmax` estimate |
|---|---|---:|
| 38T | 45nm CMOS | 20.27 GHz |
| 38T | 7nm VS-CNFET | 56.99 GHz |
| 10T | 45nm CMOS | 26.61 GHz |
| 10T | 7nm VS-CNFET | 49.31 GHz |

This quantity is a **delay-derived comparative metric**.

It is not a post-layout timing-closure result and should not be interpreted
as the guaranteed clock frequency of a fabricated system.

---

# Output-Swing Measurements

Maximum measured Sum voltages:

| Architecture | Technology | `Vmax(Sum)` |
|---|---|---:|
| 38T | 45nm CMOS | 1.071 V |
| 38T | 7nm VS-CNFET | 759.95 mV |
| 10T | 45nm CMOS | 1.180 V |
| 10T | 7nm VS-CNFET | 828.17 mV |

Transient values above the nominal supply are reported as measured rather
than clipped to the rail.

Output swing is considered alongside delay and power because reduced-device
pass-transistor circuits can introduce signal-integrity tradeoffs.

---

# Topology Comparison

Changing from 38T to 10T substantially reduced measured dynamic power.

### 45nm CMOS

```text
1.573 µW / 184.23 nW ≈ 8.5×
```

### 7nm VS-CNFET

```text
11.80 µW / 784.96 nW ≈ 15×
```

Thus, in the evaluated circuits, **logic topology had a particularly strong
effect on dynamic power**, independently of the transistor technology.

---

## Scope

The published characterization covers:

- inverter;
- 38T static full adder;
- 10T PTL full adder.

Incomplete exploratory CLA and SRAM designs are outside the scope of the
reported results.

---

## Related Documentation

- [Main README](../README.md)
- [VS-CNFET Model Configuration](MODEL_CONFIGURATION.md)
- [References](REFERENCES.md)