# Layered SystemVerilog Verification Environment for a Synchronous D Flip-Flop

## 📌 Project Purpose & Overview
The purpose of this project is to build a robust, production-grade **Layered Verification Testbench** from scratch using **SystemVerilog** to fully validate a synchronous **D Flip-Flop (DFF)** Design Under Test (DUT). 

While a D Flip-Flop is architecturally simple, verifying it using modern **Object-Oriented Programming (OOP)** principles demonstrates a deep understanding of industry-standard verification methodologies used for complex SoCs. This project strictly decouples stimulus generation, bus driving, passive signal monitoring, and automated scoreboard checking using transaction-level mailboxes and strict clock-cycle handshakes.

---

## 📂 Included Project Artifacts
This repository contains a comprehensive suite of verification deliverables. You can review them across the following files:
1. **`dff.sv`**: The hardware implementation of the synchronous D Flip-Flop using a SystemVerilog Interface wrapper.
2. **`testbench.sv`**: The complete Object-Oriented verification environment (Transaction, Generator, Driver, Monitor, Scoreboard, and Environment classes).
3. **`D_FF_Verification_Summary.txt`**: A plaintext architectural summary and simulation log exegesis for terminal-based review.
4. **`wawveform.png`**: High-resolution EPWave simulation waveforms demonstrating cycle-accurate, edge-triggered state propagation.
5. **Live Interactive Simulation Link**: [Execute & Run Live on EDA Playground](https://edaplayground.com/x/KR3w)

---

## 🏗️ Verification Testbench Architecture
The testbench follows a clean, layered architecture to isolate responsibilities and eliminate simulation deadlocks or race conditions:

```text
[Generator] --(Mailbox)--> [Driver] --------> (vif.din Pin) -------> [ DUT ]
     |                                                                 |
 (Mailbox)                                                       (vif.dout Pin)
     |                                                                 |
     v                                                                 v
 [Scoreboard] <----------- (Mailbox) <----------- [Monitor] <----------+
