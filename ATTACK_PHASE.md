# Lab Setup Guide

This document explains how the Red Team vs Blue Team simulation lab was created.

The lab environment is built using virtual machines so that attacks and monitoring can be safely performed in an isolated environment.

---

## 1. Virtualization Platform

The lab uses Oracle VirtualBox to run multiple operating systems on a single machine.

Virtual machines used in this project:

• Kali Linux (Attacker Machine)  
• Metasploitable 2 (Vulnerable Target Machine)

---

## 2. Attacker Machine Setup

Operating System: Kali Linux

Kali Linux is a penetration testing distribution that contains many security tools.

Steps:

1. Download Kali Linux VirtualBox image.
2. Import the VM into VirtualBox.
3. Allocate at least:

   RAM: 2 GB  
   CPU: 2 cores

4. Start the machine and verify that the system is working.

Tools used from Kali Linux:

• Nmap  
• Metasploit Framework

---

## 3. Target Machine Setup

Operating System: Metasploitable 2

Metasploitable is an intentionally vulnerable machine designed for practicing penetration testing.

Steps:

1. Download Metasploitable VM.
2. Import it into VirtualBox.
3. Allocate:

   RAM: 1 GB

4. Start the machine and log in.

Default credentials:

username: msfadmin  
password: msfadmin

---

## 4. Network Configuration

Both virtual machines must be connected to the same network so they can communicate.

Steps:

1. Open VirtualBox settings for each VM.
2. Navigate to Network settings.
3. Set the network adapter to the same network mode.

Example:

Adapter → Bridged Adapter  
or  
Adapter → Host-only Adapter

This allows Kali Linux to communicate with the Metasploitable machine.

---

## 5. Verifying Network Connectivity

After both machines are started:

Step 1 — Find the IP address of Metasploitable

Run on Metasploitable:

```
ifconfig
```

Step 2 — Test connectivity from Kali Linux

```
ping TARGET_IP
```

If the ping is successful, the lab environment is ready for penetration testing.

---

## 6. Lab Environment Summary

Attacker Machine: Kali Linux  
Target Machine: Metasploitable 2  
Virtualization: VirtualBox  
Monitoring Tools: Snort, Wireshark

This environment allows simulation of both offensive and defensive cybersecurity operations.
