# COMMON SOURCE AMPLIFIER

## Aim

To design and analyze a Common Source (CS) amplifier using LTSpice and perform DC, AC, and Transient analysis to extract parameters such as drain current, gain, bandwidth, and operating region.

---

## Introduction

A MOSFET (Metal Oxide Semiconductor Field Effect Transistor) can operate either as a switch or as an amplifier. Among the three configurations — Common Source (CS), Common Gate (CG), and Common Drain (CD) — the Common Source amplifier provides good voltage gain and introduces a 180° phase shift between input and output.

In a CS amplifier:
- Input is applied at the gate
- Output is taken from the drain
- Source is grounded

For proper amplification, the MOSFET must operate in the **saturation region**:

VDS ≥ VGS - VTH

![WhatsApp Image 2026-02-23 at 2 09 31 PM](https://github.com/user-attachments/assets/5ad249f5-6d4e-45b7-ad0a-7af5e1c0097c)


---

## Design Specifications

### Case 1 (Low Power Design)

- VDD = 1.8V  
- Power Budget = 50µW  
- Input = 50mV, 1kHz  
- VTH = 0.366V  

### Case 2 (Moderate Power Design)

- VDD = 2V  
- P ≤ 1.2mW  
- L = 180nm  
- CL = 0.7pF  
- VTH = 0.36V  
- VGS = 0.9V  

---

## Calculation

### 1. Drain Current

P = V × I  

For 50µW design:

I = 50µW / 1.8V  
I ≈ 27.7µA  

For 1.2mW design:

I = 1.2mW / 2V  
I = 0.6mA  

Practical chosen ID ≈ 200µA  

---

### 2. Drain Resistor

For maximum symmetrical swing:

Vout = VDD / 2  

RD = VDD / (2 × ID)  

For 2V design:

RD = 5kΩ  

For low power design:

RD = 25kΩ  

---

### 3. Width Selection

ID = (1/2) kn (VGS − VTH)^2  

VOV = 0.9 − 0.36 = 0.54V  

Initial W ≈ 1.07µm  
Adjusted W ≈ 1.377µm  

Low power case:
W = 785nm  
L = 800nm  

![WhatsApp Image 2026-02-23 at 5 36 57 PM](https://github.com/user-attachments/assets/ae5d8ca3-0549-43cd-b3ed-16e568521eed)

---

## DC Analysis

- ID matches design value  
- MOSFET operates in saturation  
- Increasing width increases current  
- Channel length modulation observed

![WhatsApp Image 2026-02-23 at 5 38 41 PM](https://github.com/user-attachments/assets/63d9c606-4efd-47fa-94d7-0c6dd879494d)

---

## Transient Analysis

Input:
- 50mV (low power)
- 10mV (moderate power)
- Frequency = 1kHz

Observations:
- Output amplified
- 180° phase shift
- Gain ≈ -2.6 (low power)
- Gain ≈ 2.7–3.7 (moderate power)

![WhatsApp Image 2026-02-23 at 5 37 39 PM](https://github.com/user-attachments/assets/b404c827-6b46-4a0b-b990-6d533e8889fb)

---

## AC Analysis

Small signal gain:

Av = -gm RD  

gm = 2ID / VOV  

Results:
- Gain ≈ -2.6 (low power)
- Gain ≈ 3.7 (moderate power)
- Bandwidth ≈ 1GHz (low power)
- Bandwidth ≈ 22.23GHz (moderate power)

![WhatsApp Image 2026-02-23 at 5 31 02 PM](https://github.com/user-attachments/assets/f69d51a8-e9e3-49c0-869d-17371f5f4384)

---

## Conclusion

Both CS amplifier designs satisfy their respective power constraints and operate in the saturation region. The amplifier provides voltage gain with a 180° phase shift. Gain depends on transconductance and drain resistance, while bandwidth is limited by parasitic capacitances.
