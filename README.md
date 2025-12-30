# CMOS XOR Gate Design – Cadence Virtuoso

## Project Overview
This project involves the **schematic design and simulation** of a **2-input CMOS XOR gate** using **Cadence Virtuoso Schematic Editor**. The focus is on analyzing the **DC transfer characteristics** and **transient response** of the circuit under different **transistor widths** and **temperature conditions** using **parametric analysis**.

---

## Tools & Technologies
- **Cadence Virtuoso Schematic Editor**
- **Cadence ADE (Analog Design Environment)**
- CMOS technology (gpdk90 - 90nm)
- Parametric Analysis (Sweep Width, Temperature)

---

## Design Specifications
- **Logic Function**:  Y = A.B + A.B
- **Inputs**: A, B (voltage sources)
- **Output**: Y
- **Technology**: CMOS (Complementary MOSFETs)
- **Simulations**: DC sweep, Transient analysis
- **Parametric Variations**:
  - Transistor widths (Wp/Wn) - (120nm / 120nm) , (240nm / 120nm) , (360nm / 120nm) , (480nm / 120nm) , (600nm / 120nm)
  - Temperature: e.g., -40°C, 27°C, 120°C

<img width="1042" height="745" alt="Truth-Table" src="https://github.com/user-attachments/assets/74137a69-ba3e-46ca-8964-2853846e4fd2" />
<img width="866" height="957" alt="reference-circuit" src="https://github.com/user-attachments/assets/40f567a1-0c00-4b8e-b9eb-e24076cb79f4" />


---

## Circuit Schematic

The following schematic shows the CMOS implementation of a 2-input XOR gate using complementary pull-up and pull-down networks:
Figure: CMOS XOR gate schematic drawn in Cadence Virtuoso.
<img width="1120" height="666" alt="XOR_Schematic" src="https://github.com/user-attachments/assets/f64d4cb6-b7f3-47c6-b497-3bf6e27acb35" />

)

Inputs:
  - A <img width="510" height="719" alt="A_input" src="https://github.com/user-attachments/assets/ffada96a-04c3-46e2-9611-07ca22a313ed" />

  - B <img width="505" height="714" alt="B_input" src="https://github.com/user-attachments/assets/0f7a5578-548f-4901-8aaa-9b1784731d37" />


---

##  Simulations Performed

### **DC Transfer Characteristics**

 Setup (ADE L)

-   The DC analysis was configured using Cadence ADE L, with a parametric sweep for:

-   Input voltage: either A or B swept from 0V to VDD
-   Temperature: -40°C, 27°C, 120°C
-   PMOS widths: from 120 nm to 600 nm in steps of 120 nm

-   The simulation aimed to analyze the output voltage behavior of the XOR gate under different scenarios.
-   <img width="691" height="509" alt="window" src="https://github.com/user-attachments/assets/a2d36c69-bcd1-4dac-b8a2-d72952f76b11" />


*Sweep on Input A*

-   Input A: swept from 0V to 1V
-   Input B: held constant at 0V
-   This simulates the XOR logic behavior for 0 XOR A
-   The output exhibits expected rising behavior as input A transitions from logic 0 to logic 1
-  <img width="1716" height="837" alt="varA" src="https://github.com/user-attachments/assets/5ed3837a-4916-4d79-9fec-d7c2152da254" />


*Sweep on Input B*

-   Input A: held constant at 0V
-   Input B: swept from 0V to 1V
-   This simulates the XOR logic behavior for A XOR 0 (same as above due to symmetry)
-   Output characteristics are similar to the previous case with consistent logic swing
-  <img width="1714" height="834" alt="varB" src="https://github.com/user-attachments/assets/077da002-3e44-4912-b381-e5923f4090c2" />


### Transient Analysis

**Setup**

-   **Input Sources**: vpulse sources were used to generate digital transitions for XOR inputs.

-   **A**: 100 ns pulse width, 50 ps rise/fall time
-   **B**: 50 ns pulse width, 50 ps rise/fall time

-   The XOR gate's dynamic behavior was observed through the resulting output waveform.
-   **Simulation Type**: Transient analysis using **Cadence ADE L**\
<img width="698" height="504" alt="ADE" src="https://github.com/user-attachments/assets/f2860b55-4533-4be2-a735-a7cdfbfad4d1" />


* * * * *

**Parametric Simulation Setup**

-   Parametric sweep configured in ADE L to vary:

-   **PMOS widths**: 120 nm to 600 nm in steps of 120 nm
-   **Temperature**: -40°C, 27°C, and 120°C

