# Game Design Document (GDD)
**Project:** Rachel Robot Mini-Games — *Cornhole* and *Disc Golf*  
**Author:** Temi Akinlade  
**Lab:** BioAdaptive Interfaces Lab  
**Date:** November 2025  

---

## 1. Overview

### Introduction
The **Rachel Robot Mini-Games** project is a suite of short, physically interactive Unity games controlled through the **Rachel** social robot system.

Rachel:
- listens to voice commands,
- responds with speech and LED feedback,
- and launches mini-games on request (e.g. **“Play Cornhole.”**).

### Current Mini-Games
- **Cornhole** — beanbag toss focused on *aim and precision*.
- **Disc Golf** — disc throw focused on *trajectory and control*.

The system is **modular**, so future titles can plug into the same robot–Unity pipeline.

---

## 2. Game Structure

### Control
Players interact with the system through:
- **Voice commands** (to Rachel),
- or **hand-tracking / in-scene UI** (inside Unity).

**Rachel handles:**
- game start / end,
- LED color cues,
- speech feedback (e.g. “Nice shot!”, “Try again!”).

### Scoring
- Each game tracks successful hits/goals.
- Score is shown on screen (Unity UI).
- Score events trigger robot reactions:
  - **Blue** LED for success
  - **Red** LED for miss

---

## 3. Game Mechanics

### A. Cornhole

**Objective:**  
Toss beanbags into the hole on the board within a time or attempt limit.

**Core Mechanics:**
- Player throws beanbags using **hand tracking**.
- Each throw uses Unity physics (mass, gravity, drag).
- **Scoring:**
  - Bag in hole → **+3 points**
  - Bag on board → **+1 point**
  - Miss → robot shows red LED
- **FX:** confetti + SFX on successful throws.

**Robot Integration:**
- Rachel turns **blue** for a score, **red** for a miss.
- Speech feedback: “Great shot!”, “That was close.”

**Gameplay Loop:**
1. Rachel announces start.
2. Player throws.
3. System checks collision.
4. Score is updated; robot reacts.
5. Round ends with Rachel’s verbal summary.

---

### B. Disc Golf

**Objective:**  
Toss a flying disc toward a distant goal and score by hitting the goal area.

**Core Mechanics:**
- Disc spawns in front of the player/camera.
- Player performs a *backhand-style toss*.
- Disc flight uses Unity physics (spin, drag, gravity).
- Player re-throws from last position if miss.
- If disc enters goal trigger → score.
- After scoring → game resets.

**Robot Integration:**
- **Blue** LED for goal.
- **Red** LED for miss.
- Verbal praise at milestones (e.g. “Nice drive!”).

**Gameplay Loop:**
1. Rachel announces start.
2. Disc spawns.
3. Player tosses.
4. Collision with goal → score + robot feedback.
5. Game continues until target score / end command.

---

## 4. Actions

| Action            | Description                                             |
|-------------------|---------------------------------------------------------|
| **Throw**         | Player tosses beanbag or disc toward target.           |
| **Voice Command** | Player talks to Rachel (“Start Cornhole”, “End game”). |
| **Scoring Reaction** | Rachel changes LED color + speaks feedback.         |
| **Restart**       | Rachel resets game state for next player/session.      |

---

## 5. Robot–Game Interface

| Event        | Robot Response                                    |
|--------------|---------------------------------------------------|
| **Start Game** | LED: **Yellow**; Speech: “Let’s begin!”         |
| **Scored**     | LED: **Blue**; Speech: “Nice one!”              |
| **Missed**     | LED: **Red**; Speech: “Almost there!”           |

- Robot communication is handled through **`RobotBridge.cs`**, which maps Unity game events → Raspberry Pi robot commands.
- This allows the game to stay in Unity while the robot handles lights, speech, and physical presence.

---

## 6. Technical

| Component    | Description                                  |
|--------------|----------------------------------------------|
| **Engine**   | Unity **2022 LTS**                           |
| **Hardware** | Rachel Robot + **Raspberry Pi** controller   |
| **Body Tracking** | MediaPipe (Unity integration)          |
| **Voice System**  | Vosk (for voice commands)               |
| **Output**        | LED feedback, audio, screen display     |

---

## 7. Gameplay Storyboard

1. Player stands in front of Rachel.
2. Player says: **“Play Cornhole.”**
3. Rachel lights up and starts the round.
4. Player tosses a beanbag → it lands in the hole.
5. Rachel glows **blue** and says: **“Perfect shot!”**
6. Next toss misses → Rachel flashes **red**, then returns to neutral.
7. At the end of the round, Unity shows summary/menu.
8. Player says: **“Play Disc Golf.”**
9. Rachel switches context and launches the Disc Golf mini-game.

---

## 8. Design Goals

- **Social Interaction:** voice-driven, robot as companion/host.
- **Physical Engagement:** promote motion, aim, coordination.
- **Immediate Feedback:** LEDs, audio, confetti/SFX.
- **Expandability:** same pattern can support future mini-games.

---

## 9. Future Development

- Add global scoreboard and difficulty levels.
- Allow Rachel to *set / adjust* difficulty.
- Improve pose detection robustness.
- Add more outdoor-/activity-themed mini-games.

---

**Lead Designer / Developer:** *Temi Akinlade*  
**Supervisor:** *Dr. John Muñoz*  
**Lab:** BioAdaptive Interfaces Lab, Wilfrid Laurier University
