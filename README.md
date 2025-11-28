https://github.com/praptiishah/os-project.git# operating-systems-scheduling


# 🖥️ CPU Process Scheduling Simulator

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Platform-Linux-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Visualization-Matplotlib-green?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Category-Operating%20Systems-yellow?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Scheduling-FCFS%20%7C%20SJF%20%7C%20Priority%20%7C%20RR-red?style=for-the-badge" />
</p>

----------------------------------------------------------------------------------------------------

## ⭐ Project Overview
This project implements a CPU Process Scheduling Simulator in Python, including classical scheduling algorithms, turnaround/waiting time computation, Gantt chart visualization, and **real Linux process integration** using `ps`.

The simulator demonstrates how different scheduling algorithms behave on both **custom datasets** and **live Linux processes**.

----------------------------------------------------------------------------------------------------

## ⭐ Algorithm Explanations

### 🔷 1. FCFS — First Come First Serve

| Concept        | Explanation                                   |
|----------------|-----------------------------------------------|
| Selection Rule | Process with earliest Arrival Time (AT) first |
| Preemption     | No                                            |
| CT Formula     | CT = start_time + BT                          |
| Behaviour      | Fair but suffers convoy effect                |

**How It Works:**
- Sort processes by Arrival Time  
- If CPU is idle, jump to next arrival  
- Execute each fully in order  

---

### 🔷 2. SJF — Shortest Job First (Non-Preemptive)

| Concept        | Explanation                                          |
|----------------|------------------------------------------------------|
| Selection Rule | Among arrived processes, choose shortest BT          |
| Preemption     | No                                                   |
| Advantage      | Produces lowest average WT and TAT                  |
| Caveat         | Long processes may starve                            |
| Behaviour      | Efficient but starvation-prone                       |

**How It Works:**
- At each step, collect all processes with AT ≤ current time  
- Select the one with minimum BT  
- If nothing has arrived, fast-forward time  

---

### 🔷 3. Priority Scheduling (Non-Preemptive)

| Concept        | Explanation                                          |
|----------------|------------------------------------------------------|
| Priority Rule  | Lower number = Higher priority                       |
| Preemption     | No                                                   |
| Behaviour      | Favors important tasks but can cause starvation      |

**How It Works:**
- Among all arrived processes, select highest priority  
- Continue until completion  
- No preemption  

---

### 🔷 4. Round Robin Scheduling

| Concept        | Explanation                                       |
|----------------|---------------------------------------------------|
| Rule           | Assign CPU time slices using fixed quantum        |
| Preemption     | Yes                                               |
| Behaviour      | Fair CPU time-sharing                              |
| Use Case       | Common in modern multitasking OS                  |

**How It Works:**
- Maintain a ready queue  
- Each process gets CPU for max `quantum` time  
- If incomplete, send back to queue  
- Add new arrivals dynamically  

----------------------------------------------------------------------------------------------------

## ⭐ Formulas Used

### Turnaround Time (TAT)
  TAT = CT-AT

### Waiting Time (WT)
  WT = TAT-BT

These values are computed in the helper function `TAT_WT()`.

----------------------------------------------------------------------------------------------------

## ⭐ Gantt Chart Visualization

Each algorithm generates a Gantt chart demonstrating:

- Execution order  
- Start & end times  
- Distinct color for each PID

Generated via:

**Gantt_Chart(gantt_data, “Algorithm Name”)**


----------------------------------------------------------------------------------------------------

## ⭐ Linux Integration (Real OS Data)

### Commands Used

ps -eo pid,comm,pri,ni,etimes,stat,pcpu –sort=-pcpu

Extracted Fields:
- pid  
- pri (priority)  
- ni (nice value)  
- etimes (elapsed time → burst time)  
- comm (command name)

### Conversion to Scheduler Format

  {
“Pid”: str(pid),
“AT”: arrival_order,
“BT”: scaled_elapsed_time,
“Priority”: pri
}

Large BTs scaled using:

BT = max(1, BT // 50)

All scheduling algorithms are executed on this Linux-derived dataset.

----------------------------------------------------------------------------------------------------

## ⭐ Repository Structure

```text
.
├── linux_integration.py
├── scheduling.py
├── requirements.txt
└── README.md
``` 

----------------------------------------------------------------------------------------------------

## ⭐ How to Run

### Install Dependencies

pip install -r requirements.txt

### Run Core Scheduling Simulation

python scheduling.py

### Run Linux Integration Mode

python linux_integration.py

----------------------------------------------------------------------------------------------------

## ⭐ Base Test Table

| PID | AT | BT | Priority |
|-----|----|----|----------|
| P1  | 0  | 6  | 3        |
| P2  | 2  | 4  | 1        |
| P3  | 4  | 5  | 4        |
| P4  | 6  | 3  | 2        |

----------------------------------------------------------------------------------------------------

## ⭐ Presentation Checklist

- Show algorithm outputs  
- Show WT/TAT/CT calculations  
- Show Linux `ps` output  
- Show converted Linux processes  
- Display all Gantt charts  
- Compare all algorithms on same data  

----------------------------------------------------------------------------------------------------

## ⭐ License

This project is for academic use under course submission requirements.
