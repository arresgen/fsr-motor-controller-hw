# Op-Amp & Comparator Controller Board

A KiCad hardware design project featuring an operational amplifier signal conditioning circuit and comparator-driven DC motor and LED indicator control.

---

## Technical Specifications & Features

* **Primary Supply Voltage:** +5V DC[cite: 1]
* **Operational Amplifier:** Texas Instruments LM358 (Dual Low-Power Op-Amp)[cite: 1]
* **Comparator:** Texas Instruments LM393 (Dual Low-Power Comparator)[cite: 1]
* **Sensor Connector:** JST-EH 2-Pin header labeled for Force Sensitive Resistor (FSR402)[cite: 1, 2]
* **Actuator Output:** Transistor-driven (2N2222 NPN) DC Motor driver stage with flyback diode protection (1N4007)[cite: 1]
* **Visual Indicator:** LED status circuit (D1) driven via comparator thresholding[cite: 1, 2]
* **Test Points:** Dedicated test points (`TP1` through `TP6`) for signal probing and hardware validation[cite: 1, 2]
* **Form Factor:** Compact 2-layer PCB (50.8 mm x 76.2 mm / KiCad 10.0 standard layer stack)[cite: 2]

---

## Circuit Overview

1. **Input Stage:** The input signal connects via connector `J1` (FSR402 sensor)[cite: 1, 2]. Resistors `R1` (1.5k) and `R2` (10k) provide biasing and initial signal division[cite: 1].
2. **Amplification & Conditioning Stage (LM358):** Unit `U1` buffers and amplifies the analog input signal[cite: 1]. Potentiometer `RV1` (10k) allows adjustable gain/reference tuning[cite: 1].
3. **Thresholding & Comparison Stage (LM393):** Dual comparator `U2` compares the processed signal against adjustable resistor network references (`R3` 100k, `R4` 6.8k)[cite: 1].
4. **Output Driver Stage:**
   * **LED Drive:** Open-collector output drives status LED `D1` through limiting resistor `R6` (4.7k)[cite: 1, 2].
   * **Motor Drive:** Comparator output switches NPN transistor `Q2` (2N2222) via base resistor `R7` (100Ω) to power DC Motor `M1`[cite: 1]. Free-wheeling diode `D2` (1N4007) suppresses inductive voltage spikes[cite: 1].

---

## Component List (BOM)

| Reference | Value / Part | Description | Footprint / Package |
| :--- | :--- | :--- | :--- |
| **U1** | LM358[cite: 1] | Low-Power Dual Op-Amp[cite: 1] | DIP-8 Socket[cite: 1, 2] |
| **U2** | LM393[cite: 1] | Dual Voltage Comparator[cite: 1] | DIP-8 Socket[cite: 1, 2] |
| **Q2** | 2N2222[cite: 1] | General Purpose NPN Transistor[cite: 1] | TO-92L Inline Wide[cite: 1, 2] |
| **D1** | LED[cite: 1] | Status Indicator[cite: 1] | JST-EH 2-Pin / THT[cite: 1, 2] |
| **D2** | 1N4007[cite: 1] | 1000V 1A Rectifier Diode[cite: 1] | DO-41 Horizontal[cite: 1, 2] |
| **M1** | Motor_DC[cite: 1] | DC Motor Output[cite: 1] | JST-EH 2-Pin Header[cite: 1, 2] |
| **J1** | FSR402[cite: 1] | Sensor Connector Input[cite: 1] | JST-EH 2-Pin Vertical[cite: 1, 2] |
| **J2** | DC Source[cite: 1] | +5V / GND Power Input[cite: 1] | JST-EH 2-Pin Vertical[cite: 1, 2] |
| **RV1** | 10k[cite: 1] | Potentiometer[cite: 1] | JST-EH 3-Pin / Trim Pot[cite: 1, 2] |
| **R1** | 1.5k[cite: 1] | Axial Resistor, 1/4W[cite: 1, 2] | DIN0207 (10.16mm Pitch)[cite: 1, 2] |
| **R2, R5** | 10k, 1k[cite: 1] | Axial Resistors, 1/4W[cite: 1, 2] | DIN0207 (10.16mm Pitch)[cite: 1, 2] |
| **R3, R4** | 100k, 6.8k[cite: 1] | Axial Resistors, 1/4W[cite: 1, 2] | DIN0207 (10.16mm Pitch)[cite: 1, 2] |
| **R6, R7** | 4.7k, 100[cite: 1] | Axial Resistors, 1/4W[cite: 1, 2] | DIN0207 (10.16mm Pitch)[cite: 1, 2] |
| **C1 - C5** | 100n / 22n[cite: 1] | Ceramic Disc Decoupling Capacitors[cite: 1, 2] | Disc D5.0mm / P5.00mm[cite: 1, 2] |

---

## Test Point Reference

* **TP1:** Input signal node post-FSR biasing stage[cite: 1, 2]
* **TP2:** Non-inverting operational amplifier stage output / input node[cite: 1, 2]
* **TP3:** Voltage reference / bias node[cite: 1, 2]
* **TP4:** Comparator output signal node[cite: 1, 2]
* **TP5:** Secondary op-amp output stage[cite: 1, 2]
* **TP6:** Motor drive / low-side control node[cite: 1, 2]

---

## Project Structure

```text
.
├── Midterm Project - Op Amp - v2.kicad_sch    # Schematic Source File
├── Midterm Project - Op Amp - v2.kicad_pcb    # PCB Layout Source File
└── README.md                                  # Documentation
