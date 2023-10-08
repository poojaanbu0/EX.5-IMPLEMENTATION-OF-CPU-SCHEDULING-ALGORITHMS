# EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS

## AIM: To implement First-Come-First-Serve (FCFS) Scheduling

## ALGORITHM:
Start the process Get the number of processes to be inserted Get the value for burst time of each process from the use. Having allocated the burst time(bt) for individual processes , Start with the first process from its initial position let other process to be in queue Calculate the waiting time(wt) and turnaround time(tat) as Wt(pi) = wt(pi-1) + tat(pi-1) (i.e. wt of current process = wt of previous process + tat of previous process) tat(pi) = wt(pi) + bt(pi) (i.e. tat of current process = wt of current process + bt of current process) Calculate the total and average waiting time and turnaround time Display the values Stop the process

## PROGRAM:


## OUTPUT:


## RESULT: First-Come-First-Serve Scheduling is implemented successfully.



# SHORTEST JOB FIRST PREEMPTIVE SCHEDULING
AIM: To implement Shortest Job First (SJF) Preemptive Scheduling

ALGORITHM:


PROGRAM:


OUTPUT:


RESULT: Shortest Job First (SJF) preemptive scheduling is implemented successfully.


AIM: To implement Shortest Job First (SJF) Non-Preemptive Scheduling

ALGORITHM:


PROGRAM:


OUTPUT:


RESULT: Shortest Job First (SJF) Non-preemptive scheduling is implemented successfully.

AIM: To implement Round Robin (RR) Scheduling

ALGORITHM:


PROGRAM:


OUTPUT:


RESULT: Round Robin (RR) Scheduling is implemented successfully.


AIM: To implement Priority Preemptive Scheduling

ALGORITHM:


PROGRAM:


OUTPUT:


RESULT: Priority Preemptive scheduling is implemented successfully.


AIM: To implement Priority Non-Preemptive Scheduling

ALGORITHM:


PROGRAM:


OUTPUT:


RESULT: Priority Non-preemptive scheduling is implemented successfully.

