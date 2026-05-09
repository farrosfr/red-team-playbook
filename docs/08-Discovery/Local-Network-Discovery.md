# Local Network Discovery (T1046)

## Overview
Adversaries may attempt to get a listing of other systems by IP address, hostname, or other logical identifier on a network that may be used for Lateral Movement.

## Tools and Techniques

### 1. Ping Sweeps
Simple ICMP echo requests to discover live hosts.
```bash
# Linux
for i in {1..254}; do ping -c 1 -W 1 192.168.1.$i | grep "bytes from" & done

# Windows
for /L %i in (1,1,254) do @ping -n 1 -w 100 192.168.1.%i | find "Reply"
```

### 2. ARP Scanning
More reliable on local subnets as it uses Layer 2 and isn't blocked by host firewalls.
```bash
arp-scan --localnet
```

### 3. Port Scanning
Using tools like `nmap` to discover open ports and services on discovered hosts.
```bash
nmap -sn 192.168.1.0/24
```

## OPSEC Considerations
* Active scanning is noisy and easily detected by Network Intrusion Detection Systems (NIDS).
* Use passive discovery methods where possible (e.g., listening to ARP broadcasts, analyzing local routing tables, or querying Active Directory).

## Mitigations
* Network segmentation to limit the scope of discovery.
* NIDS to detect abnormal scanning behavior.
