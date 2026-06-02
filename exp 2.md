# Amplifier Configuration – 

a)

---

## Common Source (CS) Amplifier using LTSpice (180nm CMOS)

---

## Aim

To design and perform DC, Transient, and AC analysis of a Common Source amplifier using LTSpice and extract the associated parameters.

---

## Components Required

- TSMC 180nm NMOS (CMOSN)
- TSMC 180nm PMOS (CMOSP)
- Source Resistor (Rs)
- Three Voltage Sources
- LTSpice Software

---

## Given Parameters

| Parameter | Value |
|------------|--------|
| Vov | 0.25 V |
| VDD | 2 V |
| Vth (PMOS) | -0.39 V |
| Vth (NMOS) | 0.36 V |
| Power (P) | ≤ 1.2 mW |
| Channel Length (L) | 180 nm |
| Ln | 480 n |

---

## Design Calculation

### ID Calculation

P = V × I  

2 V × I ≤ 1.2 mW 

ID ≤ 0.6 mA 

let ID = 100µA

### calculation in NMOS

assume VRS=0.2V

Vov=VGS-Vth

VGS=0.61

Vout=VDS+VRS

Vout=(VDD/2)+VRS

Vout= 1.2 V

VG=VGS+VRS

VG=0.61+0.2=0.81V

VDs≥VGs-Vth

VDs≥0.25 --(it is in saturation state)

VRS=ID*Rs

Rs=2kohm

ID=(Kn'w(vGS-Vth)^(2))/(2*L)

TOX=4.1*10^-9

Eox=3.98*85410^-12

UO=273.809*10^-4

W=4.997*10^-6 if we substitute this values in simulation we will get

by trial and error in PMOS and NMOS width

Wpmos=44.9µm Wnmos=10.8608µm for this values we will get Id has 100uA

### PMOS

Vov=VSG-|Vth| VSG=0.64

VS-VG=0.64

VS-0.64=VG--(4) (VS=VDD=2V)

VG=1.36V

ID=Kn'w(vSG-|Vth|)^2/2*L ----(5)

TOX=4.1*10^-9

Eox=3.9*8.85410^-12

U0=115.689*10^-4

solving 5th eq v will gwt W as

W=11.823µm

<img width="1180" height="800" alt="image" src="https://github.com/user-attachments/assets/762d6243-a7de-4d27-9572-3ed8afbaafc5" />


---

# DC Analysis

## Objective

To verify that the MOSFET operates in the saturation region and obtain the DC operating point.
<img width="862" height="644" alt="image" src="https://github.com/user-attachments/assets/c4701c90-24da-43d4-99b7-626ed008dc25" />



## Procedure

1. Design the CS amplifier in LTSpice.
2. Set VDD = 2 V and VGS = 0.61 V.
3. Go to Simulate → Edit Simulation Cmd → DC op pnt.
4. Run the simulation.

---

# Transient Analysis

## Input Signal

SINE(0.8 10m 1k)

Peak Amplitude = 10 mV 
<img width="1919" height="890" alt="image" src="https://github.com/user-attachments/assets/65a409fd-dc32-471c-bafb-ea9d692a5a4d" />

  

## Voltage Gain

Av = Vout(p-p) / Vin(p-p)  

Av ≈ 25.202 V/V  

Gain(dB) = 20 log(25.202)  

Gain ≈ 28.029 dB  

---

# AC Analysis

## Transconductance

gm = 2ID / Vov  

gm = (2 × 100 µA) / 0.25  

gm = 0.8 mS  

---

## Output Resistance

Assume λ = 0.1  

ro = 1 / (λ ID)  

ro = 1 / (0.1 × 100 µA)  

ro = 100 kΩ  

(ro_n || ro_p) ≈ 50 kΩ  

---

## Voltage Gain

Av = -gm (ro_n || ro_p) / (1 + gmRs)  

Av ≈ -15.38 V/V  

Gain(dB) = 20 log(15.38)  

Gain ≈ 23.74 dB  

---

## Bandwidth

High Cutoff Frequency (fH) ≈ 136.23621 MHz  

Low Cutoff Frequency (fL) ≈ 0 Hz  

Bandwidth (BW) ≈ 136.236 MHz 

<img width="1919" height="850" alt="image" src="https://github.com/user-attachments/assets/f5780a27-cde4-4b7a-b8df-2b7b58b6d034" />


---

# Result

## DC Analysis

MOSFET operates in saturation with ID ≈ 100 µA satisfying the power constraint.

## Transient Analysis

Simulated Gain ≈ 25.202 V/V  
Gain ≈ 28.029 dB  

## AC Analysis

Theoretical Gain ≈ 15.38 V/V  
Gain ≈ 23.74 dB  
Bandwidth ≈ 136.236 MHz  

---

# Inference

The simulated gain is higher than the theoretical gain due to:

- Assumed λ value (ro estimation error)

-Approximate small-signal model

-Bias point variation

-Simulation extracting actual device parameters

-Neglecting body effect in hand calculation  

AC analysis assumes small-signal conditions, while transient analysis reflects practical large-signal behavior.

The amplifier performance is verified and reasonably close to theoretical expectations.

---

b)

