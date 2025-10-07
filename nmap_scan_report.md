# 🧪 Task 2: Nmap Reconnaissance Report – Metasploitable2

**Internship Track:** ApexPlanet – Network Security & Scanning  
**Scan Date:** September 17, 2025  
**Analyst:** Pratham Khairmode

---

## 🎯 Target Overview

- **Victim Host:** Metasploitable2 VM  
- **Target IP:** `192.168.56.4`  
- **Scanner Host:** Kali Linux VM (`192.168.56.x`)

---

## 🔍 Scan Parameters

The following Nmap command was executed to perform a stealthy and informative scan:

```bash
nmap -sS -sV -O 192.168.56.4
```

**Flags Explained:**

- `-sS`: TCP SYN scan (stealthy and less detectable)
- `-sV`: Service version detection
- `-O`: Operating system fingerprinting

---

## 📄 Nmap Output Summary

```text
Host Status: Up (latency: 0.025s)
Closed Ports: 976 (TCP)
Scan Duration: ~33 seconds
MAC Address: 08:00:27:EF:74:9B (Oracle VirtualBox NIC)
OS Fingerprint: Linux 2.6.9 – 2.6.33
Network Distance: 1 hop
```

### 🔓 Detected Open Ports & Services

| Port | Protocol | Service | Version |
|------|----------|---------|---------|
| 21   | TCP      | FTP     | vsftpd 2.3.4 |
| 22   | TCP      | SSH     | OpenSSH 4.7p1 |
| 23   | TCP      | Telnet  | Linux telnetd |
| 25   | TCP      | SMTP    | Postfix smtpd |
| 53   | TCP      | DNS     | ISC BIND 9.4.2 |
| 80   | TCP      | HTTP    | Apache 2.2.8 |
| 139  | TCP      | SMB     | Samba smbd 3.X–4.X |
| 445  | TCP      | SMB     | Samba smbd 3.X–4.X |
| 1524 | TCP      | Bindshell | Metasploitable root shell |
| 3306 | TCP      | MySQL   | MySQL 5.0.51a |
| 5432 | TCP      | PostgreSQL | PostgreSQL 8.3.X |
| 8180 | TCP      | HTTP    | Apache Tomcat/Coyote JSP 1.1 |
| ...  | ...      | ...     | (Other services omitted for brevity) |

---

## 🧠 Interpretation & Risk Assessment

The scan revealed a wide attack surface with multiple legacy services:

- **vsftpd 2.3.4**: Known for a backdoor vulnerability.
- **OpenSSH 4.7p1**: Outdated and potentially exploitable.
- **Telnet**: Transmits credentials in plaintext—high risk.
- **Apache 2.2.8 & Tomcat 1.1**: Web services with known CVEs.
- **Samba (Ports 139/445)**: Common target for remote code execution.
- **Port 1524**: Direct root shell access—extremely dangerous.

These services collectively represent a high-risk profile, ideal for penetration testing exercises.

---

## 🧬 OS Fingerprinting

Nmap identified the host OS as:

```text
Linux Kernel 2.6.9 – 2.6.33
CPE: cpe:/o:linux:linux_kernel
```

This aligns with the known configuration of Metasploitable2 and helps inform exploit selection.

---

## ✅ Summary & Next Steps

This reconnaissance confirms that Metasploitable2 is intentionally vulnerable, with numerous exploitable services and weak configurations. The scan sets the stage for deeper vulnerability analysis using tools like **OpenVAS**, **Metasploit**, or **Nikto**.

> ⚠️ Always ensure scans are authorized and conducted in controlled environments.
