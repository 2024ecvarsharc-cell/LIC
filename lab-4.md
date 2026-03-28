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

## AC Analysis  

```
BW = FH − FL = 7.21 Hz
```

```
UGB = Gain × BW = 74.47
```

---

# CIRCUIT 2  

## Description  

PMOS transistors act as active loads using a current mirror, improving gain and output resistance.

---

## Power Analysis  

```
P = (VDD − VSS) × ISS
  = 1.8 × ISS
ISS = 1 mA
```

---

## Current Distribution  

```
ID1 = ID2 = 0.5 mA
```

---

## Output Resistance  

```
ro = 1 / (λ × ID)
   = 20 kΩ
```

```
Rout = ro || ro
     = 10 kΩ
```

---

## Transconductance  

```
gm = 2ID / Vov
   = 4.17 mS
```

---

## Theoretical Gain  

```
Ad = gm × Rout
   = 41.7 V/V
```

```
Gain ≈ 32.4 dB
```

---

## ICMR  

```
VICM(min) = −0.34 V
VICM(max) = 0.39 V
```

---

## Practical Gain  

```
Av = 1.88
Gain ≈ 5.48 dB
```

---

## Differential Input Limit  

```
√2 × Vov ≈ 0.34 V
```

---

## AC Analysis  

```
BW = 3 GHz
```

```
UGB = 7.44 GHz
```

---

## Conclusion  

The resistive load differential amplifier provides moderate gain, while the active load configuration significantly improves gain due to increased output resistance. Theoretical and practical results are reasonably close, validating the design.

# CIRCUIT 3

---

## 3.1 Power Constraint Analysis

**Supply Voltage Differential:**

VDD - VSS = 0.9 - (-0.9) = 1.8 V  

**Power Equation:**

P = (VDD - VSS) × ISS  

1.8 × ISS ≤ 1.8 × 10^-3  

ISS ≤ 1 mA  

**Design Choice:**

ISS = 1 mA  

Power Dissipation = 1.8 mW  (Constraint satisfied)

---

## 3.2 Drain Current Calculation (ID)

Under balanced condition:

ID1 = ID2 = ISS / 2  
ID1 = ID2 = 0.5 mA  

---

## 3.3 Drain-Source Voltage (VDS)

VD = 0 V  
VP = -0.7 V  

VDS = VD - VP  
VDS = 0 - (-0.7) = 0.7 V  

---

## 3.4 Gate-Source and Overdrive Voltage

VG = 0 V  
VS = -0.7 V  

VGS = VG - VS = 0 - (-0.7) = 0.7 V  

VOV = VGS - VTH  
VOV = 0.7 - 0.36 = 0.34 V  

---

## 3.5 Saturation Region Verification

Condition:

VDS > VOV  

0.7 > 0.34  

→ Transistors are in **saturation region**

---

## 3.6 Tail Current Source Analysis (M5)

VDS5 = -0.7 - (-0.9) = 0.2 V  

VOV5 = 0.2 V  

VGS5 = VTH + VOV5  
VGS5 = 0.36 + 0.2 = 0.56 V  

VG5 = VGS5 + VS  
VG5 = 0.56 - 0.9 = -0.34 V  

---

## 3.7 Tail Transistor Width (W5)

W5 = (2 × ID × L) / (μnCox × VOV²)

W5 ≈ 104 µm  

---

## 3.8 NMOS Width (W1, W2)

W1 = W2 ≈ 18 µm  

---

## 3.9 PMOS Active Load Width (W3, W4)

W3 = W4 ≈ 44.8 µm  

---

## 3.10 Final Design Values (Simulation)

W(M1, M2) ≈ 22 µm  
W(M5) ≈ 194 µm  
W(M3, M4) ≈ 100 µm  

ID = 0.5 mA  
ISS = 1 mA  

---

## 3.11 Small Signal Analysis

### Transconductance (gm)

gm = 2ID / VOV  
gm = (2 × 0.5 mA) / 0.34  

gm ≈ 2.94 mS  

---

### Output Resistance (ro)

Assuming λ ≈ 0.04  

ro ≈ 1 / (λID) ≈ 50 kΩ  

Rout = ron || rop ≈ 25 kΩ  

---

### Differential Gain

Ad = -gm × Rout  

Ad = -2.94 mS × 25 kΩ  

Ad ≈ -73.5 V/V  

---

### Gain in dB

Gain = 20 log10(73.5)  

Gain ≈ 37.3 dB  

---

## 3.12 Output Voltage Swing

Vout(max) ≈ 0.9 - 0.3 = 0.6 V  
Vout(min) ≈ -0.9 + 0.3 = -0.6 V  

---

## 3.13 Input Common Mode Range (ICMR)

Vin(max) ≈ 0.9 V  

Vin(min) = -0.9 + 0.2 + 0.7 = 0 V  

ICMR: 0 V to 0.9 V  

---

## 3.14 Differential Input Limit

Vid(max) = √2 × VOV  

Vid(max) = 1.414 × 0.34 = 0.48 V  

- Linear: Vid < 0.48 V  
- Clipping: Vid > 0.48 V  

---

## 3.15 AC Analysis

### Bandwidth

BW = 1 / (2π × Rout × CL)  

BW = 1 / (2π × 25k × 10pF)  

BW ≈ 636 Hz  

---

### Unity Gain Bandwidth (UGB)

UGB = Gain × BW  

UGB = 73.5 × 636  

UGB ≈ 46.7 kHz  

---

## 3.16 Transient Analysis

- Differential input applied (180° phase shift)
- Outputs are **equal and opposite**
- Symmetrical waveform about 0 V
- No distortion if Vid < 0.48 V  

---

##  Conclusion

- High gain due to **PMOS active load (~37 dB)**
- Power constraint satisfied (**1.8 mW**)
- All transistors operate in **saturation**
- Trade-off:
  - High gain
  - Reduced bandwidth

---
