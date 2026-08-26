# 🛡️ pfSense Firewall Deployment & Traffic Filtering Lab

## 📌 Project Overview
This lab demonstrates the installation, configuration, and practical verification of a **pfSense Firewall** deployed within a **VMware Workstation** virtualized environment. The primary objective was to configure network security rules and validate active traffic dropping for unauthorized services.

---

## 🛠️ Environment & Tools
* **Hypervisor:** VMware Workstation
* **Firewall System:** pfSense Community Edition (FreeBSD-based)
* **OS Target:** FreeBSD 64-bit
* **Management Interface:** WebGUI (HTTPS)
* **Testing Tool:** Windows PowerShell / Command Prompt (CMD)

---

## 🚀 Lab Implementation Steps

### 1. VM Provisioning & ISO Setup
* Configured a custom Virtual Machine assigned with FreeBSD (64-bit) architecture.
* Mounted the extracted `netgate-installer/pfSense` ISO file to the virtual IDE CD/DVD drive.
* Allocated **1 GB RAM**, **1 CPU Core**, and **11 GB Hard Disk Space**.
* Established the initial network bridge using **NAT Mode** for the WAN interface.

### 2. Initial Setup & WebGUI Access
* Booted the virtual machine and completed the core FreeBSD deployment.
* Obtained the primary WAN IP address assigned dynamically: `192.168.76.136`.
* Successfully accessed the pfSense Web GUI administration dashboard via a host browser.

---

## 🔒 Security Configuration: SSH Blocking Rule

To reduce the attack surface and prevent unauthorized remote management attempts over the WAN, a custom **Inbound Block Rule** was implemented.

### Rule Parameters:
| Setting | Value | Description |
| :--- | :--- | :--- |
| **Action** | `Block` | Drop matching incoming packets immediately |
| **Interface** | `WAN` | Applied strictly to external traffic |
| **Protocol** | `TCP` | Filter Transmission Control Protocol packets |
| **Source** | `Any` | Block incoming attempts from any remote host |
| **Destination Port** | `22 (SSH)` | Target standard Secure Shell access port |

---

## 🧪 Verification & Proof of Concept (PoC)

To verify the policy enforcement, an outbound connection attempt was initiated from the Host OS using native SSH CLI.

### Command Executed:
`ssh admin@192.168.76.136`

<img src="https://github.com/user-attachments/assets/7efeda8d-f7a0-4931-835d-3f2582aca97f" />
