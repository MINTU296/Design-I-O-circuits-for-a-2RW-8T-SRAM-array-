# 2RW 8T SRAM Array I/O Circuit Design

This project focuses on the design and implementation of Input/Output (I/O) circuits for a **2 Read/Write (2RW) 8T Static Random-Access Memory (SRAM)** array. The primary goal is to develop high-performance, robust, and area-efficient I/O circuits—namely, a **Precharge Circuit**, a **Write Driver**, and a **16:1 Multiplexer**—to meet stringent timing requirements under worst-case Process-Voltage-Temperature (PVT) conditions.

---

## 📌 Project Overview

### Objective
Design optimized I/O circuits for an 8T 2RW SRAM array with:
- **512 rows**, each contributing **0.5 fF** of parasitic capacitance.
- Functional performance under **SS corner**, **1.08 V supply voltage**, and **125°C temperature**.

### Key Components Designed
1. **Precharge Circuit**
   - Fully charges **bitlines (BL and BLB)** to **VDD** within **250 ps**.
   - Ensures equal voltage levels on both bitlines to prevent read/write errors.

2. **Write Driver**
   - Discharges **BL or BLB** within **100 ps**.
   - Implements **fingering technique** to reduce transistor area while maintaining speed.
   - Includes **cross-coupled PMOS** to assist in write operations.

3. **16:1 Multiplexer**
   - Two-stage design: **4:1 Tree MUX** followed by a **conventional MUX**.
   - Minimizes **parasitic capacitance**, **stack effect**, and layout area.
   - Optimized for **low delay** and **high signal integrity**.

---

## 🔧 Technical Highlights

### Precharge Circuit
- **PMOS Size**: 6.2 µm
- Achieves **full VDD precharge** in **246 ps** under SS, 1.08 V, 125°C condition.
- Balanced node charging ensures **no voltage skew**, enabling reliable SRAM operation.

### Write Driver
- **Inverter Stage**: PMOS/NMOS = 12 µm / 8 µm
- **Output Stage**: NMOS = 15 µm, PMOS = 8 µm
- Achieves **discharge time of 96 ps**, meeting the 100 ps requirement.
- Utilizes **transistor fingering** to maintain performance with reduced area.

### 16:1 Multiplexer
- **Stage 1 (Tree MUX)**:
  - MUX Transistors: 3 µm
  - Inverter: 1.4 µm / 0.7 µm
- **Stage 2 (Conventional MUX)**:
  - Inverter: 1.4 µm / 0.7 µm
  - MUX Transistors: 5 µm / 5 µm
- Propagation delay of **14 ps** under worst-case PVT.

---

## 🧪 Verification & Simulation Results

All designs were verified through:
- **Schematic-level simulations** using Cadence Virtuoso.
- **Layout extraction** and **post-layout simulations**.
- **LVS (Layout vs Schematic)** and **DRC (Design Rule Check)** clean.

### Performance Summary
| Block | Parameter | Worst-case (SS, 1.08V, 125°C) |
|-------|-----------|-------------------------------|
| Precharge Circuit | Charging Time | 246 ps |
| Write Driver | Discharge Time | 96 ps |
| MUX Stage 1 | Propagation Delay | 14 ps |

### Power & Leakage
- Low leakage current across corners (< 1 µA in typical cases).
- Static power consumption remains minimal due to careful transistor sizing and layout optimizations.

---

## 📐 Layout Implementation

- Full layout of all blocks completed in **Cadence Virtuoso**.
- Emphasis on compactness, symmetry, and routing efficiency.
- Techniques like **multi-finger transistors**, **device sharing**, and **tree-based structures** were employed for area and performance optimization.

---

## 🎯 Conclusion

This project demonstrates a comprehensive approach to designing high-speed, low-power I/O circuits for SRAM arrays. Through innovative circuit techniques such as **fingering**, **tree multiplexing**, and **cross-coupled boosting**, we achieved timing closure under worst-case PVT conditions while keeping area and power at bay.

---

## 🚀 Future Work

Potential enhancements include:
- Further reducing **delay**, **stack effect**, and **parasitic capacitance**.
- Exploring **dynamic finger segmentation** and **reconfigurable multiplexers**.
- Investigating optimal placement of **write drivers** between MUX stages.

---

## 👥 Team Members

- **Mintu Kumar** – Schematic & Layout (Precharge + Write Driver+mux)
- **Aman Kumar** – Schematic & Layout (Column MUX + ADEL), Simulations
- **Dhruv Sharma** – Schematic & Simulation (Write Driver + X-Circuit)
- **Noorain Ansari** – Presentation & Documentation
