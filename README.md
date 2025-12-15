# 🚀 CPU Instruction Pipeline Simulator

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=jupyter)
![Architecture](https://img.shields.io/badge/Arch-MIPS%20RISC-blueviolet?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> **A cycle-accurate simulator for a 5-stage RISC pipeline. It visualizes Data Hazards and demonstrates the performance boost of Operand Forwarding using the Strategy Design Pattern.**

---

## 📖 Table of Contents
- [Project Overview](#-project-overview)
- [Pipeline Architecture](#-pipeline-architecture)
- [Software Design (Strategy Pattern)](#-software-design-strategy-pattern)
- [Performance Results](#-performance-results)
- [How to Run](#-how-to-run)
- [Team Members](#-team-members)

---

## 📌 Project Overview

In high-performance computing, **Pipelining** is key to speed. This project simulates how a CPU executes instructions by breaking them into 5 stages.

It specifically addresses **Data Hazards (RAW)**—when an instruction needs data that hasn't been written back yet. We implemented two strategies to handle this:
1.  **Stalling (No Forwarding):** The safe, slow way (Waiting).
2.  **Forwarding:** The smart, fast way (Bypassing memory).

---

## 🏗️ Pipeline Architecture

The simulator moves instructions through the following standard RISC stages:

```mermaid
graph LR
    A[IF <br> Fetch] --> B[ID <br> Decode]
    B --> C[EX <br> Execute]
    C --> D[MEM <br> Memory]
    D --> E[WB <br> Write Back]
    style A fill:#4e79a7,stroke:#333,stroke-width:2px,color:white
    style B fill:#f28e2b,stroke:#333,stroke-width:2px,color:white
    style C fill:#59a14f,stroke:#333,stroke-width:2px,color:white
    style D fill:#e15759,stroke:#333,stroke-width:2px,color:white
    style E fill:#76b7b2,stroke:#333,stroke-width:2px,color:white
IF: Fetch instruction from memory.ID: Decode & read registers.EX: Calculate (ALU operation).MEM: Read/Write to data memory.WB: Write result to register file.🧩 Software Design (Strategy Pattern)To make the code modular and clean, we used the Strategy Design Pattern. This allows us to switch hazard handling logic dynamically without changing the core simulator code.مقتطف الرمزclassDiagram
    class PipelineSimulator {
        +run()
        +step()
    }
    class HazardResolver {
        <<Abstract>>
        +should_stall()
    }
    class NoForwarding {
        +should_stall()
    }
    class Forwarding {
        +should_stall()
    }

    PipelineSimulator --> HazardResolver : uses strategy
    HazardResolver <|-- NoForwarding : inherits
    HazardResolver <|-- Forwarding : inherits
📊 Performance ResultsWe benchmarked a sample instruction sequence with dependencies (RAW) to compare the two strategies.Metric🐢 No Forwarding🐇 With Forwarding🟢 ImprovementTotal Cycles15 Cycles11 CyclesFasterStalls Incurred4 Stalls0 StallsNo WaitingThroughputLowerHigher~26% BoostAnalysis: By using Forwarding, we eliminated the need to wait for the Write-Back stage, allowing dependent instructions to execute immediately using data from the ALU output.🚀 How to RunClone the repository:Bashgit clone [https://github.com/seif1436/CPU-Pipeline-Simulator.git](https://github.com/seif1436/CPU-Pipeline-Simulator.git)
cd CPU-Pipeline-Simulator
Install dependencies:Bashpip install matplotlib
Run the Simulation:Open src/Pipeline_Simulator.ipynb in Jupyter Notebook or VS Code.Run all cells to see the Gantt Chart Visualization and detailed logs.👥 Team MembersNameRoleSeif Eldin MohamedLead Developer & ArchitectureMohamed EssamImplementation LogicMohamed MedhatResearch & TestingSaeed WaleedData AnalysisSaeed MahmoudDocumentationSupervised by: Prof. Dr. Hossam Reda Mohamed<p align="center">Made with ❤️ by Zagazig University Students | HPC Course 2025</p>
### إيه المميز في النسخة دي؟ ✨

1.  **Mermaid Diagrams:** الرسومات اللي جوه (المربعات الملونة وشجرة الكلاسات) دي مش صور، ده كود هيتحول لرسمة أول ما ترفع على GitHub، فمستحيل تطلع مكسورة\!
2.  **Organization:** قسمتلك الدنيا جداول وعناوين واضحة.
3.  **Visuals:** حطيت أيقونات (🐢 للبطيء و 🐇 للسريع) عشان تكسر جمود النص.

خدها Copy وحطها في ملف الـ `README.md` وارفع، وهتدعيلي\! 🚀
