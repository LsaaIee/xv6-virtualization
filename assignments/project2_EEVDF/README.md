# Project 2 - EEVDF Scheduling 

## Objective
Implement Linux EEVDF (Earliest Eligible Virtual Deadline First) scheduler in xv6 to achieve fair CPU time allocation based on process priorities while meeting latency requirments 

## Implemented Components
- EEVDF scheduler replaces the pre-existed round-robin scheduler with fair scheduling based on virtual deadlines
- Newly implemented scheduler tracks normalized runtime for fair CPU allocation across different priorities
- Virtual deadline calculation computes deadline for each process based on weight and time slice
- Eligibility determination identifies processes that are owed CPU tiem and ready to run 
- Modified ps system call displays sheduling parameters
    - runtime/weight 
    - vruntime
    - vdeadline
    - eligibility
- Timer interrupt adjustment reduces interrup period from 0.1s to 0.001s for finer scheduling granularity

## Key Concepts
- The base of EEVDF scheduling policy is that the sheduler picks the earliest virtual deadline among eligible processes to ensure both fairness and low latency
- Nice value is converted to weight using a predefined array, where nice value 20 corresponds to weight 1024
    - A difference of 1 in nice value provides approximately 10% more or less CPU time
    - Lower nice values result in higher wights and more CPU time
- Virtual runtime (vruntime) is a normalized runtime that accounts for process weight, calculated as `vruntime += actual runtime * (1024/weight)`
    - Allows fair comparison across processes with different priorities
    - Processes with similar vruntime values have received proportionally fair CPU time
- Virtual deadline (vdeadline) is the earliest time by which a process should finish its current time slice, calculated as `vdeadline = vruntime + timeslice * (1024/weight)`
    - Updated when process exhausts its time slice or when nice value changes via setnice
    - Not updated while process is running
- Eligibility shows if a process is eligible if it is owned CPU time by the scheduler
    - Determined by comparing 