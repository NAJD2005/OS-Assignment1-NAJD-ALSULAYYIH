# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:*Processes operate in isolation, making communication complex and resource-intensive. In contrast, threads are lightweight units within a process that share the same memory and resources, requiring less overhead for creation and context switching. This makes threads more efficient for simulations that require frequent switching.

In this assignment, threads were used instead of processes because the scheduler simulation needs to handle multiple tasks efficiently. Threads allow shared access to data structures such as the ready queue and process map without complex communication mechanisms. Therefore, using threads improves performance and simplifies implementation.*

[Write your answer here. Consider: What is a process? What is a thread? How do they differ in terms of memory, resources, creation overhead? Why are threads more suitable for this simulation?]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

A process in Round-Robin scheduling is halted and returned to the end of the ready queue if it does not complete within its time quantum. This ensures that all programs are treated fairly by allowing other processes to receive CPU time. After waiting for its next turn, the procedure will resume where it left off. This cycle keeps going till the procedure is finished.

**Your Answer:* P2 executing quantum [4000ms]
 Quantum progress: 100%
 P2 completed quantum 4000ms │ Overall progress: 48%
Remaining time: 4254ms
 P2 yields CPU for context switch
In this instance, process P2 was allotted a time quantum of 4000 ms, yet it took 4254 ms to complete its execution. Consequently, the scheduler executed a context switch and halted P2. The report indicates that P2 was then re-added to the end of the ready queue. This illustrates how Round-Robin scheduling guarantees that every process has an equal chance to run and that no process monopolizes the CPU.
 P2 added to ready queue │ Burst time: 8254ms | Priority: 1
*



## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**
New
Process P1 is in the New state when the thread is first created using new Thread(process) inside the addProcessToQueue method. At this stage, the thread exists but has not started execution yet.
Runnable
P1 enters the Runnable state after it is added to the ready queue and the scheduler is ready to execute it. This happens before calling start(), where the thread is waiting for CPU allocation.
Running:
P1 moves to the Running state when the scheduler selects it and executes currentThread.start(). This is shown in the output:
P1 executing quantum [3807ms]

During this time, P1 is actively using the CPU.
Waiting
A thread enters the Waiting state when it is temporarily paused. In this program, this occurs during Thread.sleep() inside the run() method, where the process simulates execution time. Also, the main thread waits using join() until the current process finishes its quantum.
Terminated:
P1 enters the Terminated state after completing its execution. This is shown clearly in the output:
 P1 finished execution!

At this point, the thread has finished running and will not be scheduled again

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: [Time-Sharing Operating Systems]

**Description**: 
[By allocating a predetermined time slice to each activity, Round-Robin assures fairness. It gives interactive programs good responsiveness and keeps any activity from taking up all of the CPU.]

**Why Round-Robin works well here**: 
[Explain why Round-Robin scheduling is suitable. Consider fairness, responsiveness, predictability, etc.]

### Example 2: [Web Server Request Handling]

**Description**: 
[Web servers employ threads to manage several user requests concurrently.]

**Why Round-Robin works well here**: 
[Round-Robin eliminates delays and enables equitable processing of every request. It guarantees that every request is processed without starvation and increases responsiveness.]

---

## Summary

**Key concepts I understood through these questions:**
The distinction between processes and threads
Fairness and round-robin scheduling behavior
States of execution and thread lifespan
**Concepts I need to study more:**
Advanced scheduling algorithms
Performance metrics (waiting time, turnaround time)
