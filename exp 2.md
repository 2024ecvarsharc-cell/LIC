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

# DC Analysis

## Objective

To verify that all transistors operate in saturation region and to obtain the DC operating point.

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

# Result

## DC Analysis

All transistors operate in saturation with ID ≈ 200 µA.

## Transient Analysis

Simulated Gain ≈ 2.094 V/V  
Gain ≈ 6.421 dB  

## AC Analysis

Theoretical Gain ≈ 0.45 V/V  
Gain ≈ -6.935 dB  
Bandwidth ≈ 136.405 MHz  

---

# Inference

The practical gain obtained from simulation is higher than the theoretical gain calculated using the simplified small-signal formula.

The difference occurs due to:

- Approximate small-signal modeling  
- Output resistance estimation (ro1 || ro3 approximation)  
- Bias point variations  
- Device parasitic effects  
- Simulation using accurate transistor models  

AC analysis assumes small-signal conditions, while transient analysis reflects practical large-signal behavior.

The cascode structure improves frequency response and provides stable operation with moderate gain and high bandwidth.

---

