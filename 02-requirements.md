# IEC 62443-3-3 RL1 Requirements

## FR 1 Identification and Authentication Control


### SR 1.1 Human User Identification and Authentication  

\paragraph{Requirement} The system shall provide the capability to identify and authenticate all human users. This capability shall enforce such identification and authentication on all interfaces which provide human user access to the system to support segregation of duties and least privilege in accordance with applicable security policies and procedures.

\paragraph{Implementation} General engineering or service access is enabled with the host based device - engineering station - in L2 control layer of the production cell. Local access for operation users is given with embedded device HMI (Human Machine Interface). Typically administrative access for operations service management users will be established via a trusted remote jump host. Remote access for engineering or service could be used via secure remote access (trusted service cells, user firewall access and VPN) and a engineering station in the enterprise client network.
 
Role-based access control (RBAC) must be integrated for all user accounts and for all user access to the singular control device (embedded, host-based and network device) and systems of the production cell.

The capabilities to administrate the user accounts of system, to assign appropriate rights to users with appropriate roles for the system, including operators, engineers and viewers can be configured.

A administrator authorization is required for the management of user accounts. Regular users cannot can not administrate user accounts on any host-based, embedded or network devices.

Centralized RBAC via Active Directory and LDAP (for host based devices with Windows OS and applications) and RADIUS Server for unique identification aud authentication of the accounts for network and embedded devices is supported. 

Embedded devices like controller or HMI and eg. runtime applications on host based devices should connected to domain specific central user managagement with access control tools like Simatic Logon or similar.

\begin{gebox}[colback=white]{Should Have:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
 \item two-factor authentication for external human users for remote access
\end{itemize}
\end{gebox}

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
 \item no aligned authentication for human user available
 \item usage of human user accounts for machine to machine communidation instead of a system user
\end{itemize}
\end{nabox}


%Je nach Anforderungen für den Betrieb bzw. Sicherheit muss das System über ein Benutzerkonzept verfügen, in dem mindestens folgende Benutzerrollen bzw. Ebenen vorgesehen sind: Administrator, User/Operator2. Für Standardfunktionen sollte bei Möglichkeit keine Benutzeranmeldung notwendig sein. Passwörter müssen jederzeit änderbar sein.

%dedicated Serviceuser
%keine Sammeluser


% Identitäts und Zugriffsmanagement
%SR 1.1 / 1.2 – Human user, software process and device identification and %authentication SR 1.6 – Wireless access management
%Requirements according to IEC 62443
   %The system requirements (SR) 1.1 and 1.2 require the ability to clearly identify and confirm all users, software processes, and devices. Core principles such as segregation of duties and limitation of access
%(Least Privilege, PoLP) should be observed accordingly. This require- ment also %applies to the management of wireless access mecha- nisms (SR 1.6).
%How Rhebo Industrial Protector supports implementation
%The foundation for planning and ensuring the requirements for »identification and %authentication« is the transparency of the net- work asset structure and the %details of the communication taking place within it. Both aspects provide relevant %conclusions about the respective status of the individual endpoint device assets %and appli- cations in the ICS.
%Rhebo Industrial Protector identifies and visualizes in real-time all network %connections and their communication parameters for a complete digital asset %inventory by network endpoint and connec- tions. The operator can filter and %evaluate the results as required by,
%for example, network segment, device type, firmware version, proto- col, data %volume etc.
%Furthermore, Rhebo Industrial Protector monitors all communica- tion in the network %and analyzes the type and content of that com- munication. All relevant protocols %such as Profinet, S7, EtherCAT, Modbus, LLDP and PTP are supported along with %hundreds of oth- ers. The passive sensors can be integrated at any number of points %into the ICS and includes both wire and wireless communication segments.



### SR 1.2 
(not applicable in SL1)

### SR 1.3 Account Management

\paragraph{Requirement} The control system shall provide the capability to support the management of all accounts by authorized users, including adding, activating, modifying, disabling and removing accounts.

\paragraph{Implementation} The capability of management of all accounts by authorized users is supported.


\begin{gebox}[colback=white]{Should Have:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
 \item capability to integrate into a higher level account management system like RADIUS, LDAP, Simatic Logon
\end{itemize}
\end{gebox}

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item no account management capability 
  \item accounts used for essential functions could be locked out, even temporarily.
\end{itemize}
\end{nabox}

%comment: not all user accounts ---> SR 1.3 RE1  -- verfügbar in SL3

### SR 1.4 Identifier Management 
%comment: SR 1.4 - Verwaltung von Kennwärtern

\paragraph{Requirement} The control system shall provide the capability to support the management of identifiers by user, group, role or control system interface.

\paragraph{Implementation} the capability of management of identifiers by user, group, role or control system interface is supported

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item Local emergency actions for the system hampered by identification requirements. 
\end{itemize}
\end{nabox}

### SR 1.5 Authenticator Management 
% SR 1.5 - Verwaltung von Authenivikatoren

\paragraph{Requirement} The control system shall provide the capability to:
a) initialize authenticator content;
b) change all default authenticators upon control system installation;
c) change/refresh all authenticators; and
d) protect all authenticators from unauthorized disclosure and modification when stored and transmitted.

