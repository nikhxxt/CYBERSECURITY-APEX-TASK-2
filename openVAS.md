# 🛡️ Vulnerability Assessment – Metasploitable2 VM

**Date:** September 19, 2025  
**Analyst:** Pratham Khairmode  
**Internship Task:** Network Security & Scanning – Task 2  
**Objective:**  
To perform a comprehensive vulnerability scan on the Metasploitable2 virtual machine, identify exploitable services and misconfigurations, and recommend mitigation strategies.

---

## 🧪 Scan Summary

A full-system vulnerability scan was conducted using an industry-standard assessment tool. The scan targeted all open ports and services running on the Metasploitable2 VM. The results revealed a wide range of critical and high-severity issues, primarily due to outdated software and insecure configurations.

---

## 🚨 Major Exploitable Risks

The following vulnerabilities pose immediate threats and could allow attackers to gain full control of the system:

- **vsftpd 2.3.4 – Backdoor Access**  
  This FTP service contains a known backdoor that allows unauthenticated users to gain root access.

- **UnrealIRCd 3.2.8.1 – Remote Code Execution**  
  A hidden backdoor in this IRC daemon enables attackers to execute arbitrary commands remotely.

- **Apache Tomcat/Coyote Jserv – Buffer Overflow**  
  A flaw in the Jserv protocol implementation could be exploited to inject and execute malicious code.

📌 **Mitigation:**  
Upgrade all affected services to secure, patched versions immediately to eliminate these critical risks.

---

## ⚠️ Additional Severe Issues

Several other services were flagged for high-severity vulnerabilities:

- **MySQL 5.0.51a**  
  This legacy database version is susceptible to privilege escalation and other known exploits.

- **Apache HTTP Server 2.2.8**  
  The web server has multiple documented vulnerabilities that could lead to information leakage.

- **Telnet (Port 23)**  
  Telnet transmits credentials in plaintext, making it highly vulnerable to interception.

- **Samba (NetBIOS/SMB)**  
  A buffer overflow vulnerability in the Samba service could allow remote code execution with elevated privileges.

📌 **Mitigation:**  
Update all legacy services to their latest secure versions and disable insecure protocols like Telnet.

---

## 📊 Vulnerability Matrix

| Service         | Port | Vulnerability Type         | Severity   | Recommended Action         |
|----------------|------|-----------------------------|------------|----------------------------|
| vsftpd 2.3.4    | 21   | Backdoor Access             | Critical   | Upgrade to patched version |
| UnrealIRCd      | 6667 | Remote Code Execution       | Critical   | Apply security patch       |
| Apache Tomcat   | 8180 | Buffer Overflow             | Critical   | Update Jserv module        |
| MySQL           | 3306 | Privilege Escalation        | High       | Upgrade to latest version  |
| Apache HTTP     | 80   | Info Disclosure             | High       | Patch vulnerabilities      |
| Telnet          | 23   | Plaintext Credential Leak   | High       | Disable service            |
| Samba           | 445  | Remote Code Execution       | High       | Patch and restrict access  |

---

## 🧠 Final Analysis & Recommendations

The Metasploitable2 VM is intentionally vulnerable, but this scan highlights real-world risks that exist in outdated systems. The presence of backdoors, buffer overflows, and plaintext protocols provides multiple attack vectors.

### ✅ Action Plan:

- Patch all outdated software immediately  
- Disable unnecessary and insecure services  
- Implement firewall rules to restrict access  
- Monitor network traffic for suspicious activity

---

## 🔗 Related Reports

- [Nmap Scan Report](./nmap_scan_report.md)  
- [Firewall Configuration](./iptables_firewall_configuration_report.md)  
- [Wireshark Traffic Analysis](./wireshark_packet_analysis_report.md)  
- [Reconnaissance Techniques](./reconnaissance.md)

---

📌 This report fulfills the vulnerability scanning component of **Task 2: Network Security & Scanning** under the ApexPlanet internship. Be sure to include this in your GitHub repo and reference it in your demo video.
