# EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS

## AIM: To implement First-Come-First-Serve (FCFS) Scheduling

## ALGORITHM:
Start the process Get the number of processes to be inserted Get the value for burst time of each process from the use. Having allocated the burst time(bt) for individual processes , Start with the first process from its initial position let other process to be in queue Calculate the waiting time(wt) and turnaround time(tat) as Wt(pi) = wt(pi-1) + tat(pi-1) (i.e. wt of current process = wt of previous process + tat of previous process) tat(pi) = wt(pi) + bt(pi) (i.e. tat of current process = wt of current process + bt of current process) Calculate the total and average waiting time and turnaround time Display the values Stop the process

## PROGRAM:


## OUTPUT:


## RESULT: First-Come-First-Serve Scheduling is implemented successfully.



# SHORTEST JOB FIRST PREEMPTIVE SCHEDULING
## AIM: To implement Shortest Job First (SJF) Preemptive Scheduling

## ALGORITHM:


## PROGRAM:
```
#include <stdio.h>
int main()
{
 int arrival_time[10], burst_time[10], temp[10];
 int i, smallest, count = 0, time, limit;
 double wait_time = 0, turnaround_time = 0, end;
 float average_waiting_time, average_turnaround_time;
 printf("nEnter the Total Number of Processes:t");
 scanf("%d", &limit);
 printf("nEnter Details of %d Processesn", limit);
 for(i = 0; i < limit; i++)
 {
 printf("nEnter Arrival Time:t");
 scanf("%d", &arrival_time[i]);
 printf("Enter Burst Time:t");
 scanf("%d", &burst_time[i]);
 temp[i] = burst_time[i];
 }
 burst_time[9] = 9999;
 for(time = 0; count != limit; time++)
 {
 smallest = 9;
 for(i = 0; i < limit; i++)
 {
 if(arrival_time[i] <= time && burst_time[i] < burst_time[smallest] && burst_time[i] > 0)
 {
 smallest = i;
 }
 }
 burst_time[smallest]--;
 if(burst_time[smallest] == 0)
 {
 count++;
 end = time + 1;
 wait_time = wait_time + end - arrival_time[smallest] - temp[smallest];
 turnaround_time = turnaround_time + end - arrival_time[smallest]; }
 }
 average_waiting_time = wait_time / limit;
 average_turnaround_time = turnaround_time / limit;
 printf("nnAverage Waiting Time:t%lfn", average_waiting_time);
 printf("Average Turnaround Time:t%lfn", average_turnaround_time); return 0;
}
```

## OUTPUT:


## RESULT: Shortest Job First (SJF) preemptive scheduling is implemented successfully.

# SHORTEST JOB FIRST NON - PREEMPTIVESCHEDULING
## AIM: To implement Shortest Job First (SJF) Non-Preemptive Scheduling

ALGORITHM:


PROGRAM:


OUTPUT:


## RESULT: Shortest Job First (SJF) Non-preemptive scheduling is implemented successfully.

# ROUND ROBIN SCHEDULING

## AIM: To implement Round Robin (RR) Scheduling

ALGORITHM:


PROGRAM:


OUTPUT:


## RESULT: Round Robin (RR) Scheduling is implemented successfully.

# PRIORITY PREEMPTIVE SCHEDULING
## AIM: To implement Priority Preemptive Scheduling

ALGORITHM:


PROGRAM:


OUTPUT:


RESULT: Priority Preemptive scheduling is implemented successfully.

## PRIORITY NON - PREEMPTIVE SCHEDULING
# AIM: 
To implement Priority Non-Preemptive Scheduling

# ALGORITHM:
Start the process Get the number of processes to be inserted Get the corresponding priority of processes Sort the processes according to the priority and allocate the one with highest priority to execute first If two process have same priority then FCFS scheduling algorithm is used Calculate the total and average waiting time and turnaround time Display the values Stop the process

# PROGRAM:
```
#include<stdio.h>

int main()
{
    int bt[20],p[20],wt[20],tat[20],pr[20],i,j,n,total=0,pos,temp,avg_wt,avg_tat;
    printf("Enter Total Number of Process:");
    scanf("%d",&n);
 
    printf("\nEnter Burst Time and Priority\n");
    for(i=0;i<n;i++)
    {
        printf("\nP[%d]\n",i+1);
        printf("Burst Time:");
        scanf("%d",&bt[i]);
        printf("Priority:");
        scanf("%d",&pr[i]);
        p[i]=i+1;           
    }
 
    //sorting burst time, priority and process number in ascending order using selection sort
    for(i=0;i<n;i++)
    {
        pos=i;
        for(j=i+1;j<n;j++)
        {
            if(pr[j]<pr[pos])
                pos=j;
        }
 
        temp=pr[i];
        pr[i]=pr[pos];
        pr[pos]=temp;
 
        temp=bt[i];
        bt[i]=bt[pos];
        bt[pos]=temp;
 
        temp=p[i];
        p[i]=p[pos];
        p[pos]=temp;
    }
 
    wt[0]=0;	//waiting time for first process is zero
 
    //calculate waiting time
    for(i=1;i<n;i++)
    {
        wt[i]=0;
        for(j=0;j<i;j++)
            wt[i]+=bt[j];
 
        total+=wt[i];
    }
 
    avg_wt=total/n;      //average waiting time
    total=0;
 
    printf("\nProcess\t    Burst Time    \tWaiting Time\tTurnaround Time");
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];     //calculate turnaround time
        total+=tat[i];
        printf("\nP[%d]\t\t  %d\t\t    %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
    }
 
    avg_tat=total/n;     //average turnaround time
    printf("\n\nAverage Waiting Time=%d",avg_wt);
    printf("\nAverage Turnaround Time=%d\n",avg_tat);
 
	return 0;
}
```

# OUTPUT: 
![image](https://github.com/poojaanbu0/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390329/480cdb2b-3972-4282-976c-f8369c7fde2a)

# RESULT: 
Priority Non-preemptive scheduling is implemented successfully.
