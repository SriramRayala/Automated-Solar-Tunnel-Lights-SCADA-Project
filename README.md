# Automated-Solar-Tunnel-Lights-SCADA-Project

# 🔆 Automated Solar Tunnel Lights – SCADA Cybersecurity Project

This repository presents the design, implementation, and security hardening of a SCADA-based Automated Tunnel Lighting System powered by solar energy. The project was conducted as part of **BFOR 632 – Cyber Vulnerabilities Exploitation** at the **University at Albany, SUNY**.

---

## 📌 Project Summary

Traditional tunnel lighting systems waste energy by staying on continuously. This project introduces a smart, motion-triggered lighting system powered by solar panels and secured with layered cybersecurity measures.

- Control Core: Raspberry Pi
- Sensors: PIR Motion
- Lighting: 12V LED strip controlled via relay
- Monitoring: Node-RED HMI dashboard
- Power Source: Solar panel with battery storage
- Security Tools: iptables, Fail2Ban, SSH hardening, network segmentation

---

## 🧱 System Architecture

- Motion Sensor (PIR) triggers light ON via GPIO
- Relay Module switches 12V LED strip
- Manual Override via Node-RED buttons
- Raspberry Pi manages logic and logs motion activity
- Node-RED Dashboard displays real-time status (auto/manual)
- System Logs saved locally, monitored via `/var/log` and Fail2Ban

> Full integration of automated + manual lighting, energy independence, and cybersecurity in one compact SCADA prototype.

---

## 🧩 Component List

| Component         | Purpose                                                   |
|------------------|-----------------------------------------------------------|
| Raspberry Pi      | Main controller, GPIO logic, HMI hosting, logging         |
| PIR Motion Sensor | Detects vehicles to trigger lighting                      |
| 12V LED Strip     | Tunnel lighting (activated only when motion is detected) |
| 5V Relay Module   | Switches high-power LED circuit via GPIO                 |
| Solar Panel       | Generates power                                           |
| Battery           | Stores energy for night/low light operation              |
| Node-RED          | Web-based HMI for real-time system control & monitoring  |

---

## 🔐 Security Implementation

### Network Security
- Operates on a private local network (no internet exposure)
- SSH access limited to known IPs
- iptables restricts traffic to essential services

### Host Security
- SSH root login disabled
- Strong password policy enforced
- Fail2Ban monitors and blocks repeated login attempts

### HMI Security
- Node-RED dashboard secured with password authentication
- Future recommendation: HTTPS, OAuth2, account lockouts

---

## 🧠 Exploitation & Countermeasures

| Phase                  | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| Reconnaissance         | Wireshark & Nmap revealed open ports (22, 1880) on the Solar Pi             |
| Attack Execution       | Hydra used to brute-force SSH, gain access to system                        |
| Post-Exploitation      | Accessed Node-RED config, reset credentials, modified logic flows           |
| Hardening Response     | Installed Fail2Ban, configured iptables, and secured Node-RED dashboard     |

---

## 🛡️ Monitoring and Detection Tools

- Fail2Ban: Bans IPs after repeated SSH login failures
- Syslog Monitoring: Regular reviews of `/var/log/syslog` and `/var/log/auth.log`
- SSH Audit: Periodic review of active and historical SSH sessions

---

## 🚀 Future Enhancements

- Integrate light and fog sensors for adaptive lighting
- Add traffic counters and lightweight ML-based predictions
- Centralized multi-tunnel control via secure MQTT or VPN
- Deploy Security Onion for network-based anomaly detection
- Enforce 2FA for SSH and dashboard access

---

## 🎓 Academic Details

- Course: BFOR 632 – Cyber Vulnerabilities Exploitation  
- Professors: Dominick Foti & Sanjay Goel  
- University: University at Albany, State University of New York  
- Date: June 13, 2025  
- Team Number: 2  
- Team Members:
  - Melpomeni Doutsis  
  - Steve Correia  
  - Leela Pavan  
  - Sriram Rayala  
  - Srivarsha Adla  

---

## 📄 License

This work is licensed under the  
**Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International (CC BY-NC-ND 4.0)**

📌 *You may view and share this project with proper credit, but you may not modify it or use it commercially.*

🔗 [View License Terms](https://creativecommons.org/licenses/by-nc-nd/4.0/)