\paragraph{Implementation} The required capabilities for authenticator management (to initialize, change and refresh all passwords or further credentials) are provided through the operating system and concerning applications.

%* Sämtliche im Zusammenhang mit dem Betrieb notwendigen Benutzerdaten und Passwörter sind jederzeit änderbar.

Locally managed passwords are not stored in cleartext in the system (eg. salted hashes, etc), their transmission is always encrypted and the typed password is obscured by using bullets insted of characters.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item transmission and storage of cleartext passwords
  \item no protection against unauthorized disclosure or modification of authenticators (when stored, used, transmitted)
  \item not peridoc change of authenticators possible
  \end{itemize}
\end{nabox}

% Hardware Security erst ab SL3

### SR 1.6 Wireless Access Management 
% NCR SR 1.6 - Managementvon drahtlosen Zugangsverfahren

\paragraph{Requirement} The control system shall provide the capability to identify and authenticate all users (humans,
software processes or devices) engaged in wireless communication.

\paragraph{Implementation} In order to reduce the risk, the secure production cell avoids wireless communication. 

If wireless communination in a prodcution cell is functional necessary the ability to identify and authenticate all users engage in wireless communication must be fulfilled.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item unmanaged and unsecured wireless LANs are used
\end{itemize}
\end{nabox}


### SR 1.7 Strength of Password-based Authentication

\paragraph{Requirement} For control systems utilizing password-based authentication, the control system shall provide the capability to enforce configurable password strength based on minimum length and variety of character types.

\paragraph{Implementation} All host-based systems running Microsoft Windows as operation system and applications on host-based system using LDAP or Simatic Logon have the capability to enforce domain password strength locally. 

Network or embedded system must use an external Radius or Simatic Logon Service to enforce password strength.

Configurable password strength should accord to internationally recognized and proven password guidelines, e.g. NIST SP800-63-2, BSI TR-02102 

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item enforcement of configurable password strength based on minimum length and variety of character types not possible
   \item usage of hardcoded, default, unchangeable and weak passwords
\end{itemize}
\end{nabox}

%* Eine eventuell integrierte Benutzerverwaltung muss in der Lage sein, die Vorgaben bezüglich Benutzerkonten und Passwörter zu erfüllen.
% Passwortrichtlinie

### SR 1.8 
(not applicable in SL1)

### SR 1.9 
(not applicable in SL1)

### SR 1.10 Authenticator Feedback 
% SR 1.10 - Rückmeldung von Autntifikator

\paragraph{Requirement} The control system shall provide the capability to obscure feedback of authentication information during the authentication process.

\paragraph{Implementation} The default configuration in the system is to obscure password entry-related feedback. The system does not provide any hint in case of an authentication failure.

% feedback not distinguish between wrong password or wrong username 
% no timing differences for error and no error response


\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item displaying password, wireless key, SSH token in input field instead of asterisks 
\end{itemize}
\end{nabox}

#### SR 1.11 Unsuccessful Login Attempts
% SR 1.11 - ERfolglose Anmeldeversuche

\paragraph{Requirement} The control system shall provide the capability to enforce a limit of a configurable number of
consecutive invalid access attempts by any user (human, software process or device) during a configurable time period. The control system shall provide the capability to deny access for a specified period of time or until unlocked by an administrator when this limit has been exceeded.
For system accounts on behalf of which critical services or servers are run, the control system shall provide the capability to disallow interactive logons.

\paragraph{Implementation} All Centralized RBACs amd managend Windows operating system are configured to limit the number of invalid access attempts with the Account lockout threshold policy setting. 

Network and embedded devices delay further login attemps after a number of invalid account attempts.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item no logging, warning and shield function againt unsucessful login attempts
  \item accounts used for essential functions could be locked out, even temporarily. An essential function is a function or capability that is required to maintain health, safety, the environment and availability for the equipment under control.
\end{itemize}
\end{nabox}

### SR 1.12 System Use Notification

\paragraph{Requirement} The control system shall provide the capability to display a system use notification message before authenticating. The system use notification message shall be configurable by authorized personnel.

\paragraph{Implementation} All managend Windows operating systems have the capability to enforce a use notification with the LegalNoticeCaption function. In the case of remote access to the system, human user authentication is centrally performed 
%... VNC RDP

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item system use notification can not be customized/enabled
\end{itemize}
\end{nabox}


#### SR 1.13 Access via Untrusted Networks

\paragraph{Requirement} The control system shall provide the capability to monitor and control all methods of access to the control system via untrusted networks.

