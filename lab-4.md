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

Under balanced conditions (Vin1 = Vin2), the tail current splits equally:

```
ID1 = ID2 = ISS / 2
```

Power relation:

```
P = (VDD - VSS) × ISS
```

Output voltage:

```
Vout = VDD - (ID × RD)
```

```
0 = 0.9 - (0.5mA × RD)
RD = 1.8kΩ
```

---

## NMOS Width Calculation  

Oxide capacitance:

```
Cox = (εr × ε0) / tox
```

Overdrive voltage:

```
Vov = VGS - VTH
```

Drain current equation:

```
ID = (1/2) μn Cox (W/L) (Vov)^2
```

Width calculation:

```
W = (2 × ID × L) / (μn Cox (Vov)^2)
```

Final value:

```
Wn ≈ 19.9 µm
```

---

## Input Common Mode Range (ICMR)  

Maximum input:

```
Vin(max) = VDD - (ID × RD) + VTH
```

Minimum input:

```
Vin(min) = VSS + VDS(sat) + VGS
```

- Vin(max) = 0.36 V  
- Vin(min) ≈ -0.9 V  

✔ Range: **-0.9 V to 0.36 V**

---

## Output Common Mode Limits  

```
Voc(max) = VDD
```

```
Voc(min) = VDD - (ID × RD)
```

---

## Small Signal Gain  

Transconductance:

```
gm = 2ID / Vov
```

Gain:

```
Ad = -gm × RD
```

Output equation:

```
Vout1 - Vout2 = -gm × RD × Vid
```

Result:

```
Ad ≈ -5.29 V/V
Gain ≈ 14.46 dB
```

---

## Practical Gain  

```
Av = Vout(p-p) / Vin(p-p)
```

```
Gain(dB) = 20 log10(Av)
```

---

## Differential Input Operation  

### Linear Region  

```
|Vid| < √2 × Vov
```

Current equations:

```
ID1 = (ISS / 2) + (gm × Vid / 2)
ID2 = (ISS / 2) - (gm × Vid / 2)
```

✔ Both transistors ON  
✔ Linear amplification  

---

### Clipping Region  

```
|Vid| > √2 × Vov
```

✔ One transistor OFF  
✔ Output clipped  

---

## AC Analysis  

```
BW = FH - FL
```

```
UGB = Gain × BW
```

---

# CIRCUIT 2  

## Description  

PMOS transistors act as active loads using a current mirror, improving gain and output resistance.

---

## Design Specifications  

- VDD = +0.9 V  
- VSS = -0.9 V  
- Power ≤ 1.8 mW  
- Channel Length = 480 nm  
- VinCM = 0 V  
- VoCM = 0 V  
- VP = -0.7 V  
- CL = 10 pF  

---

## Power Analysis  

```
P = (VDD - VSS) × ISS
```

```
1.8V × ISS ≤ 1.8mW
ISS = 1mA
```

---

## Current Distribution  

```
ID1 = ID2 = ISS / 2 = 0.5mA
```

---

## Transistor Operation  

Voltage relations:

```
VGS = VG - VS
```

```
VDS = VD - VS
```

```
VSD = VS - VD
```

Saturation conditions:

```
NMOS: VDS ≥ Vov
PMOS: VSD ≥ Vov
```

---

## Theoretical Gain  

Output resistance:

```
ro = 1 / (λ × ID)
```

Parallel resistance:

```
Rout = ron || rop
```

Transconductance:

```
gm = 2ID / Vov
```

Gain:

```
Ad = gm × Rout
```

---

## ICMR Range  

```
VICM(min) = VS + VTH
```

```
VICM(max) = VD + VTH
```

---

## Practical Gain  

```
Av = Vout(p-p) / Vin(p-p)
```

```
Gain(dB) = 20 log10(Av)
```

---

## Differential Input Condition  

```
|Vid| < √2 × Vov
```

✔ Linear output  

---

## Clipping Condition  

```
|Vid| > √2 × Vov
```

✔ Non-linear output  

---

## AC Analysis  

```
BW = FH - FL
```

```
UGB = Gain × BW
```

---
