# Network Troubleshooting Documentation

## Overview

This document contains networking and SSH troubleshooting scenarios encountered during the Linux Server Networking Lab project.

The troubleshooting process involved:
- connectivity testing
- service verification
- interface analysis
- firewall diagnostics
- routing verification
- SSH troubleshooting
- VirtualBox adapter troubleshooting

---

# Issue 1 — No IP Address Assigned

## Symptoms

- No internet connectivity
- Unable to ping external hosts
- "Network is unreachable" error
- Interface showed no IPv4 address

---

## Investigation

Checked network interfaces:

```bash
ip a
```

Observed:
- interface was UP
- no IPv4 address assigned

---

## Cause

Incorrect VirtualBox adapter configuration.

The VM network adapter was not properly attached to:
- NAT
- Host-Only Adapter

---

## Resolution

Configured:
- Adapter 1 → NAT
- Adapter 2 → Host-Only Adapter

Applied network configuration:

```bash
sudo netplan apply
```

Verified connectivity:

```bash
ping 8.8.8.8
```

---

# Issue 2 — DNS Resolution Failure

## Symptoms

- Able to ping IP addresses
- Unable to ping domain names
- Package installation failed

Example:

```bash
ping google.com
```

Returned:
- Temporary failure in name resolution

---

## Investigation

Checked DNS configuration:

```bash
cat /etc/resolv.conf
```

Verified internet connectivity:

```bash
ping 8.8.8.8
```

---

## Cause

DNS server configuration issue.

---

## Resolution

Configured working DNS servers.

Verified:

```bash
ping google.com
```

Successfully resolved domain names.

---

# Issue 3 — SSH Connection Timeout

## Symptoms

- SSH service appeared active
- Ping connectivity successful
- SSH connection timed out from Ubuntu Desktop

Example:

```bash
ssh username@192.168.20.129
```

Returned:
- Connection timed out

---

## Investigation

Verified SSH service:

```bash
sudo systemctl status ssh
```

Verified listening port:

```bash
ss -tulnp | grep 22
```

Verified firewall rules:

```bash
sudo ufw status numbered
```

Verified network connectivity:

```bash
ping 192.168.20.129
```

---

## Cause

Possible causes identified:
- VMs connected to different Host-Only adapters
- Firewall restrictions
- Incorrect IP address used
- SSH service not properly listening
- Incorrect username used during SSH login

---

## Resolution

Confirmed:
- Both VMs connected to same Host-Only Adapter
- SSH service running correctly
- Port 22 listening
- Firewall allowed SSH traffic
- Correct IP address used

SSH connection successful after corrections.

---

# Issue 4 — UFW Firewall Blocking SSH

## Symptoms

- SSH service active
- Port 22 listening
- Ping successful
- SSH inaccessible remotely

---

## Investigation

Checked firewall status:

```bash
sudo ufw status numbered
```

Observed:
- SSH rule missing

---

## Resolution

Allowed SSH through firewall:

```bash
sudo ufw allow ssh
```

Enabled firewall:

```bash
sudo ufw enable
```

Verified firewall rules again:

```bash
sudo ufw status numbered
```

SSH access restored successfully.

---

# Issue 5 — Incorrect Static IP Configuration

## Symptoms

- Interface active
- No communication between VMs
- SSH failed
- Ping failed

---

## Investigation

Checked Netplan configuration:

```bash
sudo nano /etc/netplan/00-installer-config.yaml
```

Checked interfaces:

```bash
ip a
```

---

## Cause

Incorrect:
- subnet mask
- interface name
- YAML indentation

---

## Resolution

Corrected Netplan configuration:

```yaml
network:
  version: 2
  renderer: networkd

  ethernets:
    ens33:
      dhcp4: true

    ens37:
      dhcp4: true
      
```

Applied configuration:

```bash
sudo netplan apply
```

Connectivity restored successfully.

---

# Issue 6 — SSH Service Not Running

## Symptoms

- SSH connection refused
- Port 22 not listening

---

## Investigation

Checked SSH status:

```bash
sudo systemctl status ssh
```

Observed:
- service inactive

---

## Resolution

Started SSH service:

```bash
sudo systemctl start ssh
```

Enabled at boot:

```bash
sudo systemctl enable ssh
```

Verified listening ports:

```bash
ss -tulnp | grep 22
```

---

# Issue 7 — Incorrect SSH Username

## Symptoms

- Password rejected
- Permission denied

---

## Cause

Incorrect Linux username used during SSH login.

---

## Resolution

Verified logged-in username:

```bash
whoami
```

Used correct SSH syntax:

```bash
ssh username@192.168.20.129
```

Authentication successful.

---

# Issue 8 — VirtualBox Adapter Misconfiguration

## Symptoms

- VMs unable to communicate
- No Host-Only connectivity
- Ping failure

---

## Investigation

Verified:
- Adapter types
- Host-Only network selection
- VM network attachment

---

## Resolution

Configured:
- Adapter 1 → NAT
- Adapter 2 → Host-Only Adapter

Ensured both VMs used same Host-Only network.

---

# Issue 9 — Missing Networking Tools

## Symptoms

Commands unavailable:
- traceroute
- netstat

---

## Resolution

Installed required tools:

```bash
sudo apt install traceroute -y
```

```bash
sudo apt install net-tools -y
```

Verified commands functional.

---

# Troubleshooting Methodology Learned

This project improved practical troubleshooting skills including:

- Layered network troubleshooting
- Service verification
- Firewall diagnostics
- Interface analysis
- Connectivity testing
- Routing verification
- SSH diagnostics
- Linux service management
- VirtualBox networking troubleshooting

---

# Commands Frequently Used During Troubleshooting

## Interface Verification

```bash
ip a
```

---

## Route Verification

```bash
ip route
```

---

## Connectivity Testing

```bash
ping 8.8.8.8
```

---

## DNS Testing

```bash
ping google.com
```

---

## SSH Service Status

```bash
sudo systemctl status ssh
```

---

## Port Verification

```bash
ss -tulnp
```

---

## Firewall Status

```bash
sudo ufw status numbered
```

---

## Packet Analysis

```bash
sudo tcpdump -i ens33
```

---

# Lessons Learned

Through these troubleshooting scenarios, practical experience was gained in:

- Linux networking
- firewall troubleshooting
- SSH diagnostics
- packet analysis
- routing analysis
- virtualization networking
- DNS troubleshooting
- service management
- infrastructure debugging