\paragraph{Implementation} System access via untrusted networks (remote access, office network etc) is controlled and monitored by firewalls that support communication restrictions to the needed protocols, IP addresses and support logging and monitoring functions.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 

  \item access system from untrusted network (office network, remote access) cannot be monitored, denied, controlled or logged by an industrial firewall with strict ruleset
 
\end{itemize}
\end{nabox}


## FR 2 Use Control

### SR 2.1 Authorization Enforcement
% SR 2.1 – Durchsetzung der Autorisierung

\paragraph{Requirement} On all interfaces, the control system shall provide the capability to enforce authorizations assigned to all human users for controlling use of the control system to support segregation of duties and least privilege.

\paragraph{Implementation} Role-based access control is supported in the system for all user accounts and for all user accesses to the system. This includes capabilities to assign appropriate rights to users administering the user accounts for the system. Appropriate roles for the system, including operators, engineers, viewers can be configured.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item interfaces without authorization mechanism with system and safety relevant access (e.g. HMI, web interface, console) - not viewer access
  \item authorization mechanism is not forced by the least privilege principle
  \item authorization functions affect safety instrumented functions
\end{itemize}

\end{nabox}


### SR 2.2 Wireless Use Control
% SR 2.2 - Nutzungkontrolle von Funkverbindungen

\paragraph{Requirement} The control system shall provide the capability to authorize, monitor and enforce usage restrictions for wireless connectivity to the control system according to commonly accepted security industry practices.

\paragraph{Implementation} In order to reduce the risk, the secure production Cell avoids wireless communication. 

If wireless communination in production cell is functional necessary to ability to identify and authenticate all users engage in wireless communication must be fulfilled.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item unmanaged and unsecured wireless LANs are used for routine jobs
\end{itemize}
\end{nabox}


### SR 2.3 Use Control for Portable and Mobile Devices
% SR 43 - Nutzungskontrolle von von tragbaren und mobilen Geräten

\paragraph{Requirement} The control system shall provide the capability to automatically enforce configurable usage
restrictions that include:
a) preventing the use of portable and mobile devices;
b) requiring context specific authorization; and
c) restricting code and data transfer to/from portable and mobile devices.

\paragraph{Implementation} The system design only allows engineering access from engineering station in the production cell or secured via firewall rules from trusted and untrusted networks. The usage of any mobile devices like USB adapers should be avoided.

In additon hardening controls like disabling unused Ethernet and USB Ports and physical protection like door locks etc shoult be targeted.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item usage of removable and mobile media is not strictly reduced
  \item no locks for exposed server room, racks
\end{itemize}
\end{nabox}

### SR 2.4 Mobile Code 
% SR 2.4 - Mobiler Code

\paragraph{Requirement} The control system shall provide the capability to enforce usage restrictions for mobile code
technologies based on the potential to cause damage to the control system that include:
a. preventing the execution of mobile code;
b. requiring proper authentication and authorization for origin of the code;
c. restricting mobile code transfer to/from the control system; and
d. monitoring the use of mobile code.

\paragraph{Implementation} In general, mobile code exchange from outside the system is not needed and not allowed. System-wide hardening limits the attack surface that would allow malware to enter the system. Examples are the secure zone concept including firewalls at the zone borders, and deactivation of USB and network ports.
Deinstallation of unneeded software and secure configuration of application software reduces the risk of malware introduction through mobile code (for example in PDF files, Javascript).

For Windows-based systems malware protection (classical antivirus or application whitelisting) is in place.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item usage of removable and mobile media is not strictly reduced and need for routine jobs
  \item no locks for server room, racks
  \item Internet access of control devices is not restricted
\end{itemize}
\end{nabox}

### SR 2.5 Session Lock

\paragraph{Requirement} The control system shall provide the capability to prevent further access by initiating a session
lock after a configurable time period of inactivity or by manual initiation. The session lock shall remain in effect until the human user who owns the session or another authorized human user re-establishes access using appropriate identification and authentication procedures.

\paragraph{Implementation} Session time-out is supported by network, embedded and host-based devices.
%Automati session timeout ist avialabe for ssh https .. 


\begin{nabox}[colback=white]{Not Accepted:}

\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 

  \item no configurable session lock (manual, time period of inactivity, disable session lock)
  \item accounts used for essential functions could be locked out, even temporarily. An essential function is a function or capability that is required to maintain health, safety, the environment and availability for the equipment under control.
  \item identification and authentication affect safety instrumented functions 
  
\end{itemize}
\end{nabox}


### SR 2.6 
(not applied in SL1)
% SR 2.6 - Sitzungsperrung

### SR 2.7 
(not applied in SL1)

### SR 2.8 Auditable Events 
% SR 2.8 Prüfbare EReingusse und deren Aufzeichnung

\paragraph{Requirement} The control system shall provide the capability to generate audit records relevant to security for the following categories: access control, request errors, operating system events, control system events, backup and restore events, configuration changes, potential reconnaissance activity and audit log events. Individual audit records shall include the timestamp, source (originating device, software process or human user account), category, type, event ID and event result.

