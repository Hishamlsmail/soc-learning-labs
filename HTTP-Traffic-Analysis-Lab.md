# 🦈 Wireshark Traffic Analysis: HTTP Protocol & OSI Model Mapping

## 📌 Project Overview
This lab demonstrates practical packet inspection using **Wireshark**. The primary focus was capturing unencrypted HTTP traffic to analyze protocol headers, understand the **TCP 3-Way Handshake**, and map captured data directly to the layers of the **OSI Model**.

---

## 🛠️ Tools Used
* **Network Analyzer:** Wireshark
* **Interface:** Wi-Fi (`192.168.1.3`)
* **Protocol Analyzed:** HTTP (Hypertext Transfer Protocol) / TCP

---

## 🧪 OSI Model Encapsulation Breakdown

Based on Packet `#5002` (`GET / HTTP/1.1`), the encapsulation process across the OSI layers is mapped as follows:

| OSI Layer | Protocol / Header | Captured Data Summary |
| :--- | :--- | :--- |
| **Layer 7 - Application** | HTTP | `GET / HTTP/1.1` (Host: `neverssl.com`) |
| **Layer 4 - Transport** | TCP | Src Port: `62203`, Dst Port: `80`, Seq: `1`, Ack: `1` |
| **Layer 3 - Network** | IPv4 | Src IP: `192.168.1.3`, Dst IP: `34.223.124.45` |
| **Layer 2 - Data Link** | Ethernet II | Src MAC: `Intel_f2:dc:a8`, Dst MAC: `HuaweiTechno_99:5d:9f` |
| **Layer 1 - Physical** | Frame | Frame 5002: 490 bytes on wire (3920 bits) |
<img width="3840" height="2400" alt="Screenshot 2026-08-26 034540" src="https://github.com/user-attachments/assets/7f400282-244e-42f2-b703-f5b9a77e764f" />

---

## 🔍 Key Observations & Analysis

### 1. TCP Handshake Sequence
Before transmitting the HTTP request, a standard 3-way handshake was established with the remote web server (`34.223.124.45`):
1. **SYN (Packet #4995):** Client initiated connection on Port `80` (`53834 -> 80`).
2. **SYN-ACK (Packet #5000):** Server responded accepting the connection.
3. **ACK (Packet #5001):** Connection established.

---

### 2. HTTP Request Inspection
* **Method:** `GET` request to retrieve web content in cleartext.
* **Target Host:** `neverssl.com`
* **Cleartext Exposure:** Full HTTP request headers and User-Agent details were visibly readable in the Hex / ASCII pane without decryption.
<img width="3840" height="2400" alt="Screenshot 2026-08-26 034640" src="https://github.com/user-attachments/assets/45f1235d-f272-4ed2-b7ab-9711d53a9087" />

---

## 📈 Key Learnings
* **Deep Packet Inspection:** Understanding how data is encapsulated as it moves down the OSI stack.
* **Cleartext Vulnerability:** Observing firsthand why unencrypted HTTP is susceptible to eavesdropping compared to HTTPS/TLS.
* **Filter Mastery:** Utilizing Wireshark display filters (`http`) to isolate target protocols effectively.
