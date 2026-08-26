# 🏦 Multi-Branch Enterprise Bank Network Design & Routing Lab

## 📌 Project Overview
This project presents the full design, implementation, and routing verification of a secure **multi-branch enterprise bank network** built in **Cisco Packet Tracer**[cite: 1]. The architecture connects a Central Headquarters (HQ) with three operational bank branches: **Nasr City**, **Maadi (MR)**, and **New Cairo**[cite: 1].

<!-- DROP SCREENSHOT 1 HERE (Screenshot 2026-08-26 222434.jpg - Topology) -->
<img width="3840" height="2400" alt="Screenshot 2026-08-26 222434" src="https://github.com/user-attachments/assets/61d38ee4-a552-479b-ba7d-bd25db66a7b7" />

---

## 🛠️ Network Architecture & Topology Specifications

* **Topology Infrastructure:** 4 Routers, 4 Switches, 12 Workstations (PCs), and 1 Central Enterprise Server deployed at HQ[cite: 1].
* **Dynamic Routing Protocol:** RIPv2 (Routing Information Protocol version 2) configured with explicit subnetting and zero automatic summarization[cite: 1].
<img width="3840" height="2400" alt="Screenshot 2026-08-26 222826" src="https://github.com/user-attachments/assets/c11a120f-311a-4016-9fcb-1c16a32a27d8" />

### 📐 Subnetting & IP Addressing Scheme

| Network Location | Subnet Range | Subnet Mask | Role / Description |
| :--- | :--- | :--- | :--- |
| **HQ LAN** | `192.168.0.0/29` | `255.255.255.248` | HQ Local Subnet & Central Server[cite: 1] |
| **Nasr City LAN** | `192.168.1.0/29` | `255.255.255.248` | Branch Local Subnet[cite: 1] |
| **Maadi (MR) LAN** | `192.168.2.0/29` | `255.255.255.248` | Branch Local Subnet[cite: 1] |
| **New Cairo LAN** | `192.168.3.0/29` | `255.255.255.248` | Branch Local Subnet[cite: 1] |
| **HQ - Nasr WAN** | `10.0.0.0/30` | `255.255.255.252` | Point-to-Point WAN Link[cite: 1] |
| **HQ - MR WAN** | `10.0.1.0/30` | `255.255.255.252` | Point-to-Point Serial WAN Link[cite: 1] |
| **HQ - New Cairo WAN** | `10.0.2.0/30` | `255.255.255.252` | Point-to-Point Gigabit WAN Link[cite: 1] |

---

## ⚙️ Core Cisco IOS Configuration Excerpt (HQ Router)

### 1. Interface IP & Clock Rate Setup
```cisco
enable
configure terminal
interface GigabitEthernet0/0
 ip address 192.168.0.1 255.255.255.248
 no shutdown
interface GigabitEthernet0/1
 ip address 10.0.2.1 255.255.255.252
 no shutdown
interface Serial0/2/0
 ip address 10.0.1.1 255.255.255.252
 clock rate 64000
 no shutdown
```[cite: 1]

### 2. Dynamic RIPv2 Configuration
```cisco
router rip
 version 2
 no auto-summary
 network 192.168.0.0
 network 10.0.0.0
 network 10.0.1.0
 network 10.0.2.0
```[cite: 1]

---

## 🧪 Verification & Network Testing

### 1. Dynamic Routing Table Inspection (`show ip route`)
Confirmed route learning across network segments via RIP (`R` entries)[cite: 1]:

<!-- DROP SCREENSHOT 2 HERE (Screenshot 2026-08-26 222826.jpg - Routing Table) -->

### 2. End-to-End ICMP Reachability Test (`ping`)
Verified successful end-to-end connectivity between branch hosts and HQ infrastructure[cite: 1]:

<!-- DROP SCREENSHOT 3 HERE (Screenshot 2026-08-26 223026.jpg - Ping Command) -->
<img width="3840" height="2400" alt="Screenshot 2026-08-26 223026" src="https://github.com/user-attachments/assets/5364256d-e837-4c51-957a-c8658afe0e2a" />

---

## 📈 Key Technical Takeaways
* **VLSM & Custom Subnetting:** Designing `/29` subnets for restricted LAN hosts and `/30` point-to-point WAN links to minimize IP waste[cite: 1].
* **Dynamic Routing Protocols:** Disabling classful auto-summarization (`no auto-summary`) in RIPv2 to support discontinuous subnets[cite: 1].
* **Enterprise Topology Design:** Constructing hub-and-spoke multi-branch connectivity for corporate infrastructure[cite: 1].
