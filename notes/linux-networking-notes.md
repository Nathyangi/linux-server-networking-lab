# Linux Networking Notes

## Linux Network Interfaces

Linux uses interface names such as:

- ens33
- ens37

These interfaces handle network communication.

---

# NAT Adapter

The NAT adapter provides:

- internet connectivity
- package downloads
- DNS access

The interface receives an IP address automatically using DHCP.

---

# Host-Only Adapter

The Host-Only adapter enables communication between:

- Ubuntu Server
- Ubuntu Desktop
- Host Machine

without exposing systems directly to external networks.

---

# Netplan Configuration

Ubuntu Server uses Netplan for network configuration.

## Apply Configuration

```bash
sudo netplan apply
```

## Verify Interfaces

```bash
ip a
```

---

# DNS Verification

DNS servers can be verified using:

```bash
cat /etc/resolv.conf
```

---

# Lessons Learned

- Learned Linux network interface management
- Learned VirtualBox network architecture
- Learned DHCP configuration using Netplan
- Learned DNS verification