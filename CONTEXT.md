# UE5 Aerospace Simulation Platform — Project Context

> Paste this at the start of any Claude chat to load full project context.

---

## Who We Are

| Person | Role |
|--------|------|
| **Adhiraj** | Project lead — UE5, Blueprints, 3D engine, terrain, rendering |
| **Rajguru** | Python & Research Engineer — aerodynamics, TCP bridge, telemetry, PID, RL |

17–18 year old students from Goa, India. Starting First Year engineering in ~2 months. Goal: build an impressive open-source project over 18 months to land a research internship at IIT Bombay, IIT Kanpur, IIT Madras, or IIST Trivandrum aerospace/UAV labs.

---

## What We Are Building

A dual-purpose aerospace flight simulation platform built in Unreal Engine 5, inspired by Prepar3D.

### Three main screens

| Screen | Description |
|--------|-------------|
| Cockpit view | Third-person flight with HUD, live instruments, real Indian terrain |
| Mission planner | Top-down map, clickable waypoints, autonomous route execution |
| Telemetry dashboard | Live flight data, CSV export, Python API connection for ML research |

### Two vehicles
- Fixed-wing aircraft
- Multirotor drone / UAV

### Two modes
- **Civilian** — pilot training, drone operations
- **Defense / Research** — autonomous missions, sensor fusion, obstacle avoidance

---

## Why This Is Research-Relevant

- Built on real Indian terrain data from ISRO Bhuvan (DEM heightmaps)
- Python API bridge via TCP socket — external scripts can command the vehicle, log data, plug in ML models
- PID autopilot implemented in Python
- Reinforcement learning hookup via Stable Baselines 3 (Phase 4)
- Fully open source on GitHub

---

## Hardware

| Machine | Specs | Purpose |
|---------|-------|---------|
| Local laptop | Ryzen 7 4800H · RTX 3050 4GB · 8GB RAM | Build and test daily |
| RunPod cloud | RTX 3090 (~₹30/hr) | Heavy scene testing, final demo renders |
| Rajguru's laptop | i3 11th Gen · Intel UHD · 8GB RAM | Python only — no UE5 |

> Local target: 60fps on low settings with DLSS Performance mode.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Simulation engine | Unreal Engine 5 (Blueprints primary, C++ if needed) |
| Renderer | Forward renderer · DLSS on · Lumen off · Nanite off |
| Aerodynamics | Standard lift/drag/thrust equations (not CFD) |
| Python bridge | TCP socket · UE5 Python API |
| Autopilot | PID controller in Python |
| ML / RL | Stable Baselines 3 |
| Version control | Git + GitHub (from day one) |
| Not using | OpenFOAM, MATLAB |

---

## Aerodynamics Approach

Standard equations only — no CFD.

```
Lift    = ½ρv²SC_L
Drag    = ½ρv²SC_D
Thrust  = engine force (simplified)
```

Math reference: Anderson — *Fundamentals of Aerodynamics*, Chapters 1–4 only.

---

## 18-Month Roadmap

### Phase 1 — Months 1–3
**Learn Python and Git basics**

| Adhiraj | Rajguru |
|-----|---------|
| Python from scratch | Python from scratch |
| CS Dojo · freeCodeCamp · Kaggle | Same resources — sync weekly |
| Git + GitHub setup | Git + GitHub setup |

> **Milestone:** Projectile motion simulator in Python with matplotlib plot

---

### Phase 2 — Months 3–7
**You learn UE5. Rajguru builds the Python aerodynamics model.**

| Adhiraj | Rajguru |
|-----|---------|
| UE5 editor basics | Anderson Ch 1–4 (math background) |
| Blueprints fundamentals | Lift / drag / thrust in Python |
| Basic 3D pawn + landscape | matplotlib flight sim plots |
| Unreal Sensei · Matt Aspland (YouTube) | Unit tests for aero equations |

> **Milestone:** Controllable 3D pawn moving through a landscape · Python aero equations verified

---

### Phase 3 — Months 7–13
**Build the actual simulation. Connect Python to UE5.**

| Adhiraj | Rajguru |
|-----|---------|
| Chaos Physics + custom aero forces | TCP socket client (Python side) |
| ISRO Bhuvan terrain heightmaps | Real-time telemetry logger |
| Cockpit HUD + waypoint mission planner | CSV export + data visualisation |
| Sensor raycasts in Blueprints | GitHub: branches, PRs, documentation |
| TCP socket server in UE5 | Write-up of Python API protocol |

> **Milestone:** Fixed-wing aircraft flying over Indian terrain, fully commandable via Python script

---

### Phase 4 — Months 13–18
**PID autopilot, reinforcement learning, polish, demo.**

| Adhiraj | Rajguru |
|-----|---------|
| Visual polish + UI refinement | PID autopilot (Brian Douglas YT series) |
| RunPod demo video render | Stable Baselines 3 RL integration |
| GitHub README + screenshots | Sentdex Python RL series |
| Cold email IIT professors | Python API technical write-up |

> **Milestone:** Full demo video · open source repo · research outreach to IIT labs

---

## Resources

### Adhiraj (UE5 focus)
- [Unreal Sensei beginner course](https://www.youtube.com/@UnrealSensei)
- [Epic official learning portal](https://dev.epicgames.com/community/learning)
- [Matt Aspland Blueprints channel](https://www.youtube.com/@MattAspland)
- [ISRO Bhuvan DEM data](https://bhuvan.nrsc.gov.in)
- UE5 Python API docs (for TCP server side)

### Rajguru (Python focus)
- [CS Dojo Python](https://www.youtube.com/@CSDojo)
- [freeCodeCamp Python](https://www.freecodecamp.org)
- [Kaggle Python course](https://www.kaggle.com/learn/python)
- Anderson — *Fundamentals of Aerodynamics* Ch 1–4
- Python `socket` module docs
- `pandas` + `matplotlib` docs
- [Brian Douglas PID series](https://www.youtube.com/@BrianBDouglas) (Phase 4)
- [Stable Baselines 3 docs](https://stable-baselines3.readthedocs.io) (Phase 4)
- [Sentdex RL series](https://www.youtube.com/@sentdex) (Phase 4)

### Both
- Git + GitHub (set up in Phase 1)
- [learncpp.com](https://www.learncpp.com) (reference only, if needed)

---

## Target Labs (Year 2 outreach)

| Institute | Lab |
|-----------|-----|
| IIT Bombay | Unmanned Systems Lab |
| IIT Kanpur | Aerospace Engineering dept |
| IIT Madras | NCCRD |
| IIST Trivandrum | Defense-adjacent by design |

---

## TCP Protocol (agreed format — do not change without discussion)

```json
{
  "command": "set_throttle",
  "value": 0.75,
  "timestamp": 1234567890
}
```

Rajguru owns the Python client. You own the UE5 server. Message format is the handshake — agree before coding, version it in this file if it changes.

---

## Current Status

Not started. About to begin Phase 1 — learning Python from scratch before college starts.
