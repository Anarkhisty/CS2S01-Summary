# Scheduling
## Only one cpu: 
- Un proceso se ejecuta hasta que tenga que esperar.
- En una computadora normal el cpu se pone idle, y el tiempo que   esta asi es deperdiciado.

## Multiprograming
- Casi todos los recursos de un computador son scheduleados antes
- Process execution consists of a cycle of CPU execution and io wait.
- Hay un cambio entre el cpu burst y el io burst.
- La duracion del cpu burst depende de la computadora.
- Cuando el cpu es idle el so selecciona un proceso que esta listo para ejecutar y aloca el cpu para ese proceso.
- El ready list no es necesariamente un fifo. existen varios metodos.
scheduling decision:
## Casos de cambio de proceso 
1. I/O  resquest (wait()) 
2. Cuando hay un interrupt (running to ready) 
3. Cuando hay un switch del waiting a ready state
4. Cuando termina un proceso
### Nonpreemptive 1 y 4
### Preemptive 2 y 3
- La mayoria de sistemas operativos tiene algoritmos preemtives.
- Preemtive puede resultar en race condition por los files
## Dispacher: 
- Cambia un proceso a otro
- Cambia a user mode
- Vuelve a el location del user program para resumirlo
- El dispatcher esta involucrado en todos los context switch
## Scheduling criteria:
- Cpu utilization
- Thruoughput ( number processes complited in a time) 
- Turnaorunt time ( time from start to finish of a process)
- Waiting time
- Response time(time the process start responfding) 
## Scheduling algorithms
### First come, first served. (FIFO queue)
- Si el que demora mas entra primero entonce sel avg wait time es mayor.
### Shortest-job first scheduling 
- El burst más corto es el que se ejecuta primero
(el burst trata de predecirlo de los anteriores) 
### Round robin scheduling 
- Es como el fcfs pero con switches de procesos para que el tiempo de espera no sea tan largo en algunos casos
- Estos switches son seteados con un cierto tiempo
### Priority scheduling: 
- Puede ser preemptive or nonpreemptives.
- Cuando un proceso se añade al ready queue se tiene que comparar la prioridad de este con el actual.
- Una manera de evitar el starvation es aumentarle el priority en uno a uno de baja proridad cada tiempo. y luego aplicar el round robin 
## Multilevel queue:
- One queue for priority
- Executes the one with hightest prioirty
## Multilevel feedback queue scheduling:
- Igual que la anterior, solo que si un proceso consume mucho burst time sera movido a un queue con menor prioridad
## Multiprocesor scheduling: 
- This asymmetric multiprocessing is simple because only one core accesses the system data structures, reducing the need for data sharing.
1.- All threads may be in common ready queue
2.- Each processor have its own private queue
## Multicore:
- If a process stall(wait time to access data) it may be schedule until it gets it.
- Intel i7 suports 2 physical threads per core.
- A physical core can only executes a physical thread at a time.
## Load balancing: 
- The workload it is important to keep it balanced in all the processors.
- push migration and pull migration 
## Processor affinity: 
- Es que los procesos tratan de no pasar threads entre si, por la memoria cache. Que ha sido ultimamente utilizado por el thread , el costo ha pasarlo es muy alto. 
## Heterogeneous multiprocessing: 
- All threads run the same task, they vary in clock speed and power management
- There are several advantages to this approach. By combining a number of slower cores with faster ones, a CPU scheduler can assign tasks that do not require high performance, but may need to run for longer periodos
- Normalmente utilizados en arquitecturas ARM