---

## Aim

To design and perform DC, Transient, and AC analysis of a Cascode Common Source amplifier with PMOS active load using LTSpice and extract the associated parameters.

---

## Components Required

- TSMC 180nm NMOS (CMOSN) – M1 (Input)
- TSMC 180nm NMOS (CMOSN) – M2 (Cascode)
- TSMC 180nm PMOS (CMOSP) – M3 (Active Load)
- Voltage Sources
- LTSpice Software

---

## Given Parameters

| Parameter | Value |
|------------|--------|
| VDD | 2 V |
| ID | 100 µA  |
| VOV | 0.2 V |
| VTN | 0.36 V |
| VTP | -0.39 V |
| λn | 0.1 |
| λp | 0.12 |
| Channel Length (L) | 180 nm |
|Ln | 480 n |

---

## Design Calculation

### Output Bias Voltage

Vout = VDD / 2  

Vout = 2 / 2  

Vout = 1 V  

---

### Calculation in M1 (NMOS – Input Transistor)

ID=(Kn'w(vGS-Vth)²)/(2*L)

VGS = VOV + VTN  

VGS = 0.2 + 0.36 

VGS = 0.56 V  

Assume VS = 0.3 V  

VG = VGS + VS  

VG = 0.566 + 0.3  

VG = 0.86 V  

VDS = Vout − VS  

VDS = 1 − 0.3  

VDS = 0.7 V  

Saturation Condition:

VDS ≥ VOV  

0.7 ≥ 0.2  (Saturation satisfied)

Final Width:

W1 = 34.305 µm  

---

### Calculation in M2 (NMOS – Cascode Transistor)

VGS2 = 0.56 V  

VDS2 ≈ 0.7 V  

Saturation Condition:

VDS2 ≥ VOV  

0. 7 ≥ 0.2  (Saturation satisfied)

Final Width:

W2 = 34.305 µm  

---

### Calculation in M3 (PMOS – Active Load)

VSG = VOV + |VTP|  

VSG = 0.2 + 0.39  

VSG = 0.59 V  

VG = VDD − VSG  

VG = 2 − 0.59  

VG = 1.41 V  

VSD = VDD − Vout  

VSD = 2 − 0.6  

VSD = 1.4 V  

Saturation Condition:

VSD ≥ VOV  

1.4 ≥ 0.2  (Saturation satisfied)

Final Width:

W3 = 44.813 µm  

---

<img width="1465" height="854" alt="Screenshot 2026-06-02 083402" src="https://github.com/user-attachments/assets/9c7b55c1-6981-4bbc-8482-3697e507dc6e" />


---

# DC Analysis

## Objective

To verify that all transistors operate in saturation region and to obtain the DC operating point.

---
<img width="790" height="597" alt="Screenshot 2026-06-02 083423" src="https://github.com/user-attachments/assets/0dad9b4f-cf75-444e-bb5d-52bee418c520" />
---

## Procedure

1. Design the cascode CS amplifier in LTSpice.
2. Set VDD = 1.2 V.
3. Apply proper gate bias voltages.
4. Go to Simulate → Edit Simulation Cmd → DC op pnt.
5. Run the simulation.

All devices are confirmed to operate in saturation.

---

# Transient Analysis

## Input Signal

SINE(0.6 10m 1k)

Peak Amplitude = 10 mV  

Measured:

ΔVout = 627.83 mV − 585.94 mV  

ΔVout = 41.89 mV  

ΔVin = 20 mV  

---
<img width="1857" height="365" alt="Screenshot 2026-06-02 083442" src="https://github.com/user-attachments/assets/09f5a625-a4f5-49c4-a183-fd6cdeceef25" />
---

## Voltage Gain

Av = ΔVout / ΔVin  

Av = 41.89 / 20  

Av ≈ 2.094 V/V  

Gain(dB) = 20 log(2.094)  

Gain ≈ 6.421 dB  

---

# AC Analysis

## Transconductance

gm = 2ID / VOV  

gm = (2 × 200 µA) / 0.2  

gm = 2 mS  

---

## Output Resistance

ro1 = 1 / (λn ID)  

ro1 = 1 / (0.1 × 200 µA)  

ro1 = 50 kΩ  

ro3 = 1 / (λp ID)  

ro3 = 1 / (0.12 × 200 µA)  

ro3 = 41.66 kΩ  

ro_eff = ro1 || ro3  

ro_eff = (50k × 41.66k) / (50k + 41.66k)  

ro_eff ≈ 22.727 kΩ  

---

## Voltage Gain

Av = - (gm × ro_eff) / (1 + gm ro2)  

Av = - (0.002 × 22727) / (1 + 0.002 × 50000)  

Av = - 45.45 / 101  

Av ≈ -0.45 V/V  

Gain(dB) = 20 log(0.45)  

Gain ≈ -6.935 dB  

---

## Bandwidth

Lower cutoff frequency (fL) ≈ 0 Hz  

Upper cutoff frequency (fH) ≈ 136.405 MHz  

Bandwidth (BW) ≈ 136.405 MHz  

Unity Gain Bandwidth (UGB):

UGB = Av(mid, linear) × BW  

UGB = 2.094 × 136.405  

UGB ≈ 285.63 MHz  

---
<img width="1888" height="638" alt="Screenshot 2026-06-02 083523" src="https://github.com/user-attachments/assets/957fc6a0-8776-4df0-b2a2-9bf0197426ea" />
---

## Simulation Protocols

### 1. DC Analysis

#### Objective

Verify the structural DC operating point parameters to guarantee every active MOS device is biased safely inside the saturation region.

#### Procedure

1. Construct the complete multi-terminal Common Source (CS) amplifier architecture inside the design environment.
2. Setup the supply network with:

   * VDD = 1.2 V
   * VG1 = 0.866 V
   * VG2 = 0.566 V
   * VG3 = 0.61 V
3. Include the operating-point simulation directive:

   ```spice
   .op
   ```
4. Execute the simulation and verify:

   * Node voltages
   * Drain current flow
   * Saturation region operation
   * Target current:

   ```text
   ID ≈ 200 µA
   ```

---

### 2. Transient Analysis

#### Objective

Track time-domain dynamic properties, verify signal path stability, and measure peak-to-peak output signal amplification.

#### Procedure

1. Apply a small-signal sinusoidal input source:

   ```spice
   SINE(0.866 10m 1k)
   ```

2. Add the transient simulation directive:

   ```spice
   .trans 0 5m 0 1u
   ```

3. Run the simulation and observe:

   * Input waveform
   * Output waveform
   * Peak-to-peak voltage swing
   * Signal amplification characteristics

4. Extract:

   * Vin(p-p)
   * Vout(p-p)

---

### 3. AC Frequency Sweep

#### Objective

Characterize the amplifier frequency response, determine midband gain, and identify upper cutoff frequency characteristics.

#### Procedure

1. Configure the input source for AC small-signal analysis:

   ```spice
   AC 1
   ```

2. Define logarithmic frequency sweep limits:

   ```spice
   .ac dec 100 10 100G
   ```

3. Probe the output node and evaluate:

   * Voltage gain in dB
   * Frequency response
   * Phase response
   * Bandwidth
   * Upper cutoff frequency

4. Determine the upper cutoff frequency at the:

   ```text
   -3 dB
   ```

   attenuation point.

---

# Results

| Metric                          | Theoretical Value (Ideal) | Simulated Value (BSIM) |
| :------------------------------ | :------------------------ | :--------------------- |
| Drain Current (ID)              | 200 µA                    | 200 µA                 |
| Quiescent Output Voltage (Vout) | 0.6 V                     | 0.6 V                  |
| Voltage Gain (Av)               | -0.45 V/V (-6.935 dB)     | 2.094 V/V (6.42 dB)    |
| Upper Cutoff Frequency (fH)     | —                         | 138.181 MHz            |
| Total Bandwidth (BW)            | —                         | 138.151 MHz            |

---

# Inference

### Operating Mode Validation

Simulation results confirm that all MOS transistors (M1, M2, and M3) remain properly biased in the saturation region throughout nominal operation.

### Power Verification

The total power dissipation is:

```text
P = 0.24 mW
```

which satisfies the specified power constraint:

```text
P ≤ 0.4 mW
```

### Gain Variance Analysis

The ideal hand calculations predict a lower gain value:

```text
-6.935 dB
```

whereas BSIM simulation produces:

```text
6.42 dB
```

This deviation occurs because ideal square-law equations overestimate the source degeneration term:

```text
(1 + gmro2)
```

In practical short-channel CMOS devices, effects such as:

* Velocity saturation
* Drain Induced Barrier Lowering (DIBL)
* Channel-length modulation

reduce the effective output resistance of transistor M2, thereby lowering degeneration and increasing the achievable gain.

### Frequency Response Characteristics

With the output node dominated by the:

```text
0.5 pF
```

load capacitor, the amplifier behaves as a stable low-pass system exhibiting bandwidth preservation up to approximately:

```text
138 MHz
```

The circuit therefore demonstrates strong high-frequency performance suitable for moderate-speed analog signal processing applications.

---

c)

