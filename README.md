[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/gW4p9-Fp)
# os161SchedulerAssignBaseCode

I implemented the First-Come, First-Served (FCFS) scheduler in OS/161 by modifying the existing round-robin behavior. First, I disabled preemption by commenting out the thread_timeryield() call inside the hardclock() function. This makes sure threads won’t get interrupted by the clock and will run until they either block or finish.
Then, I updated the schedule() function in thread.c to always pick the oldest thread in the run queue . Since OS/161 already adds new threads to the end of the queue by default, I didn’t need to change how threads are added—just how we pull them out.

To test that it was working, we ran programs like add, matmul, and hog, and observed that each thread ran fully before the next one started. This matched the FCFS behavior we expected.

FCFS is really simple and works fine when tasks are predictable and similar in length, but it’s not ideal for interactive programs since it doesn’t switch between tasks. For example, if a long-running thread starts first, shorter ones have to wait their turn.