To ensure that security logs are kept for a specified number of days and to provide them for further analysis,
security logging server acts as central destination and collects the security logs via the syslog or eventlog protocol. This
server can be connected to a superordinate SIEM system without interfering with the substation component
configuration.

\paragraph{Implementation} Security-related events are logged across the whole system. All components support security logging like Syslog or Eventlog. Security-logging server act as central destination and collects the security logs.

\begin{nabox}[colback=white]{Not Accepted:}

\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
   \item relevant security-related events are not logged 
  \item security-related events are not forwardable to central logging server
  \item audit records not include the following information: timestamp, source, category, type, event ID, event result 
  \item incorrectly timestamped audit records  affect essential functions
\end{itemize}
\end{nabox}

%SR 2.8 – Auditable events
%Requirements according to IEC 62443
%The control system shall provide audit records relevant to security. events, backup and recovery, configuration changes, potential at- These shall take into account the following security categories: ac- tack activity (e.g. port scans), and audit logs.
%cess control, request errors, operating system and control system
 
%How Rhebo Industrial Protector supports implementation
Rhebo Industrial Protector reports any events in the ICS that indi- cate covert attacks, malware, espionage, exploits of vulnerabilities or Internet access, technical failures and network changes and does this in real-time.
%Each anomaly is stored with timestamp and transaction details (metadata and copy of actual communication packets). The anoma- ly notifications can be filtered according to user preferences. Opera- tors can immediately analyze the incident and plan actions.

### SR 2.9 Audit Storage Capacity
% SR 2.9 Speicherkapaziät für Aufzeichnung

\paragraph{Requirement} The control system shall allocate sufficient audit record storage capacity according to
commonly recognized recommendations for log management and system configuration. The control system shall provide auditing mechanisms to reduce the likelihood of such capacity being exceeded.

\paragraph{Implementation} All Windows-based systems support the Windows eventlog. The maximum log capacity can be configured via the Windows GPO (group policy objects). A percentage threshold can be configured for the security event log at which the system will generate a warning. 

The storage capacity on the syslog server is limited by the disc space only. The logging server has the capability to send a message to a SIEM if a threshold (disk space) is reached. The logging server has the capability to automatically delete old log entries after sending those to a SIEM. If the maximum size for the log is reaching, the runing applications are note aeffect and keep running. The control system prevents the loss of information with several measures depending on the dedicated
component.


\begin{nabox}[colback=white]{Not Accepted:}

\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 

  \item failure of audit functionality when a threshold is reached or the 
storage capacity is exceeded 
 
\end{itemize}

\end{nabox}


### SR 2.10 Response to Audit Processing Failures.
% SR 2.10 Reaktion auf ausfefalle Ereinsdatenverariebutng

\paragraph{Requirement} The control system shall provide the capability to alert personnel and prevent the loss of
essential services and functions in the event of an audit processing failure. The control system shall provide the capability to support appropriate actions in response to an audit processing failure according to commonly accepted industry practices and recommendations.

\paragraph{Implementation} Audit and logging events are not able to influe the main function fo the process. The system prevents the loss of information with several measures depending on the dedicated component. The security log information will be sent to a syslog/eventlog server in near-real-time manner. Failures between the syslog/event server and SIEM are recognized and lead to a log entry.

\begin{nabox}[colback=white]{Not Accepted:}

\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item loss of essential services or functions during an audit processing failure 
   \item no warning/status about audit processing failure 

\end{itemize}

\end{nabox}

 


### SR 2.11 Timestamps

\paragraph{Requirement} The control system shall provide timestamps for use in audit record generation.

\paragraph{Implementation} Timestamps for audit record generation will be provided by the logging devices.

\begin{nabox}[colback=white]{Not Accepted:}

\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item no ability to generate timestamps for audit records (see SR 2.8) - timestamps include date and time
  \item no correct or synced time on systems avoidable with general usage of ntp time services 
  \item incorrectly timestamped audit records affect essential functions
\end{itemize}
\end{nabox}

%SR 2.11 – Timestamps
%Requirements according to IEC 62443
%The control system shall generate and provide timestamps for the creation of audit reports.
 
%How Rhebo Industrial Protector supports implementation
%Rhebo Industrial Protector stores all anomaly notifications with in- anomaly detection with a trusted service provider, the validity of dustry standard time-synchronized timestamps. By integrating the anomaly notifications for compensation claims can be secured.


### SR 2.12 
(not applied in SL1)

## FR 3 System Integrity

### SR 3.1 Communication Integrity

\paragraph{Requirement} The control system shall provide the capability to protect the integrity of transmitted information.

\paragraph{Implementation} The secure production cell is based on secure zones and tight firewall configuration for access to secure zones. The equipment withstands the harsh environmental conditions in production area. This avoids violation of communication integrity due to electromagnetic impact.

