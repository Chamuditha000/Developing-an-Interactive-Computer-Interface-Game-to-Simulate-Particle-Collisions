## 📊 Results and Discussion

The main aim of the study was to design an **interactive interface/game** to simulate:

- Beam acceleration  
- Proton-proton collision  
- CMS detector mechanisms

---

### ⚡ Beam Acceleration Simulation

- **Linac-4:** Simulated the motion of negative hydrogen ions using varying electric field waveforms. The player controls frequency.
- **PSB (Proton Synchrotron Booster):** Simulated using the Lorentz force. Player adjusts magnetic fields to maintain constant radius.
- **PS, SPS, and LHC:** Used the same control algorithm. The LHC includes two beam pipes; players choose the direction for the proton.
- **Simplification:** Velocity was scaled at **1:10⁶** to simplify computations and enhance performance.

---

### 💥 Collision and CMS Simulation

- **Particle Generation:** Based on physics theories such as energy-momentum conservation and particle interaction rules.
- **Motion Simulation in CMS:** Magnetic field effects simulate a superconducting solenoid.
- **Detection Algorithms:** Used vector products and bending direction logic for curvature detection.
- **Energy Deposition:** Assigned based on particle type.
- **Visualization Tools:**
  - Real-time **velocity vs time** graph
  - **Energy tracking** UI from Linac-4 to LHC

---

### 🧩 Limitations and Simplifications

#### Linac-4:
- Complex structures like **RFQ, DTL, PI-mode** were not fully simulated.
- Only **acceleration** (not focusing) mechanisms were included.
- **Pre-workflows** (necessary but beam-independent) were skipped.

#### PS Booster:
- Full simulation of 16 periods with 21 components each (RF cavities, beam monitors, etc.) was too complex.
- Designed a simplified **approximate 3D model** of the full ring.
- Used the same motion algorithm for all four rings.

#### PS & SPS:
- Replaced full dipole/RF structures with approximate models:
  - **8 dipoles + RFQs** for PS
  - **16 dipoles + RFQs** for SPS
- Reused PS Booster's motion algorithm.

#### LHC:
- Modeled with **two intersecting pipes** at 4 collision points.
- Omitted internal components like superconducting magnets for simplicity.

#### CMS Detector:
- Real workflows involve advanced physics: **spallation, bremsstrahlung, pair production**, etc.
- These were too performance-heavy for real-time Unity simulation.
- Designed a **simplified detector** preserving core physics interactions and signature identification.

---

### ✅ Summary

This project successfully built an interactive simulation of the **CERN accelerator chain and CMS detector**, applying core **electromagnetic and particle physics** principles. While technical limitations led to simplifications, the final product delivers an informative and engaging visualization tool for education, research, and skill development.
