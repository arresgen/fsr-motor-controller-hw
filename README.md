# Op-Amp & Comparator Controller Board

A KiCad hardware design project featuring an operational amplifier signal conditioning circuit and comparator-driven DC motor and LED indicator control.

---

## Technical Specifications & Features

* **Primary Supply Voltage:** +5V DC
* **Operational Amplifier:** Texas Instruments LM358 (Dual Low-Power Op-Amp)
* **Comparator:** Texas Instruments LM393 (Dual Low-Power Comparator)
* **Sensor Connector:** JST-EH 2-Pin header labeled for Force Sensitive Resistor (FSR402)
* **Actuator Output:** Transistor-driven (2N2222 NPN) DC Motor driver stage with flyback diode protection (1N4007)
* **Visual Indicator:** LED status circuit (D1) driven via comparator thresholding
* **Test Points:** Dedicated test points (`TP1` through `TP6`) for signal probing and hardware validation
* **Form Factor:** Compact 2-layer PCB (50.8 mm x 76.2 mm / KiCad 10.0 standard layer stack)[cite: 2]

---

## Circuit Overview

1. **Input Stage:** The input signal connects via connector `J1` (FSR402 sensor). Resistors `R1` (1.5k) and `R2` (10k) provide biasing and initial signal division.
2. **Amplification & Conditioning Stage (LM358):** Unit `U1` buffers and amplifies the analog input signal. Potentiometer `RV1` (10k) allows adjustable gain/reference tuning.
3. **Thresholding & Comparison Stage (LM393):** Dual comparator `U2` compares the processed signal against adjustable resistor network references (`R3` 100k, `R4` 6.8k).
4. **Output Driver Stage:**
   * **LED Drive:** Open-collector output drives status LED `D1` through limiting resistor `R6` (4.7k).
   * **Motor Drive:** Comparator output switches NPN transistor `Q2` (2N2222) via base resistor `R7` (100Ω) to power DC Motor `M1`. Free-wheeling diode `D2` (1N4007) suppresses inductive voltage spikes.

---

## Component List (BOM)

| Reference | Value / Part | Description | Footprint / Package |
| :--- | :--- | :--- | :--- |
| **U1** | LM358 | Low-Power Dual Op-Amp | DIP-8 Socket |
| **U2** | LM393 | Dual Voltage Comparator | DIP-8 Socket |
| **Q2** | 2N2222 | General Purpose NPN Transistor | TO-92L Inline Wide |
| **D1** | LED | Status Indicator | JST-EH 2-Pin / THT |
| **D2** | 1N4007 | 1000V 1A Rectifier Diode | DO-41 Horizontal |
| **M1** | Motor_DC | DC Motor Output | JST-EH 2-Pin Header |
| **J1** | FSR402 | Sensor Connector Input | JST-EH 2-Pin Vertical |
| **J2** | DC Source | +5V / GND Power Input | JST-EH 2-Pin Vertical |
| **RV1** | 10k | Potentiometer | JST-EH 3-Pin / Trim Pot |
| **R1** | 1.5k | Axial Resistor, 1/4W | DIN0207 (10.16mm Pitch) |
| **R2, R5** | 10k, 1k | Axial Resistors, 1/4W | DIN0207 (10.16mm Pitch) |
| **R3, R4** | 100k, 6.8k | Axial Resistors, 1/4W | DIN0207 (10.16mm Pitch) |
| **R6, R7** | 4.7k, 100 | Axial Resistors, 1/4W | DIN0207 (10.16mm Pitch) |
| **C1 - C5** | 100n / 22n | Ceramic Disc Decoupling Capacitors | Disc D5.0mm / P5.00mm |

---

## Test Point Reference

* **TP1:** Input signal node post-FSR biasing stage
* **TP2:** Non-inverting operational amplifier stage output/input node
* **TP3:** Voltage reference/bias node
* **TP4:** Comparator output signal node
* **TP5:** Secondary op-amp output stage
* **TP6:** Motor drive / low-side control node

---

## Project Structure

```text
.
├── fsr-motor-controller-hw.kicad_sch    # Schematic Source File
├── fsr-motor-controller-hw.kicad_pcb    # PCB Layout Source File
└── README.md                                  # Documentation
