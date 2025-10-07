
# 🔒 Firewall Configuration Using iptables

**Date:** September 19, 2025  
**Author:** Pratham Khairmode  
**Purpose:** Establish a secure firewall using `iptables` with a default-deny policy, allow essential traffic, and dynamically block port scans.

---

## 🛠️ Tools

- `iptables`: Linux firewall utility for packet filtering and NAT.
- `nmap`: Network scanner used to simulate and verify port scan detection.

---

## 🧪 Procedure Overview

The configuration was executed in four structured stages:

---

### ✅ Stage 1: Enforce Default-Deny Policy

Initial firewall state allowed all traffic. To secure the system:

```bash
# Drop all incoming traffic by default
sudo iptables -P INPUT DROP

# Allow return traffic from established connections
sudo iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

# Permit local loopback traffic
sudo iptables -A INPUT -i lo -j ACCEPT
```

This setup blocks all unsolicited traffic while preserving system functionality.

---

### 🚫 Stage 2: Port Scan Detection

To identify and block aggressive scanning behavior:

```bash
# Flush existing rules
sudo iptables -F

# Create a custom chain for scan detection
sudo iptables -N PORTSCAN

# Redirect new TCP SYN packets to PORTSCAN
sudo iptables -A INPUT -p tcp --syn -j PORTSCAN

# Drop IPs with 5+ hits in 60 seconds
sudo iptables -A PORTSCAN -m recent --name SCAN --update --seconds 60 --hitcount 5 -j DROP

# Track new IPs
sudo iptables -A PORTSCAN -m recent --name SCAN --set -j ACCEPT
```

This dynamic rule set reacts to suspicious behavior in real time.

---

### 🔍 Stage 3: Validation with `nmap`

To test the firewall’s response:

```bash
nmap -v 127.0.0.1
```

**Result:** The scan was partially successful before being blocked. Remaining ports appeared as `filtered`, confirming the firewall’s effectiveness.

---

### 🧹 Stage 4: Cleanup

To restore default settings:

```bash
# Flush all rules
sudo iptables -F

# Delete custom chain
sudo iptables -X PORTSCAN

# Reset default policies
sudo iptables -P INPUT ACCEPT
```

---

## 📌 Key Takeaways

- **Default-Deny is Essential:** Minimizes exposure by blocking all traffic unless explicitly allowed.
- **Dynamic Rules Enhance Security:** Modules like `recent` enable behavior-based filtering.
- **Always Validate:** Use tools like `nmap` to confirm firewall behavior.
