# UE5 Aerospace Simulation Platform ✈️

A high-fidelity bridge between **Unreal Engine 5** and **Python**, designed for aerospace research and autonomous flight development.

## 📌 Project Overview
Built on real-world Indian terrain data (ISRO Bhuvan), this platform enables real-time flight simulation with an external Python API for PID control, telemetry analysis, and future Reinforcement Learning research.

## 📂 Repository Structure
| Folder | Contents |
| :--- | :--- |
| **`/sim`** | UE5 project, 3D assets, and terrain levels. |
| **`/python`** | TCP Client, Aerodynamics logic, and Autopilot scripts. |
| **`/docs`** | Research notes and IIT Internship pitch materials. |
| **`/data`** | Telemetry logs and exported flight CSV data. |

## 👥 The Team
| Name | Role |
| :--- | :--- |
| **Adhiraj Somanse** | Project Lead — UE5, Blueprints, Rendering |
| **Rajguru&nbsp;Kudnekar** | Research Systems — Python, Aero-physics, TCP |

## 🛠 Tech Stack
* **Engine:** Unreal Engine 5 (DLSS Enabled)
* **API:** Python 3.10+ via TCP Socket
* **Terrain:** ISRO Bhuvan DEM Data
```mermaid
graph LR
    subgraph UE5 ["🖥️ Unreal Engine 5 Server"]
        A[Chaos Physics Engine] --> B[Telemetry Generator]
        B -->|JSON| C((● TCP Server))
        D((● TCP Server)) -->|Command| A
    end

    subgraph Python ["🐍 Python Control Brain"]
        E((○ TCP Client)) -->|Telemetry| F[Research Logic/RL]
        F -->|JSON| G((○ TCP Client))
    end

    %% Flow Connections
    C -.->|60Hz Data| E
    G -.->|60Hz Ctrl| D

    %% --- GITHUB NATIVE STYLING ---
    %% We use 'fill:none' so it matches GitHub's background perfectly
    style UE5 fill:none,stroke:#38bdf8,stroke-width:1px,stroke-dasharray: 5 5
    style Python fill:none,stroke:#fbbf24,stroke-width:1px,stroke-dasharray: 5 5

    classDef ue5Node fill:#1e293b,stroke:#38bdf8,stroke-width:2px,color:#38bdf8
    classDef pyNode fill:#1e293b,stroke:#fbbf24,stroke-width:2px,color:#fbbf24
    classDef socket fill:#0f172a,stroke:#a78bfa,stroke-width:2px,color:#a78bfa

    class A,B ue5Node
    class F pyNode
    class C,D,E,G socket
```
