# ⚡️ CYBERSECURITY-APEX-TASK-2

## 🛡️ Network Security & Scanning

**Task‑2:** Step-by-step documentation of reconnaissance, scanning, firewall configuration, vulnerability analysis, and traffic inspection using tools like `nmap`, `OpenVAS`, `Wireshark`, and `iptables`.

**Goal:** Build hands-on skills in active/passive recon, port scanning, firewall rule creation, vulnerability assessment, and packet analysis using Metasploitable2 as the target VM.

---

## 🔖 Badges

[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)  
![Repo size](https://img.shields.io/github/repo-size/nikhxxt/CYBERSECURITY-APEX-TASK-2)  
![GitHub stars](https://img.shields.io/github/stars/nikhxxt/CYBERSECURITY-APEX-TASK-2?style=social)  
![GitHub forks](https://img.shields.io/github/forks/nikhxxt/CYBERSECURITY-APEX-TASK-2?style=social)

---

## 📚 Table of Contents

* [What’s Included](#whats-included)  
* [Quick Start — Reproduce the Lab](#quick-start---reproduce-the-lab)  
* [Folder Structure](#folder-structure)  
* [Commands & Verification Snippets](#commands--verification-snippets)  
* [Screenshots & Video References](#screenshots--video-references)  
* [Checklist Before Submission](#checklist-before-submission)  
* [License & Contact](#license--contact)

---

## 📦 What’s Included

### REPORTS

* `nmap_scan_report.md`  
* `iptables_firewall_configuration_report.md`  
* `openVAS.md`  
* `reconnaissance.md`  
* `wireshark_packet_analysis_report.md`

### VIDEO

* `video.mp4` — demo walkthrough

### LICENSE

* MIT License included

---

## Quick Start — Reproduce the Lab

1. **Clone the repository**

```bash
git clone https://github.com/nikhxxt/CYBERSECURITY-APEX-TASK-2.git
cd CYBERSECURITY-APEX-TASK-2
```

2. **Start Metasploitable2 VM and Kali Linux**

* Ensure both are on the same subnet  
* Verify connectivity using `ping` and `nmap`

3. **Run Reconnaissance & Scanning**

```bash
# Passive Recon
whois apexplanet.in
nslookup apexplanet.in
# Active Recon
ping -c 3 <target-ip>
telnet <target-ip> <port>  # banner grabbing
```

4. **Run Nmap Scans**

```bash
# TCP & UDP scans
sudo nmap -sS -sU -Pn <target-ip>
# Service & OS detection
sudo nmap -sV -O <target-ip>
```

5. **Run Vulnerability Scan**

* Setup OpenVAS or Nessus Essentials  
* Scan Metasploitable2  
* Export and analyze report

6. **Firewall Configuration**

```bash
# Block port scan attempts
sudo iptables -A INPUT -p tcp --tcp-flags ALL NONE -j DROP
sudo iptables -A INPUT -p tcp --tcp-flags SYN,ACK SYN -j DROP
```

7. **Capture & Analyze Traffic**

```bash
# Capture FTP credentials
sudo wireshark
# Simulate SYN flood
sudo hping3 -c 10000 -d 120 -S -w 64 -p 80 --flood <target-ip>
```

---

## Commands & Verification Snippets

### Reconnaissance

```bash
whois apexplanet.in
nslookup apexplanet.in
shodan search "apache"
```

### Nmap Scanning

```bash
sudo nmap -sS -sU -sV -O -Pn <target-ip>
```

### Firewall Rules

```bash
sudo iptables -L
sudo iptables -A INPUT -p tcp --dport 23 -j DROP
```

### Wireshark Capture

```bash
sudo wireshark
# OR
sudo tshark -i eth0 -c 100 -w /tmp/task2_capture.pcap
```

---

**LinkedIn walkthrough:**  
[Demo Video Link](https://www.linkedin.com/posts/nikhat-naaz-malki-shaik-8240aa31a_cybersecurity-internship-apexplanet-activity-7381250580087844864-PUnb?utm_source=share&utm_medium=member_desktop&rcm=ACoAAFDQ0hwBssVRSllABDcGpxoifixeymEi_nY)

---

## Checklist Before Submission

* [x] Nmap Scan Report  
* [x] Firewall Configuration  
* [x] Vulnerability Assessment  
* [x] Wireshark Traffic Analysis  
* [x] Reconnaissance Documentation  
* [x] Demo Video uploaded  
* [x] MIT License included  
* [x] README includes TOC, commands, and verification steps

---

## License & Contact

This project is licensed under the MIT License — see [`LICENSE`](LICENSE).
Repo: [https://github.com/nikhxxt/CYBERSECURITY-APEX-TASK-2](https://github.com/nikhxxt/CYBERSECURITY-APEX-TASK-2)




