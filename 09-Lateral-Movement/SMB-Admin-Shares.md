# SMB/Windows Admin Shares (T1021.002)

## Overview
Adversaries may use valid accounts with administrative privileges to move laterally within a network using Windows Admin Shares (e.g., `C$`, `ADMIN$`).

## Execution

### 1. Mounting a Share
```cmd
net use Z: \\Target-PC\C$ /user:DOMAIN\Username Password
```

### 2. Impacket (psexec.py)
A common red team tool to gain a shell on a remote system via SMB and the `ADMIN$` share.
```bash
impacket-psexec DOMAIN/Username:Password@Target-IP
```

## OPSEC Considerations
* Successful and failed logins are logged (Event IDs 4624, 4625).
* Using `psexec` creates a service on the target machine, which is highly visible to EDRs.

## Mitigations
* Disable Administrative Shares if not required.
* Restrict local administrator privileges.
* Monitor for Event ID 4624 with logon type 3 (Network).
