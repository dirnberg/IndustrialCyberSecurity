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

\newpage
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

#### Real-time Communication with Profinet IO

**Industrial Ethernet Standard for Real-time Communication**

Profinet IO is an Industrial Ethernet standard that provides real-time communication capabilities for automation applications. It is designed to meet the diverse requirements of different automation systems by offering different performance classes. Profinet IO enables the exchange of data between controllers and field devices, such as sensors and actuators, in a precise and time-sensitive manner. This article will explore Profinet's performance classes, network communication, special network requirements.

**Profinet Performance Classes** 


Profinet is available in four performance classes: CC-A, CC-B, CC-C, and CC-D.

\begin{greenbox}[colback=white]{CC-A}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
 \item Provides basic communication with cyclic real-time communication over IO and acyclic communication over UDP.
  \item Suitable for applications like building automation and commonly used in that domain.
  \item Utilizes prioritization of Ethernet data packets using IEEE 802.1p (CoS) to ensure precise control in PROFINET systems.
  \item Can be deployed with unmanaged switches but also supports managed switches.
  \item Restricted to WLAN usage.
  \item Non-isochronous TCP/IP, RT Real-Time Class 1
\end{itemize}
\end{greenbox}


\begin{greenbox}[colback=white]{CC-B}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item Extends the functionality of CC-A with network diagnostics, topology information, redundancy, and dynamic reconfiguration.  
\item Suitable for manufacturing and process automation applications.  
\item Requires managed switches provides network diagnostics through SNMP and offers QoS (Quality of Service) and LLDP (Link Layer Discovery Protocol) support. Supports bandwith limitation and 802.1q (CoS)  
\item Supports Media Redundancy Protocol (MRP) for network reliability.
\item Generic Station Description Markup Language - GSDML Support
\item Non-isochronous TCP/IP, RT Real-Time Class 1
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
\item Non-isochronous + isochronous TCP/IP, RT, IRT Real-Time Class 1, 2, 3
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


**Network Communication and Network Packets**

Profinet IO utilizes Ethernet for communication, and its packets are Ethernet frames with Ethertype set to 0x8892. TCP/IP is implemented for process data exchange, and different communication channels are used for various tasks.

Services on **Ethertype 0x8892** in Profinet IO

**PTCP (Profinet Time Communication Protocol)** is responsible for precise time synchronization in a Profinet network. It ensures accurate clock synchronization among devices, crucial for time-critical applications like motion control and coordinated processes.

**Real-Time Acyclic Communication** in Profinet IO allows non-cyclic data exchange between devices and the controller. It is used for parameterization, configuration, and acyclic read/write operations, enabling the transfer of non-time-critical data.

**Real-Time Cyclic Communication (Class 1, 2, 3)** providing different levels of performance and determinism. These classes are used for standard cyclic data transfer and alarms, catering to various real-time requirements in automation applications.

**DCP (Discovery and Configuration Protocol)** facilitates the automatic detection and configuration of Profinet devices within the network. It allows the I/O controller to identify switches and set device names and IP addresses automatically, streamlining the configuration process.

These services, operating on Ethertype 0x8892, form the backbone of Profinet IO's communication capabilities, ensuring precise and efficient data exchange for various automation tasks.

Services on **Ethertype 0x88e3** in Profinet IO for PN MRP

**PN MRP (Profinet Media Redundancy Protocol)** is a redundancy mechanism that enhances the reliability and fault tolerance of Profinet IO networks. It ensures seamless communication even in the event of link failures by providing network redundancy. Devices in the network use PN MRP to detect and recover from link failures quickly, minimizing downtime and improving network robustness. It plays a vital role in mission-critical applications where network uptime is essential for continuous operation and safety.

**Typical Wireshark Display Filter for Profinet IO**: 

*eth.type == 0x8892 or
eth.type == 0x8893 or
lldp or
arp or
dcerpc or
snmp or
dhcp or
pnio or
pnrt*

\hspace{2cm}


**Special Network and Switch Requirements**

To ensure efficient and reliable communication in a Profinet IO network, **network segmentation is crucial**. Separating field-level traffic from control-level or enterprise IT traffic enhances security and simplifies network management. PROFINET IO also supports managed Switches with VLANs, firewalls and routers for enhanced network performance and security.

\hspace{2cm}


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
