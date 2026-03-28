# DIFFERENTIAL AMPLIFIER  


### Aim:  
**"Design and analysis of the MOS differential amplifier circuit for the following specifications."**  

---

## Given Specifications  

- Drain Supply Voltage (VDD): 0.9 V  
- Source Supply Voltage (VSS): -0.9 V  
- Maximum Power Dissipation: ≤ 1.8 mW  
- Input Common Mode Voltage (VinCM): 0 V  
- Output Common Mode Voltage (VoCM): 0 V  
- Tail Node Voltage (VP): -0.7 V  
- Load Capacitance (CL): 10 pF  
- Channel Length: 480 nm  

---

## CIRCUIT 1  


<img width="2220" height="1246" alt="image" src="https://github.com/user-attachments/assets/a35f54ab-1f84-461a-9a05-20f883b1ca53" />


## DC Analysis  

### Tail Current Calculation (ISS)  

The total power consumed by the differential amplifier is limited to 1.8 mW.

```
P = (VDD − VSS) × ISS
```

Substituting values:

```
1.8 × 10^-3 = 1.8 × ISS
ISS = 1 × 10^-3 A = 1 mA
```

---

### Current Distribution  

Under balanced conditions:

```
ID1 = ID2 = ISS / 2
     = 1 mA / 2
     = 0.5 mA
```

---

### Output Voltage and Load Resistance  

```
Vout = VDD − (ID × RD)
0 = 0.9 − (0.5 mA × RD)
RD = 1.8 kΩ
```

---

## NMOS Width Calculation  

### Oxide Capacitance  

```
Cox = (εr × ε0) / tox
     = (3.9 × 8.854 × 10^-12) / (4.1 × 10^-9)
     = 8.42 × 10^-3 F/m²
```

---

### Overdrive Voltage  

```
Vov = VGS − VTH
     = 0.7 − 0.36
     = 0.34 V
```

---

### Width Calculation  

```
ID = (1/2) μn Cox (W/L) (Vov)^2
```

```
W = (2 × ID × L) / (μn Cox (Vov)^2)
  ≈ 19.9 µm
```