---


# Design and Analysis of MOSFET Amplifier Configurations Using 180 nm CMOS Technology

This repository contains the theoretical design calculations, operating point verification, and LTspice simulation analysis of MOSFET amplifier configurations implemented using 180 nm CMOS technology.

---

# Aim

To design and simulate MOSFET amplifier configurations using 180 nm CMOS technology in LTspice, perform DC, transient, and AC analyses, and compare gain, bandwidth, power consumption, and overall amplifier performance.

---

# Given Specifications

| Parameter                       | Value             |
| :------------------------------ | :---------------- |
| Supply Voltage (VDD)            | 1.2 V             |
| Drain Current (ID)              | 200 µA            |
| Overdrive Voltage (VOV)         | 0.2 V             |
| Load Capacitance (CL)           | 0.5 pF            |
| Channel Length (Ln, Lp)         | 180 nm            |
| Maximum Power                   | ≤ 0.4 mW          |
| Relative Permittivity (εr)      | 3.9               |
| Permittivity of Free Space (ε0) | 8.854 × 10⁻¹² F/m |
| Oxide Thickness (tox)           | 4.1 × 10⁻⁹ m      |
| Electron Mobility (μn)          | 273.809 cm²/Vs    |
| Hole Mobility (μp)              | 115.689 cm²/Vs    |