The communication from secure production cell to another secure production cell, service cell operations application or remote access via VPN must secured with minimum Transport Layer Security Standard (--> SR 4.3) recommended protocols (e.g. BSI TR-02102), see 4.3 

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item usage of non-standardized cryptographic protocol 
  \item usage of unsecure and legacy protocols
\end{itemize}
\end{nabox}

### SR 3.2 Malicious Code Protection

\paragraph{Requirement} The control system shall provide the capability to employ protection mechanisms to prevent,
detect, report and mitigate the effects of malicious code or unauthorized software. The control system shall provide the capability to update the protection mechanisms.

\paragraph{Implementation} For Windows-based systems, antivirus (Microsoft Defender) and application whitelisting solutions (Microsoft Defender Applicaton Control)  are released to protect against malware. Updates for antivirus signatures can be deployed via WSUS or WSUS offline (Windows Server
Update Services).

\begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
    \item no controls like antivirus and application whitelisting for standard host-based systems with standard applications (eg. HMI)
    \item outdated antivirus definition on running system
    \item usage of non hardenend shares, generic domain users, outdated legacy file share protocols
    \item installation of not signed software from unsecure sources
    \item permament connection to internet (mail, browser)
\end{itemize}
\end{nabox}

### SR 3.3 Security Functionality Verification

\paragraph{Requirement} The control system shall provide the capability to support verification of the intended
operation of security functions and report when anomalies are discovered during FAT, SAT and scheduled maintenance. These security functions shall include all those necessary to support the security requirements specified in this standard.

\paragraph{Implementation} Verification of correct implementation of security functions to address the security requirements is performed according to security tests.

\begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item no possibility to test and monitor security functionality, e.g. no log message, no notification 
\end{itemize}
\end{nabox}


### SR 3.4 Software and Information Integrity
\paragraph{Requirement} The control system shall provide the capability to detect, record, report and protect against
unauthorized changes to software and information at rest.

\paragraph{Implementation} The integrity checks are based on digitally signed software and component capabilities. Microsoft and application software updates  are protected by digital signatures. Firmware updates for are digitally signed.

\begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item usage of a outdated software and operation system
\item no usage of version-control for programmable controller code
\end{itemize}
\end{nabox}

### SR 3.5 Input Validation 

\paragraph{Requirement} The control system shall validate the syntax and content of any input which is used as an
industrial process control input or input that directly impacts the action of the control system.

\paragraph{Implementation} As a standard capability regarding to safety and functional requirements, the secure production cell components perform verification of process-related input values, for example regarding allowed ranges.

\begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item out-of-range values for a defined field 
type 
\item invalid characters in data fields 
\item missing or incomplete data and buffer overflow 
\end{itemize}
\end{nabox}




### SR 3.6 Deterministic Output 

\paragraph{Requirement} The control system shall provide the capability to set outputs to a predetermined state if
normal operation cannot be maintained as a result of an attack.

\paragraph{Implementation} In case of abnormal communication, the protection in control devices will continue to provide protection and the system providing core function without communication

\begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item in case of abnormal communication, the protection in control devices will not continue to provide protection 
\end{itemize}
\end{nabox}


%SR 3.6 – Deterministic output
%Requirements according to IEC 62443
%The control system shall provide the ability to set the output to a predetermined value if normal operation cannot be maintained due to an attack.
 
%How Rhebo Industrial Protector supports implementation
%Rhebo Industrial Protector is completely passively deployed in the ICS and does not disrupt or otherwise affect operation production devices in any way. This deployment has the unique advantage
%of preventing manipulation of the monitored data as well as the Rhebo Industrial Protector control system, even if the ICS itself is attacked or disrupted.

### SR 3.7 
(not applied in SL1)

%SR 3.7 – Error handling
%Requirements according to IEC 62443
 %The control system shall detect and handle error conditions in such a way that an effective and timely troubleshooting can be carried out.
%The information must be treated as confidential as possible in order to avoid the exploitation by attackers.
%How Rhebo Industrial Protector supports implementation
%Rhebo Industrial Protector reports error states in real-time that indi- cate system %or network errors or quality degradation. These include various quality and %continuity anomalies such as:
%• protocol errors
%• missing or delayed cyclic messages
%• communication interruptions
%• degrading round-trip times
%• TCP window sizes falling
%• missing TCP handshakes
%• low TTL of packets indicating routing problems
%%• out of order packets etc.
%Recurring anomalies are displayed in the same context of previous notifications (»recurrences«) and can be easily correlated with their source anomaly data for forensic investigations.
%Each anomaly report is evaluated according to risk and takes into account both the communication and the endpoint devices involved. The basic data for the risk assessment can be configured by opera- tors according to their specific requirements and infrastructure.
%The error condition anomalies are listed separately from securi- ty-relevant anomalies on the graphical user interface. This enables fast prioritization. All anomaly notifications and their corresponding event details are stored as PCAP for immediate forensic analysis. Information can be transmitted to other systems in encrypted form.
%Rhebo Industrial Protector thus offers operators the knowledge base and the time advantage to react to error conditions before they have serious consequences.


