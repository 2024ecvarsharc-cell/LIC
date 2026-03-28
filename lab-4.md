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

Given:  
ISS = 1 mA → ID = 0.5 mA  

Output voltage:

```
Vout = VDD - ID * RD
```

```
0 = 0.9 - (0.5mA * RD)
RD = 1.8kΩ
```

---

## NMOS Width Calculation  

```
Cox = (εr * ε0) / tox
Cox = 8.42 × 10^-3 F/m²
```

```
Vov = VGS - VTH = 0.34V
```

```
Wn ≈ 19.9 µm
```

---

## Input Common Mode Range (ICMR)  

- Vin(max) = 0.36 V  
- Vin(min) ≈ -0.9 V  

✔ Operating range: **-0.9 V to 0.36 V**

---

## Output Common Mode Limits  

- Voc(max) = 0.9 V  
- Voc(min) = 0 V  

---

## Small Signal Gain  

```
Ad = -gm * RD
```

```
gm = 2ID / Vov = 2.94 mS
```

```
Ad ≈ -5.29 V/V
Gain ≈ 14.46 dB
```

---

## Practical Gain  

- Vin(p-p) = 200 mV  
- Vout(p-p) = 1204 mV  

```
Av = 1204 / 200 = 6.02
Gain ≈ 15.59 dB
```

---

## Differential Input Operation  

### Case 1: vid < √2 Vov  

- Both transistors ON  
- Linear amplification  
- No distortion  

---

### Case 2: vid > √2 Vov  

- One transistor OFF  
- Current fully steered  
- Output clipped  

---

## AC Analysis  

- Gain ≈ 14.33 dB  
- FL = 0 Hz  
- FH = 7.21 Hz  
- Bandwidth = 7.21 Hz  

```
UGB = Gain × BW = 74.47
```

---

# CIRCUIT 2  

## Description  

PMOS transistors act as active loads using a current mirror, increasing gain and output resistance.

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
P = (VDD - VSS) * ISS
```

```
1.8V * ISS ≤ 1.8mW
ISS = 1mA
```

---

## Current Distribution  

```
ID1 = ID2 = 0.5mA
```

---

## Transistor Operation  

- PMOS in saturation  
- NMOS in saturation  
- Tail transistor acts as constant current source  

---

## Theoretical Gain  

```
ro = 20kΩ
Rout = 10kΩ
gm = 4.17 mS
```

```
Ad = 41.7 V/V ≈ 32.4 dB
```

---

## ICMR Range  

- VICM(min) = -0.34 V  
- VICM(max) = 0.39 V  

---

## Practical Gain  

- Vin(p-p) = 10 mV  
- Vout(p-p) = 18.84 mV  

```
Av = 1.88
Gain = 5.48 dB
```

---

## Differential Input Condition  

```
|Vid| < √2 Vov = 0.34V
```

✔ Output remains linear  

---

## Clipping Condition  

- Current shifts to one branch  
- Output becomes distorted  

---

## AC Analysis  

- Gain = 5.48 dB  
- FL = 0 Hz  
- FH = 3 GHz  

```
Bandwidth = 3 GHz
UGB = 7.44 GHz
```
