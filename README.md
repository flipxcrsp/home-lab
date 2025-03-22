# 🏠 Home Cybersecurity Lab & Network Setup

Welcome to my personal home lab documentation. This project highlights how I’ve designed and segmented my home network to support both secure daily use and an isolated cybersecurity lab environment for learning and hands-on practice.

---

## 🌐 Network Overview

### 🔹 Network Segmentation

| Network Name | Purpose                       | Isolation Settings                  | Devices                                                                 |
|--------------|-------------------------------|--------------------------------------|-------------------------------------------------------------------------|
| **Home_Net** | Trusted main network          | No isolation                         | Pop!_OS desktop, Razer laptop, Lenovo ThinkPad, Android phone, wife's devices, printers, Fire TV, Firesticks |
| **Lab_Net**  | Cybersecurity lab + IoT       | Guest mode with Device Isolation ON | Eufy security system, Echo Dots, smart plugs/lights, lab VMs, spare laptops |

- **Device Isolation** is enabled on `Lab_Net` to prevent lateral movement.
- Lab VMs will be connected either through virtual bridged adapters or routed via isolated interfaces.

---

## 🧪 Lab Environment & Tools

I am actively building a home cybersecurity lab focused on network monitoring, attack simulation, and SIEM/log analysis using free and open-source tools.

### 🔧 Virtual Machines (Hosted on Pop!_OS desktop)
- **Kali Linux** – Attacker machine with built-in tools
- **Metasploitable 2** – Vulnerable target for testing exploits
- **OWASP Juice Shop / DVWA** – Web app vulnerability practice
- **Splunk (Free)** – SIEM for log ingestion, analysis, and detection
- **Ubuntu Server** – Can be used as a log source, firewall, or sensor

### 🔍 Traffic & Log Analysis
- **Wireshark** – Packet inspection and filtering
- **Zeek** *(planned)* – Network traffic logging
- **Splunk Universal Forwarder** – Log ingestion from other lab machines

---

## 🛡️ Security Practices

- All lab environments are isolated from production devices.
- Using virtual machines enables safe testing, easy snapshots, and fast recovery.
- Logs are analyzed using Splunk, and packet data is collected with Wireshark for learning network behavior.
- Future enhancements include implementing IDS/IPS systems (e.g., Suricata or Zeek) and possibly setting up pfSense.

---

## 📜 Certifications & Learning Goals

### ✅ Current Certifications
- CompTIA A+
- CompTIA Network+
- CompTIA Security+

### 🎯 In Progress / Future Goals
- CompTIA CySA+
- Cisco Certified CyberOps Associate (CCCA)
- Practical experience with:
  - SIEM & log correlation
  - Vulnerability scanning
  - Hardening techniques (Linux/Windows)
  - IDS/IPS and threat detection
  - Cloud & container security

---

## 👨‍💻 Cross-Platform Familiarity

I regularly work with **Linux (Pop!_OS)** and **Windows**, and I’m expanding my awareness of **macOS security practices** to maintain versatility across environments. While I don’t actively use macOS hardware, I study its structure, permissions, and logs to stay well-rounded.

---

## 📁 Repo Structure (Planned)
```
home-lab/
├── README.md
├── network-diagram.png
├── pcaps/
│   └── traffic-analysis.md
├── lab-configs/
│   ├── kali-notes.md
│   ├── metasploitable.md
│   └── splunk-setup.md
└── attack-scenarios/
    ├── brute-force-ssh.md
    ├── sql-injection-dvwa.md
    └── reverse-shell-kali.md
```

---

## 🚧 Work In Progress

This is a living repo that will evolve as I gain experience, build new lab environments, and document my cybersecurity journey.

Stay tuned for:
- Sample packet captures and attack writeups
- Screenshots from Splunk dashboards and Wireshark
- IDS/IPS setups with Zeek or Suricata
- Lab automation and possible Ansible/Infrastructure-as-Code experiments

---

## 🤝 Let's Connect

Interested in collaborating or have suggestions?  
Feel free to connect or message me via GitHub!
