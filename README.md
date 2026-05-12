# Linux Server Networking Lab

## Overview

This project demonstrates the deployment and configuration of a Linux networking lab using Ubuntu Server and VirtualBox.

The lab environment was built to develop practical hands-on skills in:

- Linux administration
- TCP/IP networking
- SSH remote administration
- DNS configuration
- Firewall configuration
- Packet capture analysis
- Network troubleshooting
- Infrastructure documentation

---

# Technologies Used

| Component | Technology |
|---|---|
| Hypervisor | VirtualBox |
| Server OS | Ubuntu Server |
| Client OS | Ubuntu Desktop |
| Remote Access | OpenSSH |
| Firewall | UFW |
| Packet Analysis | tcpdump |
| Route Analysis | traceroute |
| Port Analysis | ss / netstat |
| Version Control | Git |
| Repository Hosting | GitHub |

---

# Objectives

- Configure Linux networking
- Implement secure remote administration
- Configure firewall security
- Analyze network traffic
- Troubleshoot connectivity issues
- Build professional infrastructure documentation

---

# Network Architecture

## Adapter 1 — NAT

Used for:
- internet access
- package installation
- DNS resolution

## Adapter 2 — Host-Only Adapter

Used for:
- VM-to-VM communication
- SSH administration
- internal lab networking

---

# Network Topology

Add your network topology image here later.

Example:

```text
                    INTERNET
                        |
                 VirtualBox NAT
                        |
                Ubuntu Server VM
                 |            |
              NAT         Host-Only
                               |
                    Ubuntu Desktop VM
```

---

# Skills Demonstrated

- Linux Administration
- Network Configuration
- SSH Remote Access
- Firewall Management
- Packet Capture Analysis
- Network Troubleshooting
- Infrastructure Documentation
- Git & GitHub Workflow

---

# Tools & Commands Used

## Network Interfaces

```bash
ip a
```

## Routing Table

```bash
ip route
```

## SSH Service

```bash
sudo systemctl status ssh
```

## Firewall Status

```bash
sudo ufw status numbered
```

## Packet Capture

```bash
sudo tcpdump -i ens33
```

---

# Repository Structure

```text
linux-server-networking-lab/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── screenshots/
│   ├── virtualbox-network-adapters.png
│   ├── ip-address-assigned.png
│   ├── ssh-service-active.png
│   ├── successful-ssh-login.png
│   ├── ufw-firewall-status.png
│   ├── tcpdump-live-capture.png
│   ├── traceroute-analysis.png
│   ├── netstat-open-ports.png
│   └── ss-open-ports.png
    └── and more


│
├── network-diagrams/
│   └── network-topology.png
│
├── configs/
│   ├── netplan-config.yaml
│   ├── ufw-rules.txt
│   └── ssh-config.txt
│
├── troubleshooting/
│   └── network-troubleshooting.md
│
│── notes/
│    ├── linux-networking-notes.md
│    └── commands-reference.md
│    └── ssh-notes.md
│    └── firewall-notes.md
│    └── tcpdump-notes.md
│    └── routing-notes.md 
  
    
```

---

# Screenshots

Add screenshots inside:

```text
screenshots/
```

Examples:
- ssh-service-active.png
- successful-ssh-login.png
- tcpdump-live-capture.png
- traceroute-analysis.png

---

# Future Improvements

- VLAN segmentation
- Multi-server deployment
- Internal DNS server
- DHCP server deployment
- VPN configuration
- Network monitoring
- Python automation
- Ansible automation
- pfSense firewall integration

---

# Lessons Learned

Through this project, I gained practical experience in:

- configuring Linux networking
- troubleshooting connectivity issues
- securing remote administration with SSH
- configuring firewalls using UFW
- analyzing traffic using tcpdump
- managing routing and DNS
- documenting infrastructure professionally
- using Git and GitHub for version control

---

# Author

Nathaniel Agbeyangi

Electrical & Electronics Engineering | Networking | Cybersecurity | IT Infrastructure