---

# Circuit Configuration

Circuit Used: Circuit 2C

---

# Design Calculations

## 1. NMOS Gate Voltage Calculation

Given:

```text
VOV = 0.2 V
```

Using:

```text
VOV = VGS − VTH
```

Therefore:

```text
VGS = VOV + VTH
```

Substituting:

```text
VGS = 0.2 + 0.36
VGS = 0.56 V
```

For transistor M2:

```text
VS = 0
VG = 0.56 V
```

---

## 2. Input Transistor Biasing (M1)

Since:

```text
VG = VD (fixed biasing)
```

Using:

```text
VGS = VTH + VOV
```

Therefore:

```text
VGS = 0.36 + 0.2
VGS = 0.56 V
```

Source voltage of M1 equals drain voltage of M2:

```text
VS = 0.56 V
```

Hence:

```text
VG = VS + VGS
VG = 0.56 + 0.56
VG = 1.12 V
```

---

## 3. PMOS Load Biasing (M3)

Using:

```text
VSG = |VTH| + VOV
```

Substituting:

```text
VSG = 0.39 + 0.2
VSG = 0.59 V
```

Given:

```text
VS = VDD = 1.2 V
```

Therefore:

```text
VG = 1.2 − 0.59
VG = 0.61 V
```

---
<img width="1193" height="713" alt="Screenshot 2026-06-02 091332" src="https://github.com/user-attachments/assets/d1f0ced9-3b9d-4928-b8bf-30af7725d90d" />
---

