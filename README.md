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
```bash
ssh admin@192.168.76.136


<img width="3840" height="2400" alt="Screenshot 2026-08-26 195019" src="https://github.com/user-attachments/assets/3d22002e-a428-4d2f-9246-3acee6c16393" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 194303" src="https://github.com/user-attachments/assets/a4cd2073-627e-4f2f-a815-cea8eaee1c24" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 194252" src="https://github.com/user-attachments/assets/51b2e443-4b3e-4f75-93fb-e5ad08d554e1" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 194127" src="https://github.com/user-attachments/assets/3b90ff67-5bed-415e-9c76-492e72d26959" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 192703" src="https://github.com/user-attachments/assets/67da2407-4fe1-4295-a6af-6eed4367f782" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 192425" src="https://github.com/user-attachments/assets/ef6a44b3-4714-4474-809f-df3047b5493e" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 191437" src="https://github.com/user-attachments/assets/4b025b24-813c-4a8e-b2a6-da51d9f02c7c" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 190858" src="https://github.com/user-attachments/assets/9d8385f7-78a5-4627-ab94-8ea0b8581a15" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 185734" src="https://github.com/user-attachments/assets/70769d65-81f2-4dc8-a0d8-6272d516afbb" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 050337" src="https://github.com/user-attachments/assets/7c7c878c-85a5-49d2-9d8e-237b5e69dceb" />
<img width="3840" height="2400" alt="Screenshot 2026-08-26 050027" src="https://github.com/user-attachments/assets/a29c595c-1819-45dc-83cc-32734bf26243" />
