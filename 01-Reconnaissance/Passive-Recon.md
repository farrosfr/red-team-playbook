# Passive Reconnaissance

## Overview
Passive reconnaissance involves gathering information about a target without directly interacting with their infrastructure. This minimizes the risk of detection.

## Techniques

### 1. WHOIS Enumeration
Used to find domain registration details and contact information.
```bash
whois example.com
```

### 2. Search Engine Dorking (Google Dorks)
Find exposed sensitive files or login portals.
- `site:target.com filetype:pdf`
- `site:target.com inurl:login`
- `site:target.com "index of /"`

### 3. Subdomain Enumeration (Passive)
Using third-party services like Sublist3r or crt.sh.
```bash
# Using crt.sh
curl -s "https://crt.sh/?q=example.com&output=json" | jq -r '.[].name_value' | sed 's/\*\.//g' | sort -u
```

## OPSEC Considerations
* Truly passive - the target sees no traffic.
* Use a VPN or Tor when performing these searches to protect your source IP.
