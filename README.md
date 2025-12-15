\# 🛠️ CPU Instruction Pipeline Simulator



!\[Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge\&logo=python\&logoColor=white)

!\[Jupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge\&logo=jupyter)

!\[Architecture](https://img.shields.io/badge/Arch-MIPS%20Pipeline-blueviolet?style=for-the-badge)



> \*\*A cycle-accurate simulator for a 5-stage RISC pipeline, implementing the Strategy Design Pattern to visualize Data Hazards and Operand Forwarding.\*\*



---



\## 📖 Project Overview

This project simulates the execution of assembly instructions through a standard 5-stage pipeline:

\*\*IF\*\* (Fetch) → \*\*ID\*\* (Decode) → \*\*EX\*\* (Execute) → \*\*MEM\*\* (Memory) → \*\*WB\*\* (Write Back).



The main objective is to analyze how \*\*Data Hazards\*\* (RAW dependencies) affect CPU performance and how \*\*Forwarding (Bypassing)\*\* techniques can resolve them to minimize pipeline stalls.



\### ✨ Key Features

\* \*\*Strategy Design Pattern:\*\* Used to implement flexible hazard resolution strategies (`NoForwarding` vs. `Forwarding`).

\* \*\*Visual Simulation:\*\* The Jupyter Notebook generates a Gantt-chart style timeline to visualize instruction overlap cycle-by-cycle.

\* \*\*Performance Analysis:\*\* Automatically calculates Total Cycles, Speedup, and Stalls Avoided.



---



\## 🏗️ Architecture \& Design

The project uses Object-Oriented Programming (OOP) to model the hardware components:



\* \*\*`Instruction`\*\*: Represents a single operation (Opcode, Destination, Source Registers).

\* \*\*`PipelineSimulator`\*\*: The core engine that advances instructions through stages.

\* \*\*`HazardResolver` (Abstract Strategy)\*\*:

&nbsp;   \* \*\*NoForwarding:\*\* Traditional approach; inserts Stalls (NOPs) when a dependency is detected.

&nbsp;   \* \*\*Forwarding:\*\* Optimized approach; bypasses the register file to forward data directly from EX/MEM stages.



---



\## 📊 Simulation Results



We compared the execution of a sample instruction sequence under both strategies to measure the impact of Forwarding.



| Strategy | Total Cycles | Stalls Avoided | Performance Impact |

| :--- | :--- | :--- | :--- |

| \*\*No Forwarding\*\* | \*\*15\*\* | — | Baseline (Slower execution due to stalls) |

| \*\*With Forwarding\*\* | \*\*11\*\* | \*\*4\*\* | \*\*~26% Faster\*\* |



> \*\*Conclusion:\*\* Implementing Forwarding successfully reduced the total execution time by eliminating 4 unnecessary stall cycles, proving its efficiency in handling Data Hazards.



---



\## 🚀 How to Run



1\.  \*\*Clone the repository:\*\*

&nbsp;   ```bash

&nbsp;   git clone \[https://github.com/seif1436/CPU-Pipeline-Simulator.git](https://github.com/seif1436/CPU-Pipeline-Simulator.git)

&nbsp;   cd CPU-Pipeline-Simulator

&nbsp;   ```



2\.  \*\*Install dependencies:\*\*

&nbsp;   ```bash

&nbsp;   pip install matplotlib

&nbsp;   ```



3\.  \*\*Run the Simulation:\*\*

&nbsp;   \* Open `src/Pipeline\_Simulator.ipynb` in \*\*Jupyter Notebook\*\* or \*\*VS Code\*\*.

&nbsp;   \* Run all cells to execute the simulation and view the visualization charts locally.



---



\## 📂 Project Structure

```text

CPU-Pipeline-Simulator/

├── src/

│   └── Pipeline\_Simulator.ipynb    # Main Simulation Logic \& Visualization

├── docs/

│   └── Project\_Presentation.pdf    # Detailed Project Report \& Slides

└── README.md                       # Documentation


👥 Team Members
Seif Eldin Mohamed

Mohamed Essam

Mohamed Medhat

Saeed Waled

Saeed Mahmoud

Supervised by: Prof. Dr. Hossam Reda Mohamed

<p align="center"> Made with ❤️ by Zagazig University Students </p>