### SR 3.8
(not applied in SL1)

### SR 3.9
(not applied in SL1)

## FR 4 Data Confidenitality

### SR 4.1 Information Confidentiality

\paragraph{Requirement} The control system shall provide the capability to protect the confidentiality of information for which explicit read authorization is supported, whether at rest or in transit.

\paragraph{Implementation}  Confidentiality of sensitive data like user authorization and certificate information is ensured in the system by applying appropriate access protection mechanisms.

System shall support communicaiton with encrypted protocols and robust check sums/hashing to the confidentiality and integrity of information at rest or in transit. --> SR 4.2

The usage of legacy or unsecure protocols like smbv1, snmpv1, ftp etc for communication secure production to operations applications must be avoided. 

Windows-based systems use the Windows build-in data protection architecture. 

This requirement can only fulfilled if also SR2.3, SR 2.4 is considered and additonal hardening controls like disabling unused Ethernet and USB Ports and physical protection like door locks etc should be applied.

\begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item usage of legacy or unsure protocols like smbv1, snmpv1, ftp etc for communication secure production  cell to operations applications 

\item sensitive data eg GDPR is stored on system in cleartext and accessable for everybody without any authorisation
\item (wireless) no use of any encryption 
\end{itemize}
\end{nabox}

### SR 4.2
(not applied in SL1)

### SR 4.3 Use of Cryptography

\paragraph{Requirement} If cryptography is required, the control system shall use cryptographic algorithms, key sizes
and mechanisms for key establishment and management according to commonly accepted security industry practices and recommendations.

\paragraph{Implementation} The production cell use standardized cryptographic mechanisms, including X.509 certificates, SSL/TLS, IPsec etc. Common best practices regarding crypto algorithms and key lengths are constantly monitored from diverse international sources (for example NIST, BSI) and adopted in the components. use of recommended protocols (e.g. BSI TR02102)

Follow protocols are accepted for usage without any compensation controls, if minimum standard for Transport Layer Security TLS 1.2 is fulfilled.

- OPC UA/TLS
- SSH
- MQTTS
- FTPS
- SMBv3
- RDP
- HTTPS 

Network and embedded devices should support secured version of
- NTP
- SYSLOGs
- RADIUS
or use compensation controls like vpn.

\begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item usage of legacy or unsure protocols like smbv1, snmpv1, ftp etc for communication secure production  cell to operations applications 

\item use of non-standardized cryptographic protocol
\item (wireless) no use of any encryption 
\item use of weak and outdated cryptographic protocol 

\end{itemize}
\end{nabox}





## FR 5 Ristricted Data Flow

### SR 5.1 Network Segmentation
%SR 5.1 – Netzaufteilung
% Grundsätzlich werden spezielle geschützte Netzwerksegmente des UEN für industrielle Automatisie-rungs- und Steuerungssysteme bereitgestellt.

\paragraph{Requirement} The control system shall provide the capability to physically segment control system networks from non-control system networks and to physically segment critical control system networks from non-critical control system networks.

\paragraph{Implementation} The production cell is shielded with an industrial firewalls with a firewall configuration follow the least priviledge/hardening principle. 

The architecture of the secure production cell separates real-time communication for automation eg. Profinet from
industrial ethernet communication. One production can consist of one inudstriual ethernet network with 0,1 or more connected real-time communication networks.

The mixture of Profinet and Industrial Ethernet must be avoided, the networks must be separated. The gateway from industrial ethernet to profinet is typically the controller. So a direct communication to a profinet device without using the controller is not possible.

\begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item production cell is not shielded with am industrial firewalls with a firewall configuration follow the least priviledge/hardening principle
\item Profinet and Industrial Ethernet networks are not separated
\end{itemize}
\end{nabox}

### SR 5.2 Zone Boundary Protection
% SR 5.2 - Schutz der Zonengrenze

\paragraph{Requirement} The control system shall provide the capability to monitor and control communications at zone boundaries to enforce the compartmentalization defined in the risk-based zones and conduits model. 

The control system shall provide the capability to deny network traffic by default and allow network traffic by exception (also termed deny all, permit by exception).
 
\paragraph{Implementation} The network segmentation is accomplished by separating the networks using industrial firewalls. The firewalls control all inbound and outbound communication with a firewall configuration follow the least priviledge/hardening principle. The default recommended firewall configuration only allows the required communication and protocols.

All blocked and relevant allow traffic will be logged for further analysis. 

 \begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item demonstrate insufficient boundary protection 
\item no defined zones or conduits
\item no firewall ruleset following deny by default, allow by exception 
\item essential functions are not maintained if zone boundary protection goes into fail-close and/or island mode 
\end{itemize}
\end{nabox}

