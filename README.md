# CMOS INVERTER and DIFFERENT ANALYSES
**Under the guidance of Professor Nagendra Krishnapura, IIT Madras**

## Software and PDK used : Cadence Virtuoso and TSMC 65nm PDK ##


## CMOS inverter Schematic
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
| Vi for Max Slope         | 600 mV         | 600 mV         |
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

## Table Overview
# Comprehensive MOS Device Behavior Table

This table documents the performance characteristics of various MOS (Metal–Oxide–Semiconductor) devices across different **technology corners**, **supply voltages**, and **temperature conditions**. It highlights output behavior for two input voltage cases:

- `Vi = 0`
- `Vi = VDD`

Technology corners include:
- `tt`: Typical-Typical  
- `ss`: Slow-Slow  
- `ff`: Fast-Fast  
- `sf`: Slow-Fast  
- `fs`: Fast-Slow  

## Leakage Current (in Ampere) Table 

| Row | Corner | VDD | Temp (°C) | Vi = 0   | Vi = VDD |
|-----|--------|-----|-----------|----------|----------|
| 1   | tt     | 1   | 0         | 2.271    | 2.272p   |
| 2   | tt     | 1   | 100       | 54.24p   | 2.403p   |
| 3   | tt     | 1.3 | 0         | 3.07p    | 5.779p   |
| 4   | tt     | 1.3 | 100       | 60.18p   | 276.5p   |
| 5   | ss     | 1   | 0         | 1.865p   | 2.153p   |
| 6   | ss     | 1   | 100       | 16.51p   | 2.214p   |
| 7   | ss     | 1.3 | 0         | 2.729p   | 3.476p   |
| 8   | ss     | 1.3 | 100       | 18.78p   | 101.3p   |
| 9   | ff     | 1   | 0         | 3.562p   | 2.501p   |
| 10  | ff     | 1   | 100       | 172.9p   | 2.917p   |
| 11  | ff     | 1.3 | 0         | 4.515p   | 17.56p   |
| 12  | ff     | 1.3 | 100       | 190.5p   | 853.4p   |
| 13  | sf     | 1   | 0         | 2.109p   | 2.277p   |
| 14  | sf     | 1   | 100       | 24.85p   | 2.563p   |
| 15  | sf     | 1.3 | 0         | 2.845p   | 11.57p   |
| 16  | sf     | 1.3 | 100       | 27.93p   | 594.4p   |
| 17  | fs     | 1   | 0         | 2.8p     | 2.267p   |
| 18  | fs     | 1   | 100       | 117.9p   | 2.331p   |
| 19  | fs     | 1.3 | 0         | 3.733p   | 3.799p   |
| 20  | fs     | 1.3 | 100       | 129.9p   | 126p     |

## gds of ON transistor (in Siemens) Table 

## 📊 MOS Performance Table

| Row | Corner | VDD | Temp (°C) | Vi = 0   | Vi = VDD |
|-----|--------|-----|-----------|----------|----------|
| 1   | tt     | 1   | 0         | 43.39u   | 67.54u   |
| 2   | tt     | 1   | 100       | 31.17u   | 48.33u   |
| 3   | tt     | 1.3 | 0         | 59.77u   | 67.54u   |
| 4   | tt     | 1.3 | 100       | 42.11u   | 48.83u   |
| 5   | ss     | 1   | 0         | 39u      | 60.94u   |
| 6   | ss     | 1   | 100       | 28.28u   | 44.34u   |
| 7   | ss     | 1.3 | 0         | 55.47u   | 60.94u   |
| 8   | ss     | 1.3 | 100       | 39.2u    | 44.34u   |
| 9   | ff     | 1   | 0         | 48.25u   | 74.55u   |
| 10  | ff     | 1   | 100       | 34.36u   | 53.6u    |
| 11  | ff     | 1.3 | 0         | 64.52u   | 74.55u   |
| 12  | ff     | 1.3 | 100       | 45.32u   | 53.59u   |
| 13  | sf     | 1   | 0         | 46.39u   | 63.05u   |
| 14  | sf     | 1   | 100       | 33.03u   | 45.97u   |
| 15  | sf     | 1.3 | 0         | 62.69u   | 63.05u   |
| 16  | sf     | 1.3 | 100       | 43.94u   | 45.97u   |
| 17  | fs     | 1   | 0         | 40.43u   | 72u      |
| 18  | fs     | 1   | 100       | 29.32u   | 51.65u   |
| 19  | fs     | 1.3 | 0         | 56.88u   | 72u      |
| 20  | fs     | 1.3 | 100       | 40.29u   | 51.65u   |

---

## 5. Layout Design :
# 5.1 Layout of Transistor with channel length L and 5L
<img width="780" height="782" alt="image" src="https://github.com/user-attachments/assets/5ba72c55-5069-477c-ac9e-cbf5c2d2f049" />

# 5.2 Layout of 5L transistor with two fingers of PMOS
<img width="556" height="581" alt="image" src="https://github.com/user-attachments/assets/10fd9607-3be9-4338-8b2d-65d8446d58e5" />

**After successfully passing the DRC, LVS and PEX, I was able to extract the CMOS inverter**
<img width="896" height="251" alt="image" src="https://github.com/user-attachments/assets/6b3529c6-fcbd-4e14-be9d-f8d9156b03b4" />
<img width="195" height="728" alt="image" src="https://github.com/user-attachments/assets/f69853f0-c2e1-4e95-835b-5babeff5ee3a" />


