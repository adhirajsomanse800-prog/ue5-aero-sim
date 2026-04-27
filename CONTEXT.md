<img width="602" height="745" alt="image" src="https://github.com/user-attachments/assets/c9d64456-68b7-46be-8785-1061fd4463c6" />

HOW THIS SPILT ACTUALLY WORKS!
The key insight is that his Python work and your UE5 work are almost entirely independent until Phase 3, when the TCP socket bridge connects them. That's your integration point — everything before that, you're working in parallel with no blockers.
Phase 1 — you both do the same thing. Learn Python together. Same resources, same pace. Weekly sync call where you both run each other's scripts. This also means he understands the codebase when he takes ownership of it in Phase 2.
Phase 2 — you diverge. You go into UE5 editor, he goes deeper into Python. His job is to have the full aerodynamics model working in pure Python before you even need it in UE5 — so when you reach Phase 3 you're not waiting for the math, just plugging it in.
Phase 3 — the bridge is everything. He writes the TCP client, you write the TCP server in UE5. Define the message format together early (JSON probably) and don't change it without telling the other. Use GitHub properly here — branches, PRs, a shared README explaining the protocol.
Phase 4 — natural split. You focus on visual polish and the demo video render on RunPod. He owns PID and RL integration. These are genuinely parallel — the RL agent talks to your sim via the same TCP bridge you already built.

RESOURCES FOR RAJGURU ( BACKEND DEVELOPER )

CS Dojo / freeCodeCamp Python (Phase 1)
Anderson "Fundamentals of Aerodynamics" Ch 1–4 (free PDF online)
Python socket module docs (Phase 3 TCP work)
pandas + matplotlib docs for telemetry/CSV
Brian Douglas PID YouTube series (Phase 4)
Stable Baselines 3 docs + Sentdex RL series (Phase 4)

RESOURCES FOR ADHIRAJ ( UE5 DEVELOPER )

Unreal Sensei beginner course
Epic official learning portal
Matt Aspland Blueprints YouTube channel
ISRO Bhuvan portal for DEM data
UE5 Python API docs (for the socket server side)