# Region of Operation Verification

## M1 – Amplifying NMOS

Given:

```text
Source Voltage = 0.556 V
Gate Voltage = 1.12 V
```

Calculation:

```text
VGS1 = 1.12 − 0.556
VGS1 = 0.564 V
```

Overdrive:

```text
VOV1 = VGS1 − VTN
VOV1 = 0.564 − 0.36
VOV1 = 0.204 V
```

Drain-to-source voltage:

```text
VDS1 = 0.882 − 0.556
VDS1 = 0.326 V
```

Condition:

```text
VDS1 > VOV1
0.326 > 0.204
```

Result:

```text
M1 operates in saturation region
```

---

## M2 – Diode Connected NMOS

For diode connection:

```text
VDS2 = VGS2
```

Given:

```text
VGS2 = 0.556 V
```

Check:

```text
VGS2 − VTN = 0.556 − 0.36
= 0.196 V
```

Condition:

```text
VDS2 > VOV2
0.556 > 0.196
```

Result:

```text
M2 operates in saturation region
```

---

## M3 – PMOS Load

Given:

```text
Source = 1.2 V
Gate = 0.61 V
Drain = 0.882 V
```

Calculation:

```text
VSG3 = 1.2 − 0.61
VSG3 = 0.59 V
```

Overdrive:

```text
VOV3 = 0.59 − 0.39
VOV3 = 0.20 V
```

Drain-to-source voltage:

```text
VSD3 = 1.2 − 0.882
VSD3 = 0.318 V
```

Condition:

```text
VSD3 > VOV3
0.318 > 0.20
```

Result:

```text
M3 operates in saturation region
```

---

# Output Voltage Swing

## Maximum Output Voltage

Upper limit occurs when PMOS transistor M3 leaves saturation.

Condition:

```text
VSD3 ≥ VOVp
```

Using:

```text
VSD3 = VDD − Vout
```

At boundary:

```text
Vout,max = VDD − VOVp
Vout,max = 1.2 − 0.20
Vout,max = 1.0 V
```

---

## Minimum Output Voltage

Lower limit occurs when NMOS transistor M1 leaves saturation.

Condition:

```text
VDS1 ≥ VOVn
```

Using:

```text
VDS1 = Vout − VS
```

At boundary:

```text
Vout,min = VS + VOVn
Vout,min = 0.556 + 0.20
Vout,min = 0.756 V
```

---

# Symmetry Check