-   This setup allows observation of performance variation under different PVT conditions.\
<img width="703" height="507" alt="Screenshot 2025-04-16 170846" src="https://github.com/user-attachments/assets/6f08b06c-93fa-44fa-8abd-96039de23a05" />



* * * * *

**Transient Response (Baseline)**

-   Output waveform for XOR gate showing expected toggling behavior based on pulse inputs.\
<img width="1712" height="839" alt="120" src="https://github.com/user-attachments/assets/0f8374d3-96de-4512-9902-02af046840ae" />


* * * * *

**Effect of PMOS Width Variation**

-   PMOS widths varied from 120 nm to 600 nm.
-   Minor improvement in **rise time** with increased PMOS width; otherwise, output remained consistent.\
*Figure: XOR output response for different PMOS sizes.<img width="1918" height="881" alt="VaryingWidth" src="https://github.com/user-attachments/assets/cf2c6bcc-585e-4622-9ddb-494603961f90" />


* * * * *

**Effect of Temperature Variation**

-   Temperature swept across -40°C, 27°C, and 120°C.
-   Output waveform shows minimal impact on delay or voltage swing, indicating thermal stability.\
*Figure: XOR transient response across temperature range.* <img width="1717" height="851" alt="graphop" src="https://github.com/user-attachments/assets/6dbb4538-f250-4767-8c8f-1dce96b972e0" />


---

## Results and Observations

**1\. Transient Response for Different Temperatures**

**Setup:**

-   CMOS XOR gate simulated using transient analysis in Cadence Virtuoso.
-   Input pulses applied with 1V supply.
-   Temperature varied across **-40°C**, **27°C**, and **120°C**.

**Observation:**

-   The output waveform remained functionally consistent across all three temperature points.
-   **Propagation delay** and **rise/fall times** exhibited **negligible variation**, indicating good temperature stability in the design.
-   No significant degradation in output voltage levels or timing observed.

**Inference:**

-   The CMOS XOR gate demonstrates **temperature robustness** across standard PVT corners. This implies that the performance of the logic circuit is relatively unaffected by temperature within the tested range.

---

**2\. Transient Response for Varying PMOS Widths**

**Setup:**

-   Width of PMOS transistors was swept from **120 nm** to **600 nm** in steps of 120 nm.
-   NMOS width kept constant.
-   Transient simulations run for each sizing configuration.

**Observation:**

-   Output voltage levels and logic functionality remained consistent.
-   Only **minimal changes in rise time** were observed as PMOS width increased.
-   No observable impact on fall time or output amplitude.

**Inference:**

-   Increasing PMOS width in the tested range did not significantly impact XOR gate performance.
-   This suggests that beyond a certain sizing point, further increasing PMOS width offers **diminishing returns**, especially in standard-load digital applications.
-   Sizing optimization should consider area and power trade-offs, as performance gains are minimal.

---

##  How to Run

1. Open Cadence Virtuoso.
2. Load GPDK 90nm library.
3. Open XOR schematic from `schematic/`.
4. Launch ADE and create testbench.
5. Choose analysis type:
   - **DC Analysis** (sweep input)
   - **Transient Analysis** (using `vpulse`)
6. Use **Tools > Parametric Analysis** for:
   - Varying transistor widths
   - Temperature sweep
7. Run and observe waveforms.


---

## Acknowledgements

This project was made possible through the support, tools, and guidance provided by various individuals and institutions. I would like to express my sincere gratitude to:
-   **Team members:** Pratyush Kumar , Ashmit Garg 
-   **Cadence Design Systems**, for providing the industry-standard tools used for schematic design and simulation.
-   **Punjab Engineering College ,Chandigarh**, for the academic environment and resources that supported this work.
-   **Department of Electronics and Communication Engineering**, PEC - for enabling access to simulation tools and lab resources.

---

 ##  References
 
- CMOS Digital Integrated Circuits - Analysis and Design, S. Kang and Y. Leblebici, Tata McGraw Hill 3rd ed. 
- CMOS Digital VLSI Design By Prof. Sudeb Dasgupta, IIT Roorkee (https://archive.nptel.ac.in/noc/courses/noc21/SEM1/noc21-ee09/)
- [Virtuoso Guide | Cadence](https://docs.virtuoso.qa/guide/)
- [gpdk90 docs | Princeton](https://www.princeton.edu/~nverma/cadenceSetup_6.1.7/gpdk090_v4.4/docs/gpdk090_spec.pdf)

---
