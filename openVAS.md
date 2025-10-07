# 🔐 Metasploitable2 Vulnerability Scan – OpenVAS Report

**Date:** October 07, 2025  
**Analyst:** Malki Shaik Nikhat Naaz  
**Internship Track:** Task 2 – Network Security & Scanning  

---

## 🎯 Purpose

To conduct a full vulnerability assessment of the Metasploitable2 virtual machine using OpenVAS, identify exploitable services and misconfigurations, and propose effective remediation strategies.

---

## 🧪 Scan Overview

An in-depth scan was performed using OpenVAS, targeting all active ports and services on the Metasploitable2 VM. The scan revealed a wide range of critical and high-severity vulnerabilities, primarily caused by outdated software and insecure protocols. These findings reflect real-world risks that can arise from legacy systems left unpatched.

---

## 🚨 Critical Findings

The following vulnerabilities pose immediate threats and could lead to full system compromise:

- **vsftpd 2.3.4 – Root Access via Backdoor**  
  A known backdoor in this FTP daemon allows unauthenticated users to gain root privileges.

- **UnrealIRCd 3.2.8.1 – Remote Command Execution**  
  This IRC service contains a hidden backdoor enabling attackers to execute arbitrary commands remotely.

- **Apache Tomcat/Coyote Jserv – Buffer Overflow Risk**  
  A flaw in the Jserv protocol could be exploited to inject and run malicious code with elevated privileges.

📌 **Remediation:**  
Upgrade or replace all vulnerable services with secure, patched versions to eliminate these critical risks.

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
| vsftpd 2.3.4    | 21   | Backdoor Access             | 🔴 Critical   | Upgrade to patched version |
| UnrealIRCd      | 6667 | Remote Code Execution       | 🔴 Critical   | Apply security patch       |
| Apache Tomcat   | 8180 | Buffer Overflow             | 🔴 Critical   | Update Jserv module        |
| MySQL           | 3306 | Privilege Escalation        | 🟠 High       | Upgrade to latest version  |
| Apache HTTP     | 80   | Info Disclosure             | 🟠 High       | Patch vulnerabilities      |
| Telnet          | 23   | Plaintext Credential Leak   | 🟠 High       | Disable service            |
| Samba           | 445  | Remote Code Execution       | 🟠 High       | Patch and restrict access  |

---

## 🧠 Analyst Reflection & Recommendations

Metasploitable2 is intentionally vulnerable for educational purposes, but this scan demonstrates how similar misconfigurations in production environments could be exploited. The presence of backdoors, buffer overflows, and plaintext protocols provides multiple entry points for attackers.

### ✅ Action Plan:

- Apply patches to all outdated services  
- Remove or disable unnecessary and insecure protocols  
- Configure firewall rules to block unauthorized access  
- Monitor network traffic for anomalies and suspicious behavior  
- Use encrypted alternatives (e.g., SFTP, SSH) instead of plaintext services

---

## 🔗 Supporting Reports

- [Nmap Scan Report](./nmap_scan_report.md)  
- [Firewall Configuration](./iptables_firewall_configuration_report.md)  
- [Wireshark Traffic Analysis](./wireshark_packet_analysis_report.md)  
- [Reconnaissance Techniques](./reconnaissance.md)

---

📁 **Submission Note:**  
This report fulfills the vulnerability scanning requirement for **Task 2: Network Security & Scanning** under the ApexPlanet internship. Include this in your GitHub repository and reference it in your final demo video.
