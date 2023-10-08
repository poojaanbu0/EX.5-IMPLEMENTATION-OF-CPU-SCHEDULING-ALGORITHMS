# EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS

# FIRST-COME-FIRST-SERVE (FCFS) SCHEDULING
## AIM: 
To implement First-Come-First-Serve (FCFS) Scheduling

## ALGORITHM:
Start the process Get the number of processes to be inserted Get the value for burst time of each process from the use. Having allocated the burst time(bt) for individual processes , Start with the first process from its initial position let other process to be in queue Calculate the waiting time(wt) and turnaround time(tat) as Wt(pi) = wt(pi-1) + tat(pi-1) (i.e. wt of current process = wt of previous process + tat of previous process) tat(pi) = wt(pi) + bt(pi) (i.e. tat of current process = wt of current process + bt of current process) Calculate the total and average waiting time and turnaround time Display the values Stop the process

## PROGRAM:
```
#include<stdio.h>
int main()
{
	int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float
	avg_wt,avg_tat;
	printf("Enter number of process:");
	scanf("%d",&n);
	printf("\nEnter Burst Time:\n");
	for(i=0;i<n;i++)
	{
		printf("p % d:",i+1);
		scanf("%d",&bt[i]);
		p[i]=i+1; //contains process number
	}
	wt[0]=0; //waiting time for first process will be zero
	//calculate waiting time
	for(i=1;i<n;i++)
	{
		wt[i]=0;
		for(j=0;j<i;j++)
		wt[i]+=bt[j];
		total+=wt[i];
	}
	avg_wt=(float)total/n; //average waiting time
	total=0;
	printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
	for(i=0;i<n;i++)
	{
		tat[i]=bt[i]+wt[i]; //calculate turnaround time
		total+=tat[i];
		printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
	}
	avg_tat=(float)total/n; //average turnaround time
	printf("\n\nAverage Waiting Time=%f",avg_wt);
	printf("\nAverage Turnaround Time=%f\n",avg_tat);
}
```

## OUTPUT:
![image](https://github.com/poojaanbu0/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390329/47858d25-b4ee-4e59-a6bb-9009514190ee)

## RESULT: 
First-Come-First-Serve Scheduling is implemented successfully.

# SHORTEST JOB FIRST PREEMPTIVE SCHEDULING
## AIM:
To implement Shortest Job First (SJF) Preemptive Scheduling

## ALGORITHM:
Start the process Get the number of processes to be inserted Sort the processes according to the burst tiine and allocate the one with shortest burst to execute first If two process have same burst length then FCFS scheduling algorithm is used Calculate the total and average waiting time and turn around time Display the values Stop the process

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
                  turnaround_time = turnaround_time + end - arrival_time[smallest];
            }
      }
      average_waiting_time = wait_time / limit; 
      average_turnaround_time = turnaround_time / limit;
      printf("nnAverage Waiting Time:t%lfn", average_waiting_time);
      printf("Average Turnaround Time:t%lfn", average_turnaround_time);
      return 0;
}
```

## OUTPUT:
![image](https://github.com/poojaanbu0/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390329/77ae5d3a-676e-49d4-8a91-3f8c26a4181d)

## RESULT: 
Shortest Job First (SJF) preemptive scheduling is implemented successfully.

# SHORTEST JOB FIRST NON - PREEMPTIVE SCHEDULING
## AIM:
To implement Shortest Job First (SJF) Non-Preemptive Scheduling

## ALGORITHM:
Start the process Get the number of processes to be inserted Get the corresponding priority of processes Sort the processes according to the priority and allocate the one with highest priority to execute first If two process have same priority then FCFS scheduling algorithm is used Calculate the total and average waiting time and turnaround time Display the values Stop the process

## PROGRAM:
```
#include<stdio.h>
 int main()
{
    int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp;
    float avg_wt,avg_tat;
    printf("Enter number of process:");
    scanf("%d",&n);
  
    printf("\nEnter Burst Time:");
    for(i=0;i<n;i++)
    {
        printf("\np%d:",i+1);
        scanf("%d",&bt[i]);
        p[i]=i+1;         
    }
  
   //sorting of burst times
    for(i=0;i<n;i++)
    {
        pos=i;
        for(j=i+1;j<n;j++)
        {
            if(bt[j]<bt[pos])
                pos=j;
        }
  
        temp=bt[i];
        bt[i]=bt[pos];
        bt[pos]=temp;
  
        temp=p[i];
        p[i]=p[pos];
        p[pos]=temp;
    }
   
    wt[0]=0;            
  
   
    for(i=1;i<n;i++)
    {
        wt[i]=0;
        for(j=0;j<i;j++)
            wt[i]+=bt[j];
  
        total+=wt[i];
    }
  
    avg_wt=(float)total/n;      
    total=0;
  
    printf("\nProcess    Burst Time    Waiting Time   Turn around Time"); 
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];   
        total+=tat[i];
        printf("\n%d   %d   %d   %d",p[i],bt[i],wt[i],tat[i]);
    }
  
    avg_tat=(float)total/n;    
    printf("\nAverage Waiting Time=%f",avg_wt);
    printf("\nAverage Turnaround Time=%f",avg_tat);
}
```

## OUTPUT:
![image](https://github.com/poojaanbu0/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390329/8f5f3f1f-ce9b-4c7c-95b8-3b4c9e68fe13)

## RESULT:
Shortest Job First (SJF) Non-preemptive scheduling is implemented successfully.

# ROUND ROBIN SCHEDULING

## AIM: 
To implement Round Robin (RR) Scheduling

## ALGORITHM:
Start the process Get the number of elements to be inserted Get the value for burst time for individual processes Get the value for time quantum Make the CPU scheduler go around the ready queue allocating CPU to each process for the time interval specified Make the CPU scheduler pick the first process and set time to interrupt after quantum. And after it's expiry dispatch the process If the process has burst time less than the time quantum then the process is released by the CPU If the process has burst time greater than time quantum then it is interrupted by the OS and the process is put to the tail of ready queue and the schedule selects next process from head of the queue Calculate the total and average waiting time and turnaround time Display the results

## PROGRAM:
```
#include<stdio.h>
int main()
{
    int st[10],bt[10],wt[10],tat[10],n,tq; 
    int i,count=0,swt=0,stat=0,temp,sq=0;
    float awt,atat;
    printf("Enter the number of processes :");
    scanf("%d",&n);
    printf("\nEnter the burst time of each process: ");
    for(i=0;i<n;i++)
    {
        printf("\np%d",i+1);
        scanf("%d",&bt[i]);
        st[i]=bt[i];
        
    }
    printf("\nenter the time quantum");
    scanf("%d",&tq);
    while(1)
    {
        for(i=0,count=0;i<n;i++)
        {
            temp=tq;
            if(st[i]==0)
            {
                count++;
                continue;
                
            }
            if(st[i]>tq)
            st[i]=st[i]-tq;
            else
            if(st[i]>=0)
            {
                temp=st[i];
                st[i]=0;
                
            }
            sq=sq+temp;
            tat[i]=sq;
            
        }
        if(n==count)
        break;
        
    }
    for(i=0;i<n;i++)
    {
        wt[i]=tat[i]-bt[i];
        swt=swt+wt[i];
        stat=stat+tat[i];
        
    }
    awt=(float)swt/n;
    atat=(float)stat/n;
    printf("\nprocess no\t burst time\t waiting time\t turnaround time\n");
    for(i=0;i<n;i++)
    printf("\n%d\t\t %d\t\t %d\t\t %d\n",i+1,bt[i],wt[i],tat[i]); 
    printf("\nAverage waiting time=%f\nAverage turn around time=%f",awt,atat);
}
```

## OUTPUT:
![image](https://github.com/poojaanbu0/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390329/9e2be743-7b04-4526-8a13-1cd8dcfc0d48)

## RESULT:
Round Robin (RR) Scheduling is implemented successfully.

# PRIORITY PREEMPTIVE SCHEDULING
## AIM:
To implement Priority Preemptive Scheduling

## ALGORITHM:
Start the process Get the number of processes to be inserted Get the corresponding priority of processes Sort the processes according to the priority and allocate the one with highest priority to execute first If two process have same priority then FCFS scheduling algorithm is used Calculate the total and average waiting time and turnaround time Display the values Stop the process

## PROGRAM:
```
#include<stdio.h>
struct process
{
    int WT,AT,BT,TAT,PT;
};

