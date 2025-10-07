# 🕵️‍♀️ Reconnaissance Techniques 

This section outlines both passive and active reconnaissance strategies used to gather intelligence about a target system. These methods are essential for understanding the network landscape before launching deeper assessments.

---

## 🌐 Passive Reconnaissance

Passive recon involves collecting publicly accessible data without alerting or interacting with the target directly.

### 📌 Domain Intelligence with `whois`

The `whois` utility queries domain registration databases to uncover ownership details, registrar info, and DNS configurations.

**Example Command:**

```bash
whois google.com
```

**Sample Output Highlights:**

- Domain Name: `GOOGLE.COM`
- Registrar: `MarkMonitor Inc.`
- Creation Date: `1997-09-15`
- Expiry Date: `2028-09-14`
- Name Servers: `NS1.GOOGLE.COM`, `NS2.GOOGLE.COM`, etc.

---

### 🧭 DNS Lookup with `nslookup`

`nslookup` helps resolve domain names to IP addresses and reveals DNS server details.

**Example Command:**

```bash
nslookup google.com
```

**Output Snapshot:**

- Server: `49.205.72.130`
- Resolved IPs: `142.250.183.174`, `2404:6800:4007:815::200e`

---

### 🔍 Google Dorking

Advanced search queries using Google operators (e.g., `inurl:`, `filetype:`, `intitle:`) can expose sensitive files, login portals, or misconfigured directories indexed online.

---

### 🌐 Shodan Search

Shodan is a specialized search engine that scans and indexes internet-connected devices. It can reveal open ports, banners, and exposed IoT systems across the globe.

---

## ⚡ Active Reconnaissance

Active recon involves direct interaction with the target network, which may trigger alerts or logs.

### 📡 Host Discovery via Ping Sweep

A ping sweep sends ICMP echo requests across a subnet to identify live hosts.

**Command Example:**

```bash
nmap -sn 192.168.56.0/24
```

This scan will return a list of responsive IPs within the specified range.

---

### 🏷️ Banner Grabbing

Banner grabbing connects to a service port and reads its initial response, which often includes software name and version.

**Command Example:**

```bash
nc -nv [target_ip] 80
```

This technique is useful for identifying outdated or vulnerable services.

---

📌 These reconnaissance methods form the foundation of any penetration test or vulnerability assessment. They help map the target environment and prioritize attack vectors for deeper analysis.

 