### SR 5.3 General Purpose Person-to-Person Communication Restrictions 
\paragraph{Requirement} The control system shall provide the capability to prevent general purpose person-to-person
messages from being received from users or systems external to the control system.


% SR 5.3 - Beschränkung der Verwendung der persönlichen Kommunikation

\paragraph{Implementation} Secure zone boundaries are protected by firewalls. The default recommended firewall configuration only allows the required communication and protocols. All other communication like unnecessary protocols carrying person-to-person communication is denied.

 \begin{nabox}[colback=white]{Not Accecpted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item demonstrate insufficient boundary protection with nonexistend, insufficient traffic inspection 
\end{itemize}
\end{nabox}


### SR 5.4 Application Partitioning
% SR 5.4 - Paritionierung von Anwendungen

\paragraph{Requirement}  The control system shall provide the capability to support partitioning of data, applications and
services based on criticality to facilitate implementing a zoning model.

\paragraph{Implementation} Partitioning of different functions, applications, or data are supported. Critical automation and protection functions are located in the secure production cell. Service functionality (for example engineering) is located in a service cell instead of placing it directly in production cell.

 \begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
\item centralized applications and data
\item develope system is separated from runtime
\end{itemize}
\end{nabox}

## FR 6 Timely Response To Events

### SR 6.1 Audit Log Accessibility

\paragraph{Requirement} The control system shall provide the capability for authorized humans and/or tools to access audit logs on a read-only basis.


% [SR 6.1] Equipment shall provide the capability to generate audit records. 

\paragraph{Implementation} All components of system should provide security audit log capabilities. The audit logs can be accessed by authorized users eg. via ssh or https.



\begin{nabox}[colback=white]{Not Accepted:}
 \begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item audit logs are accessible to unauthorized users 
  \item no capability for authorized humans or no tools to access audit logs  
\end{itemize}
\end{nabox}

%Requirements according to IEC 62443
%The control system shall provide audit records relevant to security. events, backup and recovery, configuration changes, potential at- These shall take into account the following security categories: ac- tack activity (e.g. port scans), and audit logs.
%cess control, request errors, operating system and control system
 
%How Rhebo Industrial Protector supports implementation
Rhebo Industrial Protector reports any events in the ICS that indi- cate covert attacks, malware, espionage, exploits of vulnerabilities or Internet access, technical failures and network changes and does this in real-time.
%Each anomaly is stored with timestamp and transaction details (metadata and copy of actual communication packets). The anoma- ly notifications can be filtered according to user preferences. Opera- tors can immediately analyze the incident and plan actions.

### SR 6.2
(not applied in SL1)

%Requirements according to IEC 62443
%The control system shall be able to continuously monitor the perfor- mance of all security mechanisms. By means of generally accepted
%practices and recommendations of the security industry, security bre- aches shall be detected, evaluated and reported in a %timely manner.
%How Rhebo Industrial Protector supports implementation
%Rhebo Industrial Protector continuously and seamlessly monitors fied and reported as network behavior anomalies but optionally with all communication in the ICS network. Violations of other security higher risk profile score. Recurring anomalies are flagged separately. mechanisms (e.g. firewall, virus scanner, IDS, SIEMs) are also identi-

## FR 7 Resource Availability 

### SR 7.1 Denial of Service Protection
\paragraph{Requirement} The control system shall provide the capability to operate in a degraded mode during a DoS event.

\paragraph{Implementation} DoS protection is realized with the defense-in depth approach. Industrial firewalls protect the system and prevent direct communication with the
production cell from untrusted networks.

 \begin{nabox}[colback=white]{Not Accepted:}
 \begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item  production cell is not protected by an industrial firewall against denial of service (DoS)
  \item denial of service (DoS) or denial of service (DoS) protection itself affect safety instrumented functions 
\end{itemize}
\end{nabox}

%SR 7.1 – Denial of service protection
%Requirements according to IEC 62443
%The control system shall remain functional even under deteriorated duced (SR 7.1 RE 1) and the risk that ICS users (humans, software, conditions during a DoS event. Communication loads shall be re- devices) can trigger DoS events shall be limited (SR 7.1 RE 2).
%How Rhebo Industrial Protector supports implementation
Rhebo Industrial Protector detects communication that indicates a breach of security rules or could affect the optimal functionality of network components or operational continuity. This includes new communication processes and increases in network activity among
%others. Rhebo Industrial Protector itself is not affected by external events. The passive, non-intrusive integration prevents its attack and manipulation in case of a successful penetration of the ICS.

### SR 7.2 Resource Management
\paragraph{Requirement}  The control system shall provide the capability to limit the use of resources by security functions to prevent resource exhaustion.

\paragraph{Implementation} Critical automation and protection functions and management functionality (for example engineering) are located inside the secure production cell. The secure system is designed to continue independent basic operation without relying on external network services.

The industrial firewall limits the use of ressources by securtiy funtions to protect against resource exhaustion.

With the automatic cell offline mode the system operates in case of it outages and disruption.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item  no automatic cell offline mode available.
\end{itemize}
\end{nabox}


### SR 7.3 System Backup

\paragraph{Requirement} The identity and location of critical files and the ability to conduct backups of user-level and
system-level information (including system state information) shall be supported by the control system without affecting normal plant operations.

\paragraph{Implementation} The system has the capability to backup and restore critical files like configuration and real time data that are needed to restore the system. The latest firmware and configuration are backed up via the engineering tool and are available on the engineering station.

\begin{nabox}[colback=white]{Not Accepted:}

\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item  no / insufficient backup capabilities
  \item insufficient description of configuration
\end{itemize}
\end{nabox}

### SR 7.4 System Recovery and Reconstitution
\paragraph{Requirement} The control system shall provide the capability to recover and reconstitute to a known secure
state after a disruption or failure.


\paragraph{Implementation} Disaster recovery capabilities and strategies based on the backup and restore capabilities stated for SR 7.3. The capabilities include backup and recovery of software, configuration and operational data. This includes also
the secure configuration like implemented hardening, updates and patches.

 \begin{nabox}[colback=white]{Not Accepted:}
 \begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item no capability to recover and reconstitute to a known secure state after disruption or failure
  \item security-critical patches are not reinstalled or security-related configuration settings are not reestablished with recovery
  \item system documentation and operating procedures is not available 
\end{itemize}
\end{nabox}


### SR 7.5 Emergency Power

\paragraph{Requirement} The control system shall provide the capability to switch to and from an emergency power
supply without affecting the existing security state or a documented degraded mode.

\paragraph{Implementation} For the system in scope, the capability is provided as due to loss of power supply no degradation of security will occur. Loss of power supply will result in temporary unavailability from remote, not in allowing any-to-any communication.

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item loss of power occur loss of security functions
\end{itemize}
\end{nabox}


### SR 7.6 Network and Security Configuration Settings

\paragraph{Requirement} The control system shall provide the capability to be configured according to recommended
network and security configurations as described in guidelines provided by the control system supplier. The control system shall provide an interface to the currently deployed network and security configuration settings.

\paragraph{Implementation} The system can be configured according to the recommended system security and hardening guidelines. 

\begin{nabox}[colback=white]{Not Accepted:}
\begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item the system can not be configured according to the recommended system security and hardening
guidelines
\end{itemize}
\end{nabox}

### SR 7.7 Least Functionality 

\paragraph{Requirement} The control system shall provide the capability to specifically prohibit and/or restrict the use of
unnecessary functions, ports, protocols and/or services.

\paragraph{Implementation} Capability to set configuration options to a secure state (hardening) are provided by the system.

 \begin{nabox}[colback=white]{Not Accepted:}
 \begin{itemize}
 \renewcommand{\labelitemi}{$\Square$} 
  \item  no capability to restrict the use of unnecessary functions, ports, protocols, unneeded software and/or services 
  \item functions beyond a baseline configuration can not be deactivated 
\end{itemize}
\end{nabox}

%Nicht verwendete und benötigte Netzwerkdienste und -protokolle sind auf Clients, Server und auf Netzwerkomponenten zu deaktivieren.

%Jedes System, Anwendung, Komponente und jeder Benutzer erhalten bei Möglichkeit nur die Rechte, die für die Ausführung der Tätigkeit benötigt werden und der Betrieb von Anwendungen sollte im normalen Benutzerkontext erfolgen (keine erweiterten Rechte, Berechtigung usw.).

%Betrieb der Anwendung im normalen Benutzerkontext, d.h. es sind keine erweiterten Rechte oder Berechtigungen für den ordnungsgemäßen Betrieb notwendig.



%SR 7.7 Härtung
%    The control system shall restrict the use of unnecessary functions, ports, protocols and/or services.
%   Rhebo Industrial Protector supports operators in managing the ICS with a complete visualization of all endpoint device assets, ports, connections and their network behavior in terms of functions, pro- tocols and content. Any change in network behavior as well as any
%new connection and component are reported as an anomaly in real-time. This allows operators to continuously check whether un- necessary or harmful functions, ports, protocols and services exist in the ICS – and remove them.
%SR 7.7 – Least functionality
%Requirements according to IEC 62443
%The control system shall restrict the use of unnecessary functions, ports, protocols and/or services.
 
%How Rhebo Industrial Protector supports implementation
%Rhebo Industrial Protector supports operators in managing the ICS with a complete visualization of all endpoint device assets, ports, connections and their network behavior in terms of functions, pro- tocols and content. Any change in network behavior as well as any
%new connection and component are reported as an anomaly in real-time. This allows operators to continuously check whether un- necessary or harmful functions, ports, protocols and services exist in the ICS – and remove them.


### SR 7.8 
(not applied in SL1)


