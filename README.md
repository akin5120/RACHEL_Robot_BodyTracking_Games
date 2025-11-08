#  Project RACHEL: Social Robot for Active Aging

![Cornhole Banner](docs/banner.png)

**Role:** Lead UX Designer · Game Designer · Developer  
**Team:** 1 Director · 1 Software Engineer · 1 Mechanical Engineer · Me  
**Tools:** Unity · C# · MediaPipe Unity Plugin · Vosk (Voice Command) · Blender · Figma  
**Year:** 2025  

---

##  Overview
Project **RACHEL** is a social robot designed to encourage **active aging** through movement and play.  
The system combines **body tracking**, **voice recognition**, and **game-based interaction** to engage older adults in light physical activity.

I served as **Lead UX Designer, Game Designer, and Developer**, responsible for the full end-to-end design — from gameplay concepts and interface design to technical implementation in Unity.

---

##  Vision
We wanted to build a robot that felt more like a *companion* than a device — one that could motivate users to move through simple, joyful games.

**Core Goals**
- Encourage movement through play  
- Respond naturally to body gestures and voice commands  
- Run autonomously on the robot without external scripts  

---

##  My Role
I owned the design and development process end-to-end:
- Concepted and prototyped multiple **movement-based mini-games**  
- Designed **diegetic UI** elements to keep focus inside the game world  
- Integrated **MediaPipe Unity Plugin** for real-time body tracking  
- Added **Vosk** voice command system for hands-free interaction  
- Conducted **playtests** to refine usability and engagement  

---

##  Design Evolution

### Phase 1 — Garden Games
The first iteration centered around garden-themed tasks (watering, picking, reaching).  
It was calming but exposed key tracking challenges:
- Arm tracking was strong; **legs were harder to track accurately**  
- **Low light and multiple users** affected stability  
- Players needed clear visual feedback to feel confident  

| ![Old Ui](docs/oldui.png) | User Interface Earlier Iteration |

### Phase 2 — Outdoor Mini-Games
Based on feedback, we pivoted to **Cornhole** and **Disc Golf**, drawing inspiration from familiar outdoor leisure activities.  
These were easier to understand and provided more precise movement goals.

| ![UI](docs/ui.png) | User Interface |

Each mini-game featured:
- A **goal-based progression system**
- **Audio feedback** for hits and misses  
- **Score tracking and adaptive difficulty**  

---

##  Technical Implementation

### MediaPipe Body Tracking
Originally, body tracking ran through a Python UDP bridge, but this wasn’t ideal for a standalone robot.  
I transitioned to **MediaPipe Unity**, which captures webcam input directly inside Unity.

| ![Bodytracking Test](docs/balloon.gif) | Cornhole mini-game in Unity |

**How it works:**
1. Unity accesses the robot’s webcam.  
2. MediaPipe extracts 33 body landmarks (shoulders, elbows, wrists, knees, etc.).  
3. I map these landmarks to Unity transforms, triggering events like “throw” or “swing.”  

**Key Challenges**
- **Leg jitter** → solved with smoothing algorithms.  
- **Lighting sensitivity** → adjusted exposure dynamically.  
- **Multi-person detection** → filtered to the nearest skeleton.  

### Voice Interaction
Using **Vosk**, RACHEL recognizes offline commands like:
```
"Start game"
"Pause"
"Exit"
```
These commands drive the gameplay flow, allowing full hands-free interaction.

---

##  Playtesting Insights
One early prototype used a slider bar to time throws.  
Testers focused on the UI instead of the motion itself.

**Solution:** replaced on-screen sliders with **diegetic visual cues** (wind grass) to keep attention in the 3D space.

---

##  Outcome
-  Two working mini-games (Cornhole + Disc Golf)
-  Fully functional Unity body tracking and voice input system
-  Ethics-approved research version ready for participant testing
-  Publicly demoed at **AGE-WELL 2025 Conference** in Montreal  

| ![Age-Well](docs/gameplay.png) | AGE-WELL 2025 Conference |
---

##  Reflection
Designing RACHEL taught me how to build **player-centered, embodied experiences** — where the interface isn’t just a screen, but the human body itself.

It strengthened my ability to:
- Balance **fun and usability**  
- Work in **agile, cross-disciplinary teams**  
- Combine **UX principles with technical execution**

---

##  Keywords
UX Design · Game Design · Unity · C# · MediaPipe · Voice Interaction · Exergames · Human-Robot Interaction · Accessibility · Active Aging  

---


**Developed by:** [Temijuyin Akinlade](https://www.linkedin.com/in/temijuyin)  
© 2025 BioAdaptive Lab · Unity · AGE-WELL Network
