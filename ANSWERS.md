# Assignment Questions

## Instructions
Answer all 4 questions with detailed explanations. Each answer should be **3-5 sentences minimum** and demonstrate your understanding of the concepts.

---

## Question 1: Thread vs Process

**Question**: Explain the difference between a **thread** and a **process**. Why did we use threads in this assignment instead of creating separate processes?

**Your Answer:*A thread is a smaller unit of execution within a process, whereas a process is an independent program in operation with its own memory space and system resources. While numerous threads share memory and resources, each process functions independently, making communication more difficult and resource-intensive. Because they require less overhead for creation and context switching than processes, threads are regarded as lightweight. Because the scheduler simulation must effectively manage several jobs, threads were utilized in this assignment rather than processes. Using threads enhances the simulation's overall performance and responsiveness by enabling shared access to data structures like the ready queue and process map without the need for complicated communication protocols.*

[Write your answer here. Consider: What is a process? What is a thread? How do they differ in terms of memory, resources, creation overhead? Why are threads more suitable for this simulation?]

---

## Question 2: Ready Queue Behavior

**Question**: In Round-Robin scheduling, what happens when a process doesn't finish within its time quantum? Explain using an example from your program output.

**Your Answer:**

A process in Round-Robin scheduling is halted and returned to the end of the ready queue if it does not complete within its time quantum. This ensures that all programs are treated fairly by allowing other processes to receive CPU time. After waiting for its next turn, the procedure will resume where it left off. This cycle
P2 executing quantum [4000ms]
 Quantum progress: 100%
 P2 completed quantum 4000ms │ Overall progress:  48%
Remaining time: 4254ms
 P2 yields CPU for context switch

 P2 added to ready queue │ Burst time: 8254ms | Priority: 1
 In this instance, process P2 was allotted a time quantum of 4000 ms, yet it took 4254 ms to complete its execution. Consequently, the scheduler executed a context switch and halted P2. The report indicates that P2 was then re-added to the end of the ready queue. This illustrates how Round-Robin scheduling guarantees that every process has an equal chance to run and that no process monopolizes the CPU.


## Question 3: Thread States

**Question**: A thread can be in different states: **New**, **Runnable**, **Running**, **Waiting**, **Terminated**. Walk through these states for one process (P1) from your simulation.

**Your Answer:**
New:
Process P1 is in the New state when the thread is first created using new Thread(process) inside the addProcessToQueue method. At this stage, the thread exists but has not started execution yet.
Runnable:
P1 enters the Runnable state after it is added to the ready queue and the scheduler is ready to execute it. This happens before calling start(), where the thread is waiting for CPU allocation.
Running:
P1 moves to the Running state when the scheduler selects it and executes currentThread.start(). This is shown in the output:
▶1 executing quantum [3807ms]

During this time, P1 is actively using the CPU.
Waiting:
A thread enters the Waiting state when it is temporarily paused. In this program, this occurs during Thread.sleep() inside the run() method, where the process simulates execution time. Also, the main thread waits using join() until the current process finishes its quantum.
Terminated:
P1 enters the Terminated state after completing its execution. This is shown clearly in the output:
✓P1 finished execution!

At this point, the thread has finished running and will not be scheduled again.

## Question 4: Real-World Applications

**Question**: Give **TWO** real-world examples where Round-Robin scheduling with threads would be useful. Explain why this scheduling algorithm works well for those scenarios.

**Your Answer:**

### Example 1: [Operating Systems Time-Sharing]

**Description**: 
Shared CPU time enables numerous users and apps to operate concurrently on modern operating systems.
**Why Round-Robin works well here**: 
By allocating a predetermined time slice to each activity, Round-Robin assures fairness. It gives interactive programs good responsiveness and keeps any activity from taking up all of the CPU.
### Example 2: [Web Server Request Handling]

**Description**: 
Web servers employ threads to manage several user requests concurrently.
**Why Round-Robin works well here**: 
Round-Robin allows each request to be processed fairly and prevents delays. It improves responsiveness and ensures that all requests are handled without starvation.
---

## Summary

**Key concepts I understood through these questions:**
The distinction between processes and threads
Fairness and round-robin scheduling behavior
States of execution and thread lifespan
**Concepts I need to study more:**
Sophisticated algorithms for scheduling
Performance indicators (waiting and turnaround times)
