# 🔍 Vulnerability Assessment Report – Metasploitable2

**Objective:**  
To evaluate the security posture of the Metasploitable2 virtual machine by identifying exploitable services, outdated software, and misconfigurations using a full-system vulnerability scan.

---

## 🧪 Scan Overview

A deep scan was conducted using a robust vulnerability assessment tool, targeting all active ports and services on the Metasploitable2 VM. The goal was to uncover weaknesses that could be leveraged by attackers.

The results revealed a system riddled with critical and high-risk vulnerabilities, many stemming from legacy software and insecure configurations.

---

## 🚨 Critical Vulnerabilities

Several high-impact issues were discovered that could allow full system compromise:

- **vsftpd 2.3.4 Backdoor:**  
  This FTP service contains a known backdoor that permits unauthenticated root access. Exploiting this could result in total control of the host.

- **UnrealIRCd 3.2.8.1 Remote Execution:**  
  The IRC daemon includes a hidden backdoor enabling attackers to execute arbitrary commands remotely.

- **Apache Tomcat/Coyote Jserv Buffer Overflow:**  
  A flaw in the Jserv protocol implementation could allow attackers to inject malicious code and execute it with elevated privileges.

📌 **Recommended Action:**  
Immediately upgrade all affected services to secure, patched versions to eliminate these critical risks.

---

## ⚠️ High-Risk Findings

In addition to the above, several services were flagged for serious vulnerabilities:

- **MySQL (5.0.51a):**  
  This outdated database engine is vulnerable to privilege escalation and other known exploits.

- **Apache HTTP Server (2.2.8):**  
  The web server version in use has multiple documented vulnerabilities that could expose sensitive data.

- **Telnet (Port 23):**  
  Telnet transmits data in plaintext, including credentials, making it highly susceptible to interception.

- **Samba Service:**  
  A buffer overflow vulnerability was identified that could allow remote code execution with root-level access.

📌 **Recommended Action:**  
Update all legacy services to current versions and disable insecure protocols like Telnet to reduce exposure.

---

## 🧠 Summary & Recommendations

The Metasploitable2 VM presents a highly vulnerable environment, with multiple outdated services and exploitable flaws. These issues offer attackers numerous vectors for intrusion and privilege escalation.

### ✅ Key Recommendations:

- Patch all legacy software immediately  
- Remove or disable unnecessary and insecure services  
- Deploy a firewall to restrict unauthorized access and mitigate future threats

---

This report supports the internship’s Task 2 objectives under **Network Security & Scanning**, and complements your Nmap and firewall configuration findings. Be sure to include this in your GitHub repo alongside your scan reports and demo video.