struct process a[10];

int main()
{
    int n,temp[10],t,count=0,short_p;
    float total_WT=0,total_TAT=0,Avg_WT,Avg_TAT;
    printf("Enter the number of the process\n");
    scanf("%d",&n);
    printf("Enter the arrival time , burst time and priority of the process\n");
    printf("AT BT PT\n");
    for(int i=0;i<n;i++)
    {
        scanf("%d%d%d",&a[i].AT,&a[i].BT,&a[i].PT);
        
        // copying the burst time in
        // a temp array fot futher use
        temp[i]=a[i].BT;
    }
    
    // we initialize the burst time
    // of a process with maximum 
    a[9].PT=10000;
    
    for(t=0;count!=n;t++)
    {
        short_p=9;
        for(int i=0;i<n;i++)
        {
            if(a[short_p].PT>a[i].PT && a[i].AT<=t && a[i].BT>0)
            {
                short_p=i;
            }
        }
        
        a[short_p].BT=a[short_p].BT-1;
        
        // if any process is completed
        if(a[short_p].BT==0)
        {
            // one process is completed
            // so count increases by 1
            count++;
            a[short_p].WT=t+1-a[short_p].AT-temp[short_p];
            a[short_p].TAT=t+1-a[short_p].AT;
            
            // total calculation
            total_WT=total_WT+a[short_p].WT;
            total_TAT=total_TAT+a[short_p].TAT;
            
        }
    }
    
    Avg_WT=total_WT/n;
    Avg_TAT=total_TAT/n;
    
    // printing of the answer
    printf("ID WT TAT\n");
    for(int i=0;i<n;i++)
    {
        printf("%d %d\t%d\n",i+1,a[i].WT,a[i].TAT);
    }
    
    printf("Avg waiting time of the process  is %f\n",Avg_WT);
    printf("Avg turn around time of the process is %f\n",Avg_TAT);
    
    return 0;
}
```

## OUTPUT:
![image](https://github.com/poojaanbu0/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390329/9108d2fe-5e73-466a-8b71-638b9cc2b34e)

## RESULT: 
Priority Preemptive scheduling is implemented successfully.


# PRIORITY NON - PREEMPTIVE SCHEDULING
## AIM: 
To implement Priority Non-Preemptive Scheduling

## ALGORITHM:
Start the process Get the number of processes to be inserted Get the corresponding priority of processes Sort the processes according to the priority and allocate the one with highest priority to execute first If two process have same priority then FCFS scheduling algorithm is used Calculate the total and average waiting time and turnaround time Display the values Stop the process

## PROGRAM:
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

## OUTPUT: 
![image](https://github.com/poojaanbu0/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/119390329/480cdb2b-3972-4282-976c-f8369c7fde2a)

## RESULT: 
Priority Non-preemptive scheduling is implemented successfully.
