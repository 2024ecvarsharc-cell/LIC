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

ID ≤ 0.4 mA 

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

ID(PMOS)=Kn'w(vSG-|Vth|)^2/2*L ----(5)

TOX=4.1*10^-9

Eox=3.98.85410^-12

U0=115.689*10^-4

solving 5th eq v will gwt W as

W=11.823µm

<img width="1180" height="800" alt="image" src="https://github.com/user-attachments/assets/762d6243-a7de-4d27-9572-3ed8afbaafc5" />


---

# DC Analysis

## Objective

To verify that the MOSFET operates in the saturation region and obtain the DC operating point.

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
  

## Voltage Gain

Av = Vout(p-p) / Vin(p-p)  

Av ≈ 6.30 V/V  

Gain(dB) = 20 log(6.30)  

Gain ≈ 16 dB  

---

# AC Analysis

## Transconductance

gm = 2ID / Vov  

gm = (2 × 200 µA) / 0.25  

gm = 1.6 mS  

---

## Output Resistance

Assume λ = 0.1  

ro = 1 / (λ ID)  

ro = 1 / (0.1 × 200 µA)  

ro = 50 kΩ  

(ro_n || ro_p) ≈ 25 kΩ  

---

## Voltage Gain

Av = -gm (ro_n || ro_p) / (1 + gmRs)  

Av ≈ -15.38 V/V  

Gain(dB) = 20 log(15.38)  

Gain ≈ 23.74 dB  

---

## Bandwidth

High Cutoff Frequency (fH) ≈ 376.34 MHz  

Low Cutoff Frequency (fL) ≈ 0 Hz  

Bandwidth (BW) ≈ 376 MHz  

---

# Result

## DC Analysis

MOSFET operates in saturation with ID ≈ 200 µA satisfying the power constraint.

## Transient Analysis

Simulated Gain ≈ 6.30 V/V  
Gain ≈ 16 dB  

## AC Analysis

Theoretical Gain ≈ 15.38 V/V  
Gain ≈ 23.74 dB  
Bandwidth ≈ 376 MHz  

---

# Inference

The simulated gain is lower than the theoretical gain due to:

- Channel length modulation  
- Source degeneration resistance  
- Non-ideal MOS characteristics  

AC analysis assumes small-signal conditions, while transient analysis reflects practical large-signal behavior.

The amplifier performance is verified and reasonably close to theoretical expectations.
