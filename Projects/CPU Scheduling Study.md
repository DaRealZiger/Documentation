# CPU Management Study

CPUs have a certain amount of core to execute processes; therefore, the operating system must have a way to schedule processes in order to avoid process [starvation].

There are a multitude of [CPU-scheduling algorithm] that are used, each concuring different results.

For example:
-----------
1. First Come First Served (FCFS)
2. Shortest Process Next (SPN)
3. Shortest Remaining Time (SRT)
4. Round Robin (RR)
5. Highest Response Ratio Next (HRRN)
6. Multilevel Feedback Queue Scheduling (MFQ)

### Study Project
A program shall be created to simulate a CPU handling the scheduling of multiple processes. 

The program shall receive input data regarding processes to be ran by the CPU with different attributes such as `arrival time` and `service time`

The program shall simulate the each algorithm and output each stage of the CPU schedule. 

The user will get a gantt chart as a result of the simulation along with other data such as `completion time`, `turn around time` and `waiting time` 