Quiescent output voltage:

```text
Vout,Q = 0.882 V
```

Upper swing:

```text
1.0 − 0.882 = 0.118 V
```

Lower swing:

```text
0.882 − 0.756 = 0.126 V
```

The amplifier output swing is approximately symmetrical.

---

# MOSFET Width Calculations

Using:

```text
ID = (1/2) μ Cox (W/L) VOV²
```

Rearranging:

```text
W = (2 ID L) / (μ Cox VOV²)
```

---

## NMOS Width Calculation

Substituting:

```text
Wn = (2 × 200×10⁻⁶ × 0.18×10⁻⁶)
     /
     (0.02738 × 8.42×10⁻³ × (0.2)²)
```

Result:

```text
Wn ≈ 7.8 µm
```

Practical optimized value from simulation:

```text
Wn = 33.567 µm
```

---

## PMOS Width Calculation

Substituting:

```text
Wp = (2 × 200×10⁻⁶ × 0.18×10⁻⁶)
     /
     (0.01157 × 8.42×10⁻³ × (0.2)²)
```

Result:

```text
Wp ≈ 18 µm
```

Observed behavior:

```text
At Wp = 18 µm, drain current ≈ 120 µA
```

To achieve:

```text
ID ≈ 200 µA
```

Optimized simulation value:

```text
Wp = 49.6 µm
```

---

# Simulation Protocols

## 1. DC Analysis

### Objective

Verify DC operating point and saturation region biasing.

### Procedure

1. Construct Circuit 2C in LTspice.
2. Apply:

   * VDD = 1.2 V
   * VG1 = 1.12 V
   * VG2 = 0.56 V
   * VG3 = 0.61 V
3. Add simulation directive:

   ```spice
   .op
   ```
4. Verify:

   * Node voltages
   * Drain current
   * Saturation conditions

Result:

```text
ID ≈ 200 µA
```
---
<img width="1233" height="837" alt="Screenshot 2026-06-02 091624" src="https://github.com/user-attachments/assets/5f93d362-6558-4fbf-b5e8-50e24cab1fd1" />
---

## 2. Transient Analysis

### Objective

Measure time-domain amplification and waveform stability.

### Procedure

1. Apply sinusoidal input:

   ```spice
   SINE(1.12 10m 1k)
   ```
2. Add directive:

   ```spice
   .trans 0 5m 0 1u
   ```
3. Observe:

   * Input waveform
   * Output waveform
   * Peak-to-peak voltage gain

---
<img width="1233" height="687" alt="Screenshot 2026-06-02 093254" src="https://github.com/user-attachments/assets/e3436762-8db6-4fda-8963-1091e30a10ec" />

---
## 3. AC Analysis

### Objective

Determine gain and frequency response.

### Procedure

1. Configure input source:

   ```spice
   AC 1
   ```
2. Add AC sweep:

   ```spice
   .ac dec 100 10 100G
   ```
3. Plot:

   * Gain
   * Bandwidth
   * Frequency response

---
<img width="1234" height="675" alt="Screenshot 2026-06-02 093316" src="https://github.com/user-attachments/assets/4ce34ad6-e4ab-4afe-9385-f19ef8a7f68c" />
---

# Results

| Parameter            | Value     |
| :------------------- | :-------- |
| Drain Current        | ≈ 200 µA  |
| Optimized NMOS Width | 33.567 µm |
| Optimized PMOS Width | 49.6 µm   |
| Voltage Gain (Av)    | 10.18 V/V |
| Gain in dB           | 20.154 dB |

---

# Inference

* Circuit 3 provides the highest practical midband gain of approximately 18.6 dB.
* Circuit 3 achieves the highest unity gain bandwidth (UGB).
* Diode-connected loads reduce gain but simplify transistor biasing.
* A clear gain-bandwidth trade-off is observed across amplifier configurations.
* Simulation results validate the behavior of 180 nm CMOS analog amplifier design principles.

