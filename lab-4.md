# FORMULAS USED IN DIFFERENTIAL AMPLIFIER

---

## 1. DC ANALYSIS

### Current Distribution
```
ID1 = ID2 = ISS / 2
```

### Output Voltage
```
Vout = VDD - (ID × RD)
```

### Power Relation
```
P = (VDD - VSS) × ISS
```

---

## 2. OXIDE CAPACITANCE

```
Cox = (εr × ε0) / tox
```

---

## 3. OVERDRIVE VOLTAGE

```
Vov = VGS - VTH
```

---

## 4. MOSFET DRAIN CURRENT (SATURATION)

```
ID = (1/2) μn Cox (W/L) (Vov)^2
```

### Width Calculation
```
W = (2 × ID × L) / (μn Cox (Vov)^2)
```

---

## 5. INPUT COMMON MODE RANGE (ICMR)

### Maximum Input Voltage
```
Vin(max) = VDD - (ID × RD) + VTH
```

### Minimum Input Voltage
```
Vin(min) = VSS + VDS(sat) + VGS
```

---

## 6. OUTPUT COMMON MODE VOLTAGE

### Maximum Output
```
Voc(max) = VDD
```

### Minimum Output
```
Voc(min) = VDD - (ID × RD)
```

---

## 7. TRANSCONDUCTANCE

```
gm = 2ID / Vov
```

OR

```
gm = √(2 μn Cox (W/L) ID)
```

---

## 8. DIFFERENTIAL GAIN

### Resistive Load
```
Ad = -gm × RD
```

### Active Load
```
Ad = gm × Rout
```

---

## 9. OUTPUT RESISTANCE

```
ro = 1 / (λ × ID)
```

### Parallel Resistance
```
Rout = ron || rop
```

---

## 10. GAIN IN DECIBELS

```
Gain(dB) = 20 log10(Av)
```

---

## 11. PRACTICAL GAIN

```
Av = Vout(p-p) / Vin(p-p)
```

---

## 12. DIFFERENTIAL INPUT CONDITION

### Linear Region
```
|Vid| < √2 × Vov
```

### Saturation (Clipping)
```
|Vid| > √2 × Vov
```

---

## 13. CURRENT STEERING

```
ID1 = (ISS / 2) + (gm × Vid / 2)
ID2 = (ISS / 2) - (gm × Vid / 2)
```

---

## 14. BANDWIDTH

```
BW = FH - FL
```

---

## 15. UNITY GAIN BANDWIDTH

```
UGB = Gain × Bandwidth
```

---

## 16. SMALL SIGNAL OUTPUT

```
Vout1 - Vout2 = -gm × RD × Vid
```

---

## 17. SATURATION CONDITION

### NMOS
```
VDS ≥ Vov
```

### PMOS
```
VSD ≥ Vov
```

---

## 18. GATE-SOURCE VOLTAGE

```
VGS = VG - VS
```

---

## 19. DRAIN-SOURCE VOLTAGE

```
VDS = VD - VS
```

---

## 20. SOURCE-DRAIN VOLTAGE (PMOS)

```
VSD = VS - VD
```

---
