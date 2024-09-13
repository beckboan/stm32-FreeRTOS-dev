# RTOS Introduction

## Real time deals with guarantees, not with raw speed

- Having more processors doesn't mean real time
- Guarantees, not promises

## Response time is _guaranteed_

- A NRTA application may have largely varying response time
- You can't trust NRTA if response time is critical

## What are RTAs

1. Not fast applications
2. They are time deterministic
3. Small deviation in terms of ms or seconds push into soft real time (SRTA)
4. Must fall within a provided time limit
   - ex: airbag in vehicle

## What is a RTOS?

It's an OS designed to run applications with precise timing and reliability

To be considered "real-time", an OS must have a known max time for operations ex:

1. Handling of interrupts and internal exceptions
2. Handling of critical sections
3. Scheduling mechanisms

### Popular RTOS

- VxWorks
- QNZ
- FreeRTOS
- Integrity

## Task Scheduling (RTOS vs GPOS)

### GPOS

- Programmed for high throughput
- Some times execution of high priority will be delayed to serve multiple low priority
- Scheduler typically uses a fairness policy
- No guarantee that time critical processes will be prioritized

### RTOS

- Threads execute in order of priority
- High priority thread can only be paused by higher priority
- RTOS may yield less throughput that GPOS, but it does not mean that the throughput is poor

### Latency

Task scheduling latency is the triggering of an event and the time at which it is allowed to run on the CPU

**RTOS** - The latency remains relatively constant

**GPOS** - Latency increases with the number of tasks

#### Interrupt Latency

- Critical for RTOS interrupt and scheduling latency to be time bounded and small

## Priority Inversion

- LP and HP tasks switch positions
- RTOS uses re-scheduling to fix this
- Priority inversion is less significant for GPOS

## Multi-Tasking

- Running multiple tasks on a processor is accomplished by a "scheduler"
- Another method is to use a multi-core processor (each core can execute a task)
