# operating-systems-scheduling

CPU Process Scheduling Simulator

FCFS • SJF • Priority • Round Robin • Linux Integration


<img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge">  
<img src="https://img.shields.io/badge/OS-Linux%20Compatible-green?style=for-the-badge">  
<img src="https://img.shields.io/badge/Matplotlib-Visualization-orange?style=for-the-badge">  
<img src="https://img.shields.io/badge/Category-Operating%20Systems-yellow?style=for-the-badge">
</div>

📌 Project Overview

This project implements a fully-functional CPU Process Scheduling Simulator in Python, featuring classical scheduling algorithms and real Linux process integration.

Designed for Operating Systems coursework, the simulator computes Completion Time (CT), Turnaround Time (TAT), Waiting Time (WT) and visualizes each algorithm using Gantt Charts.

It also demonstrates OS–Python integration by fetching live processes from Linux using ps and simulating them through the scheduler.


⸻

🚀 Features

✔ Classical Scheduling Algorithms
	•	FCFS (First Come First Serve)
	•	SJF (Shortest Job First — Non-Preemptive)
	•	Priority Scheduling (Non-Preemptive)
	•	Round Robin (with Quantum)

✔ Performance Metrics
	•	Completion Time (CT)
	•	Turnaround Time (TAT = CT − AT)
	•	Waiting Time (WT = TAT − BT)

✔ Visualizations
	•	Automatic Matplotlib Gantt Charts for each algorithm

✔ Linux Process Integration
	•	Fetch real processes using ps -eo pid,pri,ni,etimes,comm
	•	Convert into scheduler format
	•	Analyze how actual OS processes behave under FCFS, SJF, RR, Priority

⸻

🧠 Algorithm Explanations

1. FCFS — First Come First Serve

Concept - Explanation
Selection Rule - Process with earliest Arrival Time (AT) gets CPU first
Preemption - ❌ No
CT Formula - CT = start_time + BT
Behaviour - Fair but suffers convoy effect
