# Penetration Testing Report: SickOS 1.2

## Introduction
This document provides a penetration testing report for **SickOS 1.2**, a vulnerable virtual machine designed for ethical hacking and cybersecurity practice. The assessment follows a structured methodology based on the **five phases of penetration testing**:

1. Reconnaissance
2. Scanning & Enumeration
3. Gaining Access
4. Maintaining Access
5. Covering Tracks (Post Exploitation)

---

## 1. Reconnaissance
### Objective:
Gather information about the target system to identify possible attack vectors.

### Methodology:
- Passive Reconnaissance: Checking public information about SickOS 1.2.
- Active Reconnaissance: Identifying live hosts using **ping sweep** and **ARP scans**.
- Tools Used: `whois`, `nslookup`, `dig`, `theHarvester`

---

## 2. Scanning & Enumeration
### Objective:
Identify open ports, services, and vulnerabilities in the target system.

### Methodology:
- Port Scanning: Used `nmap` to detect open ports.
- Service Enumeration: Identified services running on open ports.
- Vulnerability Scanning: Checked for known vulnerabilities using `nikto` and `OpenVAS`.

### Findings:
- Open Ports: 22 (SSH), 80 (HTTP)
- Web Server Detected: Apache 2.x
- Possible Exploits: Old CMS or web-based vulnerabilities

---

## 3. Gaining Access
### Objective:
Exploit vulnerabilities to gain initial access to the target system.

### Methodology:
- **Web Exploitation**: Checked for SQL Injection, LFI, and RCE.
- **Brute Force Attack**: Attempted SSH login using `hydra`.
- **Exploit Execution**: Used Metasploit to exploit a detected vulnerability.

### Findings:
- Exploited a vulnerable PHP script for **Remote Code Execution (RCE)**.
- Gained initial shell access as a **low-privilege user**.

---

## 4. Maintaining Access
### Objective:
Ensure continued access to the system for further exploitation.

### Methodology:
- **Created a backdoor** using a Netcat reverse shell.
- **Privilege Escalation**: Enumerated SUID binaries and sudo permissions.
- **Kernel Exploits**: Attempted privilege escalation with `Dirty Cow`.

### Findings:
- Used a misconfigured `sudo` command to gain **root access**.
- Established persistence by adding a new user to `/etc/passwd`.

---

## 5. Covering Tracks (Post Exploitation)
### Objective:
Remove evidence of the attack to avoid detection.

### Methodology:
- **Cleared logs** from `/var/log/`.
- **Removed history** from `.bash_history`.
- **Disabled monitoring services** to prevent detection.

### Findings:
- Successfully covered tracks and maintained root access without detection.

---

## Conclusion
The **SickOS 1.2** machine was successfully compromised using a structured penetration testing methodology. The key takeaways include:
- Weak web security led to **Remote Code Execution**.
- Poor privilege management allowed **root escalation**.
- Lack of monitoring enabled persistence and covering tracks.

This assessment highlights the importance of secure configurations and regular system updates to prevent exploitation.

---

## Disclaimer
This penetration test was conducted in a controlled environment for ethical hacking and educational purposes only. Unauthorized testing on live systems is illegal and punishable by law.

---

## References
- `Nmap`, `Metasploit`, `Burp Suite`, `Hydra`, `Nikto`
- [SickOS 1.2 on VulnHub](https://www.vulnhub.com/entry/sickos-12,144/)

