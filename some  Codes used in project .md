# Particle Accelerator Simulation Framework (Unity 3D)

## Overview
This project presents a computational simulation framework for modelling charged particle dynamics in accelerator environments. The system integrates electromagnetic field interactions, RF acceleration, and real-time visualization using Unity 3D.

⚠️ **Note:** This repository contains selected components and representative code samples. The complete system is part of ongoing development and is not publicly released.

The simulation focuses on three main components:
- Magnetic and electric force-based particle motion  
- Drift Tube Linac (DTL) acceleration modelling  
- Real-time velocity and acceleration visualization  

---

## 1. Electromagnetic Force Simulation

The particle motion is governed by the Lorentz force equation:

$$
\vec{F} = q(\vec{v} \times \vec{B}) + q\vec{E}
$$

### Implementation Highlights
- Magnetic force computed using cross product of velocity and magnetic field  
- Electric force applied along velocity direction  
- Real-time force updates applied using Unity Rigidbody system  

### Sample Code
```csharp
Vector3 velocity_ = rb.velocity;
float magneticFieldStrength = Mathf.Abs(controller.Horizontal * 0.2f);
Vector3 changingM_field = magneticF.normalized * magneticFieldStrength;

Vector3 magnetic_Force = q * Vector3.Cross(velocity_, changingM_field);
Vector3 elec_force = q * elec_f_strength * velocity_.normalized;

Vector3 tot_force = magnetic_Force + elec_force;
rb.AddForce(tot_force);
```

---

## 2. Booster and Relativistic Energy Calculation

The system includes a booster region where:
- Particle velocity thresholds trigger transitions  
- Relativistic energy is approximated using Lorentz factor  

### Energy Expression
$$
E = \gamma m c^2, \quad 
\gamma = \frac{1}{\sqrt{1 - (v/c)^2}}
$$

### Sample Code
```csharp
EnergyText.text = ((1 / Mathf.Sqrt(1 - (((float)v_c / (300)) * ((float)v_c / (300))))) * 938.272).ToString();
```

---

## 3. Drift Tube Linac (DTL) Simulation

A simplified DTL system is implemented using discrete acceleration gaps.

### Key Features
- Gap-based acceleration zones  
- RF field-driven sinusoidal electric field  
- Phase-dependent acceleration  

### RF Field Model
$$
E(t) = E_0 \sin(2\pi f t)
$$

### Sample Code
```csharp
float sd = Mathf.Sin(2 * Mathf.PI * rf_F * Time.time);
if(sd > 0)
{
    E_F = f_a * sd;
    movement.acc(E_F);
}
```

### Gap Detection Logic
```csharp
if(particleposition.z >= gap01.transform.position.z &&
   particleposition.z <= (gap10.transform.position.z + gaplength))
{
    inDTL = true;
}
```

---

## 4. Real-Time Data Visualization

A custom plotting system is implemented using Unity textures.

### Features
- Velocity vs time plotting  
- Acceleration tracking  
- Dynamic scaling and buffer control  

### Sample Code
```csharp
velos.Add(c_v_m * Scalee);

int y = Mathf.Clamp((int)velos[i], 0, t_H - 1);
plotT.SetPixel(i, y, Color.yellow);
plotT.Apply();
```

---

## 5. Computational Methods

- Numerical integration of motion equations (Runge–Kutta methods)  
- Vector-based force modelling  
- Real-time physics simulation using Unity engine  
- RF signal-based acceleration modelling  

---

## 6. Applications

This framework can be extended for:
- Accelerator physics education  
- Beam dynamics visualization  
- CERN-inspired simulation environments  
- Interactive computational physics tools  

---

## 7. Repository Scope and Protection

This repository provides a **demonstration of methodology and selected implementation components only**.

- Full simulation framework is under active development  
- Core architecture and extended features are not publicly available  
- Additional materials can be shared upon request for academic purposes  

---

## Keywords
Accelerator Physics, Beam Dynamics, Particle Simulation, Lorentz Force, RF Acceleration, Computational Physics, Unity 3D
