# Enterprise IoT
%

## Digital Production
% 1.1

## Industrial Internet of Things
% 1.2

% ### 1.2.1 Basics

% %### % 1.2.3 ICS

### PLC
% 1.2.4

#### Real-time Execution
% 1.2.4.1

In today's industrial automation systems, a programmable logic controller (PLC) functions as a real-time embedded computer with extensive input/output capabilities. The PLC executes programs in a cyclical manner, following a set of tasks with specified cycle times to ensure timely and accurate control of processes. This document explores the concepts of real-time execution, cycle time, watchdog, and multitasking in industrial PLCs.

**Real-time Execution**

Real-time execution in PLCs involves the periodic operation of the controller. It follows a specific sequence of steps, including sampling sensor signals, converting them to digital form using analog-to-digital converters (A/D converters), computing control signals, converting them to analog form for actuators, and updating controller variables. The PLC operates by waiting for clock interrupts, and at each interval, it performs the designated tasks in a prescribed order to maintain control over the process.

**Cycle Time**

The cycle time of a PLC refers to the time required to complete one full execution cycle of the program. It encompasses all the steps involved in real-time execution, including reading inputs, computing control signals, sending outputs, and updating variables. The cycle time directly impacts the responsiveness and efficiency of the PLC in controlling industrial processes. It is essential to optimize the cycle time for efficient operation.

The cycle time of a PLC depends on the complexity of the control program and the hardware capabilities. A typical industrial PLC may have cycle times ranging from 1ms to 250 ms, depending on the specific application's demands. Achieving a cycle time of 250 $ \mu$s represents an extreme optimization requiring all relevant conditions to be met, including fast input/output response times and suitable hardware configurations.

**Watchdog**

The watchdog function is a critical safety feature in PLCs. It involves the monitoring of the execution of the control program. If the PLC fails to complete a cycle within a specified time (watchdog time), the watchdog function is triggered. It serves as a safety mechanism to detect and respond to potential malfunctions or program errors. The watchdog function can initiate pre-defined actions to bring the system to a safe state in case of failure.

**Multitasking**

In the context of PLCs, multitasking refers to the capability of running multiple tasks concurrently. The IEC 61131 execution engine of a PLC consists of resources where one or more tasks can run simultaneously. Each task operates with its specific program, enabling efficient handling of various control tasks without interference. Multitasking allows the PLC to manage multiple processes effectively, meeting diverse industrial requirements.

---

**References**

[1] \url{https://tinyurl.com/vexb9z6n} ---
TH Mittelessen, Grundwissen SPS-Technik

[2] \url{https://tinyurl.com/y6z4wt5t} --- Siemens Learning material on S7-1200 PLCs

[3] \url{https://tinyurl.com/mvzzxvay} --- Siemens S7-1500 Manual - cycle and reaction times 

% TODO: excecution time sketch!