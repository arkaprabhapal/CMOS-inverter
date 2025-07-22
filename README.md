# CMOS-inverte

**Under the guidance of Professor Nagendra Krishnapura, IIT Madras**

Software and PDK used : Cadence Virtuoso and TSMC 65nm PDK


## 1. Basic Schematic
<img width="257" height="300" alt="image" src="https://github.com/user-attachments/assets/7e02923c-7e30-445b-b802-e70841b3063e" />

Wp = 2Wn = 400 nm
L = 150 nm

I designed two inverters. One with Channel Length L and another with 5L.

Supply, Vdd = 1.2 V
### 1. DC sweep: Vo and ID versus Vi with Vi varying from 0 to VDD.
## 1.1 For L : 
- <img width="962" height="387" alt="image" src="https://github.com/user-attachments/assets/2301c49a-65fb-4244-b522-4b8caf3c6c60" />
## 1.2 For 5L : 
- <img width="968" height="340" alt="image" src="https://github.com/user-attachments/assets/6657a57e-fa49-49e0-ac45-4031f001a147" />

## Comparative Chart :
- # Transistor Parameter Comparison — L vs. 5L

This repository provides a comparative analysis of key electrical parameters for MOS transistors with channel lengths `L` and `5L`. The data highlights performance metrics across different input voltages (Vi), which are useful in analog/mixed-signal circuit design and optimization.

## 📊 Parameter Table

| **Parameter**             | **L**          | **5L**         |
|--------------------------|----------------|----------------|
| Vi for Max Slope         | 576 mV         | 600 mV         |
| Maximum Slope            | -19.995        | -35.0096       |
| **At Vi = 0 V**          |                |                |
| Leakage Current (I<sub>leak</sub>) | 11.546 pA      | 12.2724 pA     |
| g<sub>mp</sub>           | 8.852 pS       | 7.681 pS       |
| g<sub>mn</sub>           | 153.4 pS       | 56.9 pS        |
| g<sub>dsp</sub>          | 216.6 µS       | 48.99 µS       |
| g<sub>dsn</sub>          | 2.548 pS       | 564.7 fS       |
| **At Vi = V<sub>DD</sub>** |              |                |
| Leakage Current (I<sub>leak</sub>) | 4.33908 pA     | 2.98 pA        |
| g<sub>mp</sub>           | 57.68 pS       | 16.99 pS       |
| g<sub>mn</sub>           | 55.14 µS       | 30.55 pS       |
| g<sub>dsp</sub>          | 977.9 fS       | 137 fS         |
| g<sub>dsn</sub>          | 1.973 µS       | 61.24 µS       |

## 📘 Parameter Guide

- **Vi for Max Slope**: Input voltage at which maximum dVi/dVo occurs.
- **Maximum Slope**: Peak transition region sensitivity.
- **I<sub>leak</sub>**: Leakage current under specified Vi conditions.
- **g<sub>mp</sub>, g<sub>mn</sub>**: Transconductance of p-type and n-type devices.
- **g<sub>dsp</sub>, g<sub>dsn</sub>**: Output conductance of p-type and n-type devices.

## 🔬 Applications

This data serves as a reference for:
- Device sizing in analog IC design
- Performance modeling across technology nodes
- Input sensitivity analysis

## 2. SELF BIASED INVERTER
<img width="277" height="538" alt="image" src="https://github.com/user-attachments/assets/58bf69ae-7c64-453d-ae2c-7bc6d4f791e2" />

## 🔧 Table: Operating Point Parameters

| Parameter         | Length = L     | Length = 5L     | Description                              |
|------------------|----------------|-----------------|------------------------------------------|
| Vo               | 575.3 mV       | 590.6 mV        | Output voltage                           |
| I_VDD            | 5.918 µA       | 1.558 µA        | Current through VDD                      |
| gmp              | 55.14 µS       | 12.97 µS        | Transconductance of PMOS                 |
| gmn              | 69.62 µS       | 14.38 µS        | Transconductance of NMOS                 |
| gdsp (OP)        | 1.973 µS       | 196.1 nS        | PMOS drain-source conductance (measured)|
| gdsp (Est.)      | 2.646 µS       | 269.9 nS        | PMOS drain-source conductance (estimated)|
| μp * Cox         | 96.33 µA/V²    | 152.27 µA/V²    | Mobility × Oxide capacitance (PMOS)     |
| VTP              | -482.7 mV      | -415.8 mV       | Threshold voltage (PMOS)                 |
| μn * Cox         | 316.9 µA/V²    | 359.325 µA/V²   | Mobility × Oxide capacitance (NMOS)     |
| VTN              | 512.5 mV       | 431.6 mV        | Threshold voltage (NMOS)                 |

*Note: `gdsp (OP)` is from operating point measurement, while `gdsp (Est.)` is calculated.*

## 3. SELF BIASED AMPLIFIER
<img width="935" height="534" alt="image" src="https://github.com/user-attachments/assets/019a6cb3-0a81-4f83-b7f5-acc261dbc955" />

## 📊 Summary

| Parameter                             | Length = L     | Length = 5L   | Description                                                                 |
|--------------------------------------|----------------|---------------|-----------------------------------------------------------------------------|
| Rbias                                | 20 MΩ          | 40 MΩ          | Bias resistance for amplifier design                                        |
| Mid-band \|vo/vi\|                   | 26.71          | 55.643         | Gain from AC analysis                                                       |
| (gmp + gmn) / (gdsp + gdsn)          | 27.01          | 58.691         | Transconductance to conductance ratio                                      |
| Input Peak-to-Peak @ 10% Deviation   | 20 mV          | 5 mV           | Input signal range allowed for 10% deviation between AC and transient      |
| Output Peak-to-Peak @ 10% Deviation  | 513.6135 mV    | 510 mV         | Output signal swing within the same deviation tolerance                    |


## 4. Simulations over PVT corners using ADE-Explorer: Setup the (twenty) corners as {tt, ss, ff, sf, fs} × {1 V, 1.3 V} × {0◦ C, 100◦ C}.

<img width="722" height="441" alt="image" src="https://github.com/user-attachments/assets/94b08c31-cf56-462e-8f03-80d463167a54" />


