# 🌐 HYBRID-X: Secure Hybrid Infrastructure

> 🚀 A hybrid IT infrastructure blueprint combining on-premises systems with cloud-based architecture for centralized security, automation, and monitoring.

---

## 📌 Overview

**HYBRID-X** is a hybrid infrastructure project designed to simulate and implement a modern enterprise IT environment combining:

- On-premises networking and system components.
- Cloud-based infrastructure using AWS.
- Centralized security monitoring using Wazuh SIEM and the ELK Stack.
- Firewall segmentation with pfSense.
- Automation-ready configuration using Ansible (planned).

This project is ideal for cybersecurity learning, system administration, infrastructure design, and cloud-hybrid integration.

---

## 🧰 Tech Stack

| Category             | Tools/Technologies                                 |
|----------------------|----------------------------------------------------|
| Operating Systems    | Ubuntu Server, Debian 12, Windows Server           |
| Cloud Infrastructure | AWS EC2, VPC, Subnets, Security Groups, IGW        |
| Security Monitoring  | [Wazuh](https://wazuh.com), ELK Stack              |
| Virtualization       | VMware Workstation                                 |
| Firewall             | pfSense                                            |
| Automation           | Ansible (Planned)                                  |
| Diagramming          | draw.io, Excalidraw, Lucidchart                    |

---

## 🧱 Project Architecture

### 🏠 Local Network (VMware Workstation)

- `vm1-local-ubuntu` — Ubuntu Endpoint Server
- `vm2-local-windows` — Windows Server Endpoint
- `vm3-pfsense-fw` — pfSense Firewall with 2 NICs (LAN & WAN)

### ☁️ Cloud Infrastructure (AWS)

- `aws-wazuh-manager` — Wazuh Server + ELK Stack
- `aws-linux-endpoint` — Ubuntu EC2 as remote endpoint

---

## 🔐 Security Highlights

- Wazuh agents installed on all endpoints (local + cloud)
- Real-time event logging and alerting
- File Integrity Monitoring (FIM)
- pfSense firewall rules to segment and secure local LAN
- AWS security groups to limit exposure to internet threats

---

## 🗂️ Directory Structure

```bash
hybrid-x/
├── aws/
│   ├── wazuh-manager-setup.md
│   ├── linux-endpoint-setup.md
├── local/
│   ├── pfSense-config/
│   ├── ubuntu-endpoint-setup.md
│   └── windows-endpoint-setup.md
├── wazuh/
│   ├── manager/
│   └── agents/
├── diagrams/
│   └── hybrid-network-diagram.png
├── playbooks/           # For future Ansible integration
├── checklist.md         # Verification steps for each phase
└── README.md
```

## 🌐 Network Diagram

![Hybrid Network Diagram](./diagrams/hybrid-network-diagram.png)

---

## 🛠️ Setup Guide

### Phase 1: Local Infrastructure (VMware)

1. **Deploy pfSense**
   - Assign 2 NICs (WAN + LAN)
   - Configure DHCP on LAN
   - Set firewall rules: Allow LAN → WAN; Deny WAN → LAN by default

2. **Deploy Ubuntu & Windows Endpoints**
   - Set static IP or use DHCP from pfSense
   - Install Wazuh agent pointing to AWS manager
   - Enable basic services for simulation (e.g., SSH, SMB)

---

### Phase 2: Cloud Infrastructure (AWS)

1. **Launch Wazuh Manager**
   - Ubuntu EC2 (t2.small recommended)
   - Use Wazuh installation script
   - Open ports 55000 (agent), 5601 (Kibana), 1514/1515 (Logstash)

2. **Launch Linux Endpoint**
   - Ubuntu EC2 (t2.micro)
   - Install Wazuh agent
   - Simulate logs/alerts

3. **Create AWS VPC**
   - Public Subnet for Wazuh Manager
   - Security Groups for access control (SSH, HTTP/S, Wazuh Ports)

---

### Phase 3: Integration

- Configure Wazuh to monitor:
  - Local Ubuntu + Windows logs
  - AWS EC2 endpoint logs
- Set up dashboards in Kibana
- Test File Integrity Monitoring (FIM)
- Forward alerts from local to cloud for centralized logging

---

### Phase 4: Automation (Planned)

- Implement Ansible to:
  - Automate server deployment
  - Configure agents
  - Push firewall settings

---

## 📅 Roadmap

- [x] Design Network Architecture
- [x] Setup Local Network in VMware
- [x] Deploy Cloud Infrastructure in AWS
- [x] Install & Configure Wazuh Manager
- [x] Connect all endpoints to Wazuh
- [ ] Automate with Ansible
- [ ] Conduct Simulated Attacks for Testing
- [ ] Document & Publish Research Findings

---

## 📚 Key Learnings

- Building secure hybrid infrastructures
- Network segmentation using pfSense
- Cloud VPC and EC2 architecture
- Security monitoring using open-source tools
- Real-time log analysis and alerting
- Preparing for DevSecOps/CloudOps roles

---

## 📬 Contact

**Author & Project Owner**  
👤 Aman Altab Mulla  
📧 [amanmullaofficial@gmail.com](mailto:amanmullaofficial@gmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/amanmullaofficial) *(optional)*  
🌐 [GitHub](https://github.com/amanmullaofficial) *(optional)*

---

## 📜 License

This project is open-source and available under the MIT License. See the `LICENSE` file for details.

---

> 🌟 Contributions, suggestions, and forks are welcome! Let's make infrastructure smarter and more secure together.
```
