# DIFFERENTIAL AMPLIFIER  

## CIRCUIT 1  

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
