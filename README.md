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

## 2. Determining the DC current  
- Lower Limit : It is calculated by the slew rate of the OTA and it came to be 50μA.
- Upper Limit : it is calculated from the maximum power consumption of the circuit and it came to be 55.55μA.
- So, I chose the DC current to be **55μA** as it satisfies both criterias.
- 
## 3. Determining the dimensions of MOSFETs
We are considering the **Length(L)** of all mosfets as 1µm.
### 3.1 Input pair NMOS 
Its dimensions were calculated from UGF. The calculated value of (W/L) was 6. But by not getting the expected gm from this W/L ratio in the simulation, I changed it to **7**.
### 3.2 Current mirror PMOS 
Its dimensions were calculated from ICMR+ value. The calculated value was (W/L) = **7**.
### 3.3 Current mirror NMOS
Its dimensions were calculated from ICMR- value and the calculated value was (W/L) = **5.87**

## 4. Initial analysis
### At ICMR = 0.8V
- ![Screenshot](https://github.com/user-attachments/assets/7aa7f112-9508-4afa-8250-f48ceebdc3fe)
- ![Screenshot-1](https://github.com/user-attachments/assets/459ecb4e-d831-4714-9618-14f39dd1a5f8)
- Gain = 38.5dB and UGF = 5.04 MHz
### At ICMR = 1.6V
- ![Screenshot-4](https://github.com/user-attachments/assets/c2f19236-3c48-4963-8041-36b2338b3b24)
- ![Screenshot-3](https://github.com/user-attachments/assets/6876d200-7ac2-4e22-9dcd-96a14a0d876f)
- Gain = 34.2 dB and UGF = 5.07 MHz
The gain is slightly low at ICMR = 1.6V and the ouput DC voltage level is slightly low than calculated. So the circuit is tuned accordingly.
### Power consumption
- I have observed the changed of Io w.r.t change in ICMR voltage.
- ![Screenshot-12](https://github.com/user-attachments/assets/4e422a9d-b032-4374-bcf0-c21548ef38c7)
It has been observed that Io increases linearly w.r.t Input common mode voltage. And at ICMR = 1.6V, Io = 57.42 μA. But the maximum limit is 55.55 μA. So, the value of current in current source of current mirror is tuned accordingly.

## 5. Final Transistor tunings
- **Current mirror PMOS** : (W/L) = **8**
- **Input pair NMOS** : (W/L) = **9**
- **Current mirror NMOS** : (W/L) = **5.87**
- **Value of DC current of the OTA** : Io = 53 μA. This is the value of current at current source of the current sink of the OTA structure.
  
## 6. Final Analysis

### At ICMR = 0.8V
- ![Screenshot-23](https://github.com/user-attachments/assets/a069651c-288f-46e1-9a2b-d3c1daef6bc6)
- ![Screenshot-22](https://github.com/user-attachments/assets/285d222e-ef93-499d-a1ed-3e5ad554fd5d)
- Gain = 39.31 dB and UGF = 5.53 MHz
### At ICMR = 1.6V
- ![Screenshot-24](https://github.com/user-attachments/assets/3f17c8c8-970e-4c72-a5d9-a10e58455ce1)
- ![Screenshot-25](https://github.com/user-attachments/assets/0232898c-6317-4f67-8e71-e2ca38a8478c)
- Gain = 36.18 dB and UGF = 5.61 MHz
### Power consumption
- The value of Io is measured w.r.t change in Input common mode voltage.
![Screenshot-21](https://github.com/user-attachments/assets/72766050-c5f7-4564-95a5-205155611bea)
- Io increases linearly w.r.t ICM voltage and 52.97 μA ≤ Io ≤ 55.37 μA.
- So, Power consumption, P ranges between 95.346 μW ≤ P ≤ 99.66 μW.


## 7. Final design
- **FInal ciecuit design**
- ![Screenshot-13](https://github.com/user-attachments/assets/fa32796b-d7de-4ee7-af8a-40fb99170104)
- **Symbol creation**
- ![Screenshot-14](https://github.com/user-attachments/assets/a7de3671-85b2-4648-b4b1-8fa6e819db6d)

## 8. Further Analysis
### 8.1 Calculation of CMRR (Common Mode Rejection Ratio)
I have used the following circuit for calculating CMRR.
![Screenshot-31](https://github.com/user-attachments/assets/24d4a5e1-d8b9-4b65-a6f1-39b824f6a346)
- At **ICMR = 0.8 V** :
- ![Screenshot-28](https://github.com/user-attachments/assets/c2e6ffeb-0361-4d25-a81c-e004b19ffd51)
- We are getting **CMRR = 81.2 dB** .
- - At **ICMR = 1.6 V** :
- ![Screenshot-29](https://github.com/user-attachments/assets/16375093-ae18-49b4-a852-4bdb62a63c67)
- We are getting **CMRR = 83.03 dB** .

### 8.2 Output swing
![Screenshot-33](https://github.com/user-attachments/assets/53b37bb6-f79b-4bfb-8617-1c3d4e241b6a)
Maximum Output swing = 1.367 V p-p

## 9. Noise Analysis
![Screenshot-57](https://github.com/user-attachments/assets/6d251ae4-d8c7-4bef-8a82-c28ac4ec6dc2)




