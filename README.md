# Real-Time Control of a Phase-Controlled SCR Rectifier
### Model-Based Design (MBD) and Embedded C-Code Generation



##  Overview
This project implements a **Single-Phase Controlled Half-Wave Rectifier** using a Silicon Controlled Rectifier (SCR). The primary focus is the development of a robust firing-angle control system ($\alpha$) using **MATLAB/Simulink**. 

By leveraging **Model-Based Design**, this project demonstrates the workflow of taking a power electronics mathematical model and generating optimized, MISRA-C compliant code for deployment on a real-time embedded microcontroller.

##  Technical Specifications
* **System Frequency:** 60 Hz ($T = 0.01667$ s)
* **Control Method:** Phase-Angle Triggering
* **Target Hardware:** Fixed-step Discrete Solver
* **Sample Time ($T_s$):** $1 \times 10^{-5}$ s ($10 \mu\text{s}$)
* **Phase Shift Logic:** Sample-based delay calculation ($0^\circ$ to $180^\circ$)

##  Firing Angle Logic & Math
To ensure precise triggering in an embedded environment, the phase delay is converted from degrees to discrete samples based on the system frequency and solver step size:

$$Samples = \frac{\alpha \times (1/f)}{360 \times T_s}$$

For a **60 Hz** signal at a **10 $\mu\text{s}$** sample rate:
* **$0^\circ$ Delay:** 0 samples (Full conduction)
* **$90^\circ$ Delay:** $\approx 417$ samples
* **$180^\circ$ Delay:** $\approx 833$ samples (Theoretical extinction)


##  Key Learning Outcomes (EE + Software Integration)
1.  **Synchronization:** Implementing Zero-Crossing Detection (ZCD) to synchronize the gate pulse with the AC mains frequency.
2.  **Timing Constraints:** Managing sample-time mismatches between the high-speed controller logic and the physical simulation solver.
3.  **Embedded Deployment:** Preparing the model for Hardware-in-the-Loop (HIL) testing by enforcing strictly discrete-time blocks and fixed-point arithmetic readiness.

##  Future Work
* Uploaded generated C code

---
**Author:** Jaime Vargas  
**Focus:** Power Electronics | Embedded Systems | ASIC/VLSI Design
