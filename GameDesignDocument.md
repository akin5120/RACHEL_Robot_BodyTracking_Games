Game Design Document (GDD) 

Rachel Robot Mini-Games: Cornhole and Disc Golf 

Author: Temi Akinlade 
Lab: BioAdaptive Interfaces Lab 
Date: November 2025 

 

1. Overview 

Introduction 

The Rachel Robot Mini-Games project is a suite of short, physically interactive Unity games controlled through the Rachel social robot system. Rachel listens, responds, and launches games via voice commands (e.g., “Play Cornhole”). 

The current suite includes: 

Cornhole: A beanbag-toss game of aim and precision. 

Disc Golf: A disc-throwing game emphasizing trajectory and control. 

Future titles will build on this modular structure. 

 

2. Game Structure 

Control 

Players interact through voice commands or hand tracking UI. 

Rachel handles: 

Game start and end 

LED color cues 

Speech feedback (“Nice shot!” or “Try again!”). 

Scoring 

Each game tracks successful hits or goals. 

Score is displayed on-screen and triggers robot responses. 

Rachel lights blue for success or red for a miss. 

3. Game Mechanics 

A. Cornhole 

Objective: Toss beanbags into a hole on the board within a time limit. 

Core Mechanics: 

Players throw beanbags using hand-tracking. 

Each throw applies real physics (mass, gravity, drag). 

Bags that land inside the hole = +3 point. 

Bags that land on the board = +1 point. 

Bags that miss trigger a red LED flash. 

Confetti and sound effects celebrate each successful throw. 

Robot Integration: 

Rachel turns blue for a score, red for a miss. 

Speech feedback (e.g., “Great shot!”). 

Loop: 

Rachel announces start  

Player throws  

System checks collision  

Score and feedback  

Round ends with Rachel’s summary. 

 

B. Disc Golf 

Objective: Toss a flying disc toward a distant goal and aim for accuracy. 

Core Mechanics: 

Disc spawns directly in front of the camera. 

Player performs a “backhand toss” to launch. 

Disc’s flight path uses Unity’s physics (spin, drag, gravity). 

Player toss again from position of last disc drop. 

If the disc enters the goal area, player scores. 

After scoring, the game resets. 

Robot Integration: 

Blue LED for goal, red for miss, verbal praise at milestones. 

Loop: 

Rachel announces start. 

Disc spawns. 

Player tosses. 

Collision with goal triggers score + robot feedback. 

Game continues until target score. 

 

4. Actions 

Action 

Description 

Throw 

Player tosses beanbag or disc toward target. 

Voice Command 

Player talks to Rachel (“Start Cornhole”, “End game”). 

Scoring Reaction 

Rachel changes LED color and speaks feedback. 

Restart 

Rachel resets game state for next player. 

 

5. Robot-Game Interface 

Event 

Robot Response 

Start Game 

LED: Yellow, Speech: “Let’s begin!” 

Scored 

LED: Blue, Speech: “Nice one!” 

Missed 

LED: Red, Speech: “Almost there!” 

Robot communication handled through RobotBridge.cs, linking Unity events to Raspberry Pi commands. 

 

6. Technical  

Component 

Description 

Engine 

Unity 2022 LTS 

Hardware 

Rachel Robot + Raspberry Pi controller 

Body Tracking 

MediaPipe Unity 

Voice System 

Vosk 

Output 

LED feedback, audio, screen display 

 

7. Gameplay story board 

The player stands before Rachel. 
“Play Cornhole,” they say. Rachel lights up and starts the round. 
The player tosses a beanbag; it lands cleanly in the hole. Rachel glows blue and cheers, “Perfect shot!” 
Another bag misses; Rachel’s lights turn red briefly, then back to neutral. 
When rounds are complete, menu summarizes points. 
The player then says, “Play Disc Golf,” and the next mini game begins seamlessly. 

 

8. Design Goals 

Social Interaction: Voice-driven robot play. 

Physical Engagement: Encourages motion, aim, coordination. 

Immediate Feedback: LEDs, audio, confetti. 

Expandability: Framework allows easy addition of future mini games. 

 

9. Future Development 

Add scoreboard and difficulty levels,  

Give Rachel access to control difficulty level. 

Improve pose detection system 

Add more outdoor theme mini games. 

 

Lead Designer / Developer: Temi Akinlade 
Supervisor: Dr. John Muñoz 
Lab: BioAdaptive Interfaces Lab, Wilfrid Laurier University 

 

 