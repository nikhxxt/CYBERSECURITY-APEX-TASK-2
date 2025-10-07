# 📡 Network Traffic Analysis & SYN Flood Simulation – Wireshark Report

**Date:** 19 September 2025  
**Analyst:** Pratham Khairmode  
**Purpose:** To monitor and dissect network traffic involving HTTP, DNS, and FTP protocols, expose vulnerabilities in plaintext transmissions, and emulate a TCP SYN flood attack to study its network footprint.

---

## 🧰 Tools & Environment

- **Wireshark** – Used for packet capture and protocol inspection  
- **hping3** – Utility for crafting and flooding packets  
- **Platform:** Kali Linux VM (VirtualBox)

---

## 🧪 Procedure Breakdown

The analysis was divided into three focused segments:

---

### 🔍 Segment 1: Capturing Protocol Traffic

**Steps Taken:**

- Initiated live capture on interface `eth0` using Wireshark  
- Generated traffic by:
  - Visiting `http://http.net` to trigger DNS and HTTP exchanges
  - Connecting to `ftp.debian.org` via FTP client to initiate command/control flow

**Filtering Applied:**

- `dns` → Tracked domain resolution  
- `http` → Revealed unencrypted GET requests  
- `ftp` → Displayed session commands and responses

---

### 🔐 Segment 2: FTP Credential Exposure

**Goal:** Highlight risks of transmitting sensitive data over unencrypted channels

**Process:**

- Applied `ftp` filter to isolate relevant packets  
- Located authentication commands (`USER`, `PASS`)  
- Used **Follow TCP Stream** to reconstruct session

**Outcome:**  
Credentials were clearly visible in raw text, confirming that FTP exposes login data without encryption.

---

### 💥 Segment 3: SYN Flood Emulation

**Objective:** Simulate a denial-of-service attack and observe its network signature

**Execution:**

- Started a new capture with filter:  
  ```text
  tcp.flags.syn == 1 and tcp.flags.ack == 0
  ```
- Launched flood using:
  ```bash
  sudo hping3 -S --flood -V 10.0.2.15
  ```

**Observations:**

- Massive influx of `[SYN]` packets targeting `10.0.2.15`  
- Source IPs were randomized to obscure origin  
- No `ACK` responses—indicating incomplete handshakes

---

## ✅ Summary & Insights

This hands-on exercise reinforced key cybersecurity concepts:

- **FTP Risks:** Plaintext protocols like FTP are inherently insecure. Use encrypted alternatives (SFTP, FTPS) for safe data transmission.
- **DoS Detection:** SYN flood attacks leave a distinct trace—high volume of SYN packets from spoofed IPs targeting a single host.
- **Wireshark Utility:** Packet-level visibility is essential for diagnosing threats, analyzing performance, and defending networks.

---
