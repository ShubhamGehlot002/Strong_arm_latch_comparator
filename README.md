# Strong-Arm Latch Design in UMC 65nm CMOS

## Overview
This project implements a Strong-Arm Latch comparator using the UMC 65nm CMOS process. An SR latch is connected at the output stage to ensure that the output state changes on every clock cycle. The design uses an ideal clock source with controlled rise and fall times and includes an inverter chain before driving the comparator clock input.

---

# Design Specifications

| Parameter | Value |
|---|---|
| Technology | UMC 65nm CMOS |
| Comparator Type | Strong-Arm Latch |
| Output Stage | SR Latch |
| Clock Frequency | 100 MHz |
| Clock Rise Time | 40 ps |
| Clock Fall Time | 40 ps |
| Clock Conditioning | 2-stage inverter chain |

---

# Design Description

## Strong-Arm Latch Comparator
The Strong-Arm Latch is a dynamic comparator widely used in high-speed and low-power analog-to-digital converters (ADCs). It operates in two phases:

### Reset Phase
- Internal nodes are precharged.
- Output nodes are initialized.
- Tail current path remains inactive.

### Regeneration Phase
- Differential input voltage is amplified.
- Positive feedback regenerates the small voltage difference.
- Outputs resolve to full logic levels.

---

## SR Latch Integration
An SR latch is added at the output of the comparator to:

- Hold the comparator decision.
- Ensure stable digital outputs.
- Enable output transition during every clock cycle.

---

# Clock Generation

An ideal pulse clock source is used with:

- Frequency: 100 MHz
- Rise time: 40 ps
- Fall time: 40 ps

The clock signal is passed through a chain of two CMOS inverters before driving the comparator clock input. This helps in:

- Improving signal integrity
- Providing realistic clock buffering
- Reducing loading effects

---

# Simulation Results

## Transient Analysis
Transient simulations verify:

- Correct comparator operation
- Regeneration behavior
- Output switching characteristics
- SR latch functionality

### Expected Outputs
- Differential outputs switch according to the input polarity.
- Output is latched correctly for each clock cycle.

---

## Transient Noise Analysis
Transient noise simulations are performed to evaluate:

- Comparator sensitivity
- Noise-induced offset
- Decision reliability

The analysis helps determine the robustness of the latch under noisy operating conditions.

---

## Monte Carlo Analysis
Monte Carlo simulations are used to analyze process variations and mismatch effects.

Parameters evaluated include:

- Input-referred offset
- Output variability
- Regeneration reliability
- Device mismatch sensitivity

This validates the robustness of the design across manufacturing variations.

---

# Layout

The layout of the Strong-Arm Latch is implemented in UMC 65nm CMOS.

## Layout Considerations

- Symmetric differential structure
- Matched transistor placement
- Common-centroid techniques where applicable
- Reduced parasitic mismatch
- Proper routing for clock and output nodes

## Verification

The following verification steps should be completed:

- DRC (Design Rule Check)
- LVS (Layout Versus Schematic)
- Parasitic Extraction (PEX)

---

# Tools Used

Typical EDA tools used for this project may include:

- Cadence Virtuoso
- Spectre Simulator
- Assura / Pegasus / Calibre

---

# Folder Structure

```text
project/
│
├── schematic/
├── symbol/
├── simulations/
│   ├── transient/
│   ├── transient_noise/
│   └── monte_carlo/
├── layout/
├── extracted/
└── README.md
