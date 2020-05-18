# Deadlocks

**Deadlock**: Situation when a <mark>waiting process will never change its state </mark>, because the requested resource is held by another process

---
## System Model
**system**: a finite <mark>set of resources</mark> that will be distributed to many processes.
Examples of system types:
- CPU cycles
- files
	- printer
	- DVD drivers
- I/O devices

> **NOTE**: The allocation of any instance of resourcre matters. It's not the same a closer printer than a further printer.

**Sources of deadlocks**: <mark>synchronization tools</mark>, such as mutex locks and semaphores (they are also considerd as system resources, but each lock is connected to another resurces, such as a data structure).

The sources are used using the following sequence:
1. Request
2. Use
3. Release

> **NOTE**: The steps of the previous sequences may be implemented as systemcalls

Example of Deadlock:
> **Example**: Context: the system contains three CD drivers | Three process request each CD driver, then each process will request another CD to release their current resource.

---
## Deadlock Characterization
### Necesssary Conditions
Conditions to arise a deadlock:
* **Mutual exclusion**: at least one resource requested by two or more processes
* **Hold and Wait**: a process holds a resource while is waiting for another
* **No preemption**: the resource can be realesed only voluntarily by the process
* **Circular wait**: if there processes are: P0, P1 and P2; P0 waits for P1, P1 waits for P2 and P2 waits for P0.

> **NOTE**:  the circular-wait condition implies the hold-and-wait condition

---
## Methods for Handling Deadlocks
Three possible ways to deal with Deadlocks:
* **Establish a protocol**: to prevent or avoid deadlocks
* **Recover from deadlock**: The system must detect the deadlock and then recover.
* **Ignore the deadlock**: pretend that deadlocks never occur in the system

> **CURIOUS FACT**: OSs such as Linux or Windows ignore deadlocks made by user programs.
Some times the system should be restarted manually.

Many of the approaches below are combined to build a better Deadlock Handler in OSs.

---
## Deadlock Prevention
This method ensure that at least of the conditions to arise a deadlock cannot hold.

### Mutual Exclusion
Avoid mutual exclusion trying to use sharable resources, such as *read-only* files.

### Hold and Wait
Two possible protocols:
1. Allocate resources before the process begins
2. Request only resources that the process needs

> **Example**: a process that reads data from a DVD a save it in a filesys, then sort the filesys and send the data to the printer.
**1.** Allocate the DVD, the filesys and the printer at the beginning of the process. **2.** The process allocates the DVD and filesys, then releases both; after that, allocate the filesys and the printer and finally, the process release the filesys and printer.

Disadvatanges:
1. This method hold resources that are not being used.
2. Starvation is possible (because of popular resources)

### No Preemption


### Circular Wait

---
## Deadlock Avoidance
The system may provide:
- An algorithm that examines the state of the system to determine whether a deadlock has ocurred
- An alogorithm to recover from deadlock

### Single Instance of Each Resource Type

### Several Instances of a Resuource Type
---
## Deadlock Detection

---
## Recovery from Deadlock