![WhatsApp Image 2026-03-28 at 11 42 19 PM (1)](https://github.com/user-attachments/assets/a92d274b-5ba7-4667-87c7-062cde330c7f)


---

## Input Common Mode Range (ICMR)  

### Maximum Input  

```
Vin(max) = VDD − (ID × RD) + VTH
         = 0.9 − 0.9 + 0.36
         = 0.36 V
```

---

### Minimum Input  

```
Vin(min) = VSS + VDS(sat) + VGS
         = −0.9 + 0.2 + 0.7
         ≈ 0 V
```

Operating range: −0.9 V to 0.36 V  

---

For linear amplification, input common-mode signal must stay between -0.9V and +0.36V.

<img width="1281" height="1339" alt="image" src="https://github.com/user-attachments/assets/06acd803-1445-4497-ab80-153ba4b47cb8" />

---

if we increase the vin values then graph will be clipped( square form)

<img width="1255" height="1311" alt="image" src="https://github.com/user-attachments/assets/2c0c6003-2fa6-42b1-bc26-6fbd8c22b9ec" />


## Output Common Mode  

```
Voc(max) = VDD = 0.9 V
```

```
Voc(min) = VDD − (ID × RD)
         = 0 V
```

---

## Small Signal Gain  

### Transconductance  

```
gm = 2ID / Vov
   = 2.94 mS
```

---

### Differential Gain  

```
Ad = −gm × RD
   = −5.29 V/V
```

---

### Gain in dB  

```
Gain = 20 log10(5.29)
     ≈ 14.46 dB
```

---

## Practical Gain  

```
Av = Vout(p-p) / Vin(p-p)
   = 1204 / 200
   = 6.02
```

```
Gain ≈ 15.59 dB
```

---

## Differential Input Condition  

```
√2 × Vov = 1.414 × 0.34 ≈ 0.48 V
```

- Linear: Vid < 0.48 V  
- Clipping: Vid > 0.48 V  

---

<img width="1281" height="1339" alt="image" src="https://github.com/user-attachments/assets/336c2e00-c27b-4e55-8cc2-ab254a3adef3" />

---

## AC Analysis  

```
BW = FH − FL = 7.21 Hz
```

```
UGB = Gain × BW = 74.47
```

##  Conclusion

The differential amplifier satisfies the power constraint with ISS = 1 mA and operates properly in saturation. It achieves a moderate gain of around 14–15 dB with balanced current distribution.

However, the circuit has a limited input range and very low bandwidth (7.21 Hz), resulting in poor high-frequency performance. Hence, while simple and power-efficient, it is not suitable for high-gain or high-speed applications.

---

# CIRCUIT 2 – Differential Amplifier with Active Load

---

<img width="1187" height="853" alt="image" src="https://github.com/user-attachments/assets/5787bd37-91bf-4d03-aaa5-0db31fa9399d" />


---

## DC Analysis

### Tail Current Calculation (ISS)

The total power consumption is limited to **1.8 mW**.

P = (VDD − VSS) × ISS  

1.8 × 10^-3 = 1.8 × ISS  

ISS = 1 mA  

---

### Current Distribution

Under balanced conditions:

ID1 = ID2 = ISS / 2  
     = 1 mA / 2  
     = 0.5 mA  

---

### Output Resistance

ro = 1 / (λ × ID)  
   = 1 / (0.1 × 0.5 × 10^-3)  
   = 20 kΩ  

Rout = ro || ro  
     = 10 kΩ  

---

<img width="846" height="633" alt="image" src="https://github.com/user-attachments/assets/99d41676-1e90-4937-9718-35115be1318f" />

<img width="853" height="209" alt="image" src="https://github.com/user-attachments/assets/da5120e5-1458-40af-9473-5ed6df8b4cfd" />

---

### Output Voltage and Load Behavior

PMOS transistors act as **active loads (current mirror)** instead of resistors.

- Provides high output resistance  
- Improves voltage gain  
- Converts differential output to single-ended output  
- Suitable for integrated circuit implementation  

---

### Transconductance (gm)

gm = 2ID / Vov  
   = (2 × 0.5 mA) / 0.24  
   = 4.17 mS  

---

## Small Signal Gain

### Differential Gain

Ad = gm × Rout  
   = 4.17 mS × 10 kΩ  
   = 41.7 V/V  

---

<img width="958" height="848" alt="image" src="https://github.com/user-attachments/assets/c1e506e7-9fd0-430f-b69b-d2f02ce370b2" />

---

### Gain in dB

Gain = 20 log10(41.7)  
     ≈ 32.4 dB  

---

### Practical Gain

Av = 1.88  

Gain ≈ 5.48 dB  

> Note: Practical gain is lower due to non-ideal effects such as channel length modulation, parasitic capacitances, and current mirror mismatch.

---

## Input Common Mode Range (ICMR)

VICM(min) = −0.34 V  
VICM(max) = 0.39 V  

Operating range: **−0.34 V to 0.39 V**

---

## Differential Input Condition

√2 × Vov ≈ 0.34 V  

- Linear Region: Vid < 0.34 V  
- Clipping Region: Vid > 0.34 V  

---

## Output Common Mode

Voc(max) ≈ VDD = 0.9 V  

Voc(min) ≈ limited by saturation conditions  

---

<img width="1264" height="1009" alt="image" src="https://github.com/user-attachments/assets/fc32ac50-43fe-40c3-8e87-a9c92748f8bd" />


---

## AC Analysis

BW = 3 GHz  

UGB = Gain × BW  
    = 7.44 GHz  

---

<img width="959" height="849" alt="image" src="https://github.com/user-attachments/assets/2e0a4bd7-020d-4e8e-ad86-a656d9434edb" />


<img width="960" height="845" alt="image" src="https://github.com/user-attachments/assets/381daee8-950f-4b30-9abc-dd3482c9ece8" />


---

## Conclusion  

The resistive load differential amplifier provides moderate gain, while the active load configuration significantly improves gain due to increased output resistance. Theoretical and practical results are reasonably close, validating the design.

# CIRCUIT 3 – Differential Amplifier with Active Load and Tail Current Source

<img width="825" height="653" alt="image" src="https://github.com/user-attachments/assets/7a18eabd-8ddf-4669-a780-2702dbf11e46" />

---

## DC Analysis

### Power Constraint Analysis

Supply voltage difference:

VDD − VSS = 0.9 − (−0.9) = 1.8 V  

Power equation:

P = (VDD − VSS) × ISS  

1.8 × ISS ≤ 1.8 × 10^-3  

ISS ≤ 1 mA  

Design choice:

ISS = 1 mA  

Power Dissipation = 1.8 mW (Constraint satisfied)  

---

### Current Distribution

Under balanced condition:

ID1 = ID2 = ISS / 2  
     = 1 mA / 2  
     = 0.5 mA  

---

### Drain-Source Voltage (VDS)

VD = 0 V  
VP = −0.7 V  

VDS = VD − VP  
     = 0 − (−0.7)  
     = 0.7 V  

---

### Gate-Source and Overdrive Voltage

VG = 0 V  
VS = −0.7 V  

VGS = VG − VS  
     = 0 − (−0.7)  
     = 0.7 V  

VOV = VGS − VTH  
     = 0.7 − 0.36  
     = 0.34 V  

---

### Saturation Region Verification

Condition:

VDS > VOV  

0.7 > 0.34  

→ Transistors operate in saturation region  

---

### Tail Current Source Analysis (M5)

VDS5 = −0.7 − (−0.9)  
     = 0.2 V  

VOV5 = 0.2 V  

VGS5 = VTH + VOV5  
     = 0.36 + 0.2  
     = 0.56 V  

VG5 = VGS5 + VS  
     = 0.56 − 0.9  
     = −0.34 V  

---

### Transistor Sizing

#### Tail Transistor Width (W5)

W5 = (2 × ID × L) / (μnCox × VOV²)  

W5 ≈ 104 µm  

---

#### NMOS Width (W1, W2)

W1 = W2 ≈ 18 µm  

---

#### PMOS Active Load Width (W3, W4)

W3 = W4 ≈ 44.8 µm  

---

<img width="858" height="622" alt="image" src="https://github.com/user-attachments/assets/531b00d5-b99f-48ce-908c-5c58dc0e45fa" />

<img width="851" height="292" alt="image" src="https://github.com/user-attachments/assets/3f375a67-08b7-401a-9f9d-9a568ef6f60e" />

---

### Final Design Values (Simulation)

W(M1, M2) ≈ 22 µm  
W(M5) ≈ 194 µm  
W(M3, M4) ≈ 100 µm  

ID = 0.5 mA  
ISS = 1 mA  

---

## Small Signal Analysis

### Transconductance (gm)

gm = 2ID / VOV  
   = (2 × 0.5 mA) / 0.34  

gm ≈ 2.94 mS  

---

### Output Resistance (ro)

ro ≈ 1 / (λ × ID)  
   = 1 / (0.04 × 0.5 × 10^-3)  

ro ≈ 50 kΩ  

Rout = ron || rop  
     ≈ 25 kΩ  

---

### Differential Gain

Ad = −gm × Rout  
   = −2.94 mS × 25 kΩ  

Ad ≈ −73.5 V/V  

---

### Gain in dB

Gain = 20 log10(73.5)  

Gain ≈ 37.3 dB  

---

## Output Voltage Swing

Vout(max) ≈ 0.9 − 0.3 = 0.6 V  

Vout(min) ≈ −0.9 + 0.3 = −0.6 V  

---

## Input Common Mode Range (ICMR)

Vin(max) ≈ 0.9 V  

Vin(min) = −0.9 + 0.2 + 0.7  
         = 0 V  

Operating range: **0 V to 0.9 V**  

---

## Differential Input Condition

Vid(max) = √2 × VOV  
         = 1.414 × 0.34  
         ≈ 0.48 V  

- Linear Region: Vid < 0.48 V  
- Clipping Region: Vid > 0.48 V  


---

## AC Analysis

### Bandwidth

BW = 1 / (2π × Rout × CL)  

BW = 1 / (2π × 25k × 10pF)  

BW ≈ 636 Hz  

---

<img width="960" height="846" alt="image" src="https://github.com/user-attachments/assets/7896a709-ba9c-49ce-a4dd-b3275005ce36" />

<img width="958" height="848" alt="image" src="https://github.com/user-attachments/assets/4f5bd447-ec81-4fec-ab19-20a777fff7cb" />

---

### Unity Gain Bandwidth (UGB)

UGB = Gain × BW  

UGB = 73.5 × 636  

UGB ≈ 46.7 kHz  

---

## Transient Analysis

- Differential input applied with 180° phase shift  
- Outputs are equal and opposite  
- Waveform is symmetrical about 0 V  
- No distortion when Vid < 0.48 V

---

<img width="1282" height="1289" alt="image" src="https://github.com/user-attachments/assets/9ccb0d8c-ff0b-4d57-8691-c11b2f34805e" />

<img width="1280" height="1366" alt="image" src="https://github.com/user-attachments/assets/3da42f81-0c34-4326-a454-f9966b197e21" />

---

##  Conclusion

- High gain due to **PMOS active load (~37 dB)**
- Power constraint satisfied (**1.8 mW**)
- All transistors operate in **saturation**
- Trade-off:
  - High gain
  - Reduced bandwidth

---
