# 🌐 DNS Reconnaissance & Query Analysis Lab

## 📌 Project Overview
This project demonstrates basic **DNS Enumeration and Analysis** using the native command-line tool `nslookup`. The purpose of this lab is to inspect domain-to-IP resolution (A/AAAA records) and mail exchange infrastructure (MX records) for external domain reconnaissance.

---

## 🛠️ Tools Used
* **Operating System:** Windows 11
* **Command Tool:** Windows Command Prompt (CMD / CLI)
* **Protocol Analyzed:** Domain Name System (DNS)

---

## 🧪 Executed Queries & Results

### 1. Standard Domain Resolution (A & AAAA Records)
Querying the domain `google.com` to resolve its primary IPv4 and IPv6 addresses.

**Command:**
`nslookup google.com`

**Output Breakdown:**
* **IPv4 Address:** `142.251.209.174`
* **IPv6 Address:** `2a00:1450:4006:81a::200e`
<img width="1905" height="2260" alt="Screenshot 2026-08-26 035033" src="https://github.com/user-attachments/assets/7954a2ba-f193-4d5a-a27e-5993714f0830" />

---

### 2. Mail Exchange Query (MX Records)
Querying specific DNS resource records (`-type=MX`) to identify configured mail servers handling email traffic for `google.com`.

**Command:**
`nslookup -type=MX google.com`

**Output Breakdown:**
* **Primary Mail Exchange Host:** `smtp.google.com` (Preference = 10)
* **Resolved Mail Server IP Pools:**
  * `64.233.166.26`
  * `74.125.71.26`
  * `74.125.71.27`
  * `74.125.133.26`
  * `74.125.133.27`
 
    <img width="3840" height="2400" alt="Screenshot 2026-08-26 035117" src="https://github.com/user-attachments/assets/384236ab-e9e8-4ca7-95d4-3cfb552697cd" />
