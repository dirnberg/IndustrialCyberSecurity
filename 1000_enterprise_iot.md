# Enterprise IoT

## Digital Production

### Technical Progress

### Digital Terms

### Digial Challenges

### Business Aliggnment

### Digital Strategies

## Industrial Internet of Things

### Basics

### Industrial Control Systems

### PLC

#### Real-time Execution

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


\hspace{2cm}

---

**References**

[1] \url{https://tinyurl.com/vexb9z6n} ---
TH Mittelessen, Grundwissen SPS-Technik

[2] \url{https://tinyurl.com/y6z4wt5t} --- Siemens Learning material on S7-1200 PLCs

[3] \url{https://tinyurl.com/mvzzxvay} --- Siemens S7-1500 Manual - cycle and reaction times 

\hspace{2cm}

\begin{nabox}[colback=white]{ToDo}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
 \item Sketch Execution time
\end{itemize}
\end{nabox}

\newpage
#### Profinet

**Industrial Ethernet Standard for Real-time Communication**

Profinet is an Industrial Ethernet standard that provides real-time communication capabilities for automation applications. It is designed to meet the diverse requirements of different automation systems by offering different performance classes. Profinet enables the exchange of data between controllers and field devices, such as sensors and actuators, in a precise and time-sensitive manner. This article will explore Profinet's performance classes, network communication, special network requirements, and the ProfinetA tool.

**Network Communication and Network Packets**

Profinet uses Ethernet as the communication medium and relies on layer 2 of the OSI model for field-level real-time communication. Profinet packets are Ethernet frames with an **ethertype** value set to **0x8892**.

- Profinet **DCP** (Discovery and Configuration Protocol): Facilitates the automatic detection and configuration of Profinet devices in the network. It allows devices to be identified and assigned IP addresses in a seamless manner.
- Profinet **IO**: Enables the exchange of input and output data between controllers and field devices. It provides an isochronous communication channel for time-sensitive applications like motion control.

**Special Network  and Switch Requirements**

To ensure optimal Profinet network performance, certain network requirements and switch configurations must be met:
- Network Segmentation: Separating the network into smaller segments improves efficiency, response times, security, and network management via Managed Switches (VLAN) and Firewwall/Routers.
- Realtime Traffic Isolation: Real-time field-level traffic should be kept separate from enterprise IT traffic to avoid interference.

**PronetA**

PronetA from Siemens is a free tool that assists in configuring and testing Profinet networks. It automatically detects the network topology and displays connected Profinet devices, allowing for easy configuration, including IP address assignment and device naming. Moreover, ProfinetA's IO-Check feature enables the testing of network components for correct wiring and functionality before the entire system assembly.

**Conclusion** 

Profinet is a robust and flexible Industrial Ethernet standard that provides real-time communication for various automation applications. By understanding the different performance classes, network communication, and special requirements, engineers can design efficient and reliable Profinet networks to meet their automation needs.


\hspace{2cm}

**References**

[1] \url{https://tinyurl.com/2p8uuert} ---
Profinet Technologie

[2] \url{https://tinyurl.com/y6z4wt5t} ---
Siemens SCE Training S7-1200

[3] \url{https://tinyurl.com/5e97jwvw} ---
Intel TSN

[4] \url{https://tinyurl.com/mtj6627z} ---
PROFINET IO Conformance Classes

[5] \url{https://tinyurl.com/y6v8r5sb} ---
Neumann 2005 - Ethernet-based real-time communications with PROFINET IO

[6] \url{https://tinyurl.com/2p8tzxa5} ---
PROFINET device classes





\newpage
**Profinet Performance Classes** 


Profinet is available in four performance classes: CC-A, CC-B, CC-C, and CC-D.

\begin{greenbox}[colback=white]{CC-A}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
 \item Provides basic communication with cyclic real-time communication over IO and acyclic communication over TCP/IP.
  \item Suitable for applications like building automation and commonly used in that domain.
  \item Utilizes prioritization of Ethernet data packets using IEEE 802.1p (CoS) to ensure precise control in PROFINET systems.
  \item Can be deployed with unmanaged switches but also supports managed switches.
  \item Restricted to WLAN usage.
\end{itemize}
\end{greenbox}

\begin{greenbox}[colback=white]{CC-B}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item Extends the functionality of CC-A with network diagnostics, topology information, redundancy, and dynamic reconfiguration.  
\item Suitable for manufacturing and process automation applications.  
\item Requires managed switches provides network diagnostics through SNMP and offers QoS (Quality of Service) and LLDP (Link Layer Discovery Protocol) support. Supports bandwith limitation and 802.1q (CoS)  
\item Generic Station Description Markup Language - GSDML Support
\end{itemize}
\end{greenbox}

\begin{greenbox}[colback=white]{CC-C}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item Builds upon CC-B by adding isochronous real-time (IRT) communication for motion control applications.
\item Real-Time Data Exchange - cycle tis down to 31.25 $/mu s$
\item Requires managed switches, and its real-time communication is based on IRT (Isochronous Real Time)
\item  managed switches provides network diagnostics through SNMP and offers QoS (Quality of Service) and LLDP (Link Layer Discovery Protocol) support. Supports bandwith limitation and Supports bandwith limitation and 802.1q (CoS)
\item Generic Station Description Markup Language - GSDML Support
\item Precise synchronization using Profinet Time Communication Protocol (PTCP).
\end{itemize}
\end{greenbox}

\begin{greenbox}[colback=white]{CC-D}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item Similar to CC-C in terms of functionality but implements Time-Sensitive Networking (TSN) standards for advanced real-time applications.
\item Requires managed switches and supports bandwifths from 10 Mbit to 10 Gbit, including Wireless-Kommunikation (5G).
\end{itemize}
\end{greenbox}

\hspace{2cm}









