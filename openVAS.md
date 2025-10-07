# 🔐 Metasploitable2 Vulnerability Scan – OpenVAS Report

**Date:** October 07, 2025  
**Analyst:** Malki Shaik Nikhat Naaz  
**Internship Track:** Task 2 – Network Security & Scanning  
**Purpose:**  
To conduct a full vulnerability assessment of the Metasploitable2 VM, identify exploitable services and misconfigurations, and propose remediation strategies.

---

## 🧪 Scan Overview

An in-depth scan was performed using OpenVAS, targeting all active ports and services on the Metasploitable2 virtual machine. The scan revealed a range of critical and high-severity vulnerabilities, mostly due to outdated software and insecure protocols.

---

## 🚨 Critical Findings

These vulnerabilities pose immediate threats and could lead to full system compromise:

- **vsftpd 2.3.4 – Root Access via Backdoor**  
  This FTP daemon contains a known backdoor that allows unauthenticated users to gain root privileges.

- **UnrealIRCd 3.2.8.1 – Remote Command Execution**  
  A hidden backdoor in this IRC service enables attackers to execute arbitrary commands remotely.

- **Apache Tomcat/Coyote Jserv – Buffer Overflow Risk**  
  A flaw in the Jserv protocol could be exploited to inject and run malicious code.

📌 **Remediation:**  
Upgrade all vulnerable services to patched versions to eliminate these critical risks.

---

## ⚠️ High-Risk Vulnerabilities

Additional services were flagged for serious security flaws:

- **MySQL 5.0.51a**  
  This legacy database version is vulnerable to privilege escalation and other known exploits.

- **Apache HTTP Server 2.2.8**  
  The web server has multiple documented flaws that could expose sensitive data.

- **Telnet (Port 23)**  
  Telnet transmits credentials in plaintext, making it highly vulnerable to interception.

- **Samba (NetBIOS/SMB)**  
  A buffer overflow vulnerability in the Samba service could allow remote code execution with elevated privileges.

📌 **Remediation:**  
Update all legacy services and disable insecure protocols like Telnet to reduce exposure.

---

## 📊 Vulnerability Matrix

| Service         | Port | Issue Type                  | Severity   | Recommended Action         |
|----------------|------|-----------------------------|------------|-----------------------------|
| vsftpd 2.3.4    | 21   | Backdoor Access             | Critical   | Upgrade to patched version |
| UnrealIRCd      | 6667 | Remote Code Execution       | Critical   | Apply security patch       |
| Apache Tomcat   | 8180 | Buffer Overflow             | Critical   | Update Jserv module        |
| MySQL           | 3306 | Privilege Escalation        | High       | Upgrade to latest version  |
| Apache HTTP     | 80   | Info Disclosure             | High       | Patch vulnerabilities      |
| Telnet          | 23   | Plaintext Credential Leak   | High       | Disable service            |
| Samba           | 445  | Remote Code Execution       | High       | Patch and restrict access  |

---

## 🧠 Analyst Reflection & Recommendations

Metasploitable2 is designed to be vulnerable, but this scan illustrates how similar configurations in real-world systems could be exploited. The presence of backdoors, buffer overflows, and plaintext protocols provides multiple entry points for attackers.

### ✅ Action Plan:

- Apply patches to all outdated services  
- Remove or disable unnecessary and insecure protocols  
- Configure firewall rules to block unauthorized access  
- Monitor network traffic for anomalies and suspicious behavior

---

## 🔗 Supporting Reports

- [Nmap Scan Report](./nmap_scan_report.md)  
- [Firewall Configuration](./iptables_firewall_configuration_report.md)  
- [Wireshark Traffic Analysis](./wireshark_packet_analysis_report.md)  
- [Reconnaissance Techniques](./reconnaissance.md)

---


