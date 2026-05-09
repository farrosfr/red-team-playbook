# Process Injection (T1055)

## Overview
Process injection is a method of executing arbitrary code in the address space of a separate live process. Running code in the context of another process may allow access to the process's memory, system/network resources, and possibly elevated privileges.

## Common Techniques

### 1. DLL Injection (T1055.001)
Injecting a malicious DLL into a target process.
* Using `CreateRemoteThread` and `LoadLibrary` API calls.
* Often requires a custom loader or tools like Metasploit/Cobalt Strike.

### 2. Process Hollowing (T1055.012)
Starting a process in a suspended state, unmapping its legitimate code, and replacing it with malicious code before resuming the thread.

## OPSEC Considerations
* Injecting into highly monitored processes (e.g., `lsass.exe`, `explorer.exe`) can trigger EDR alerts.
* Choose target processes that blend in with normal system activity (e.g., `svchost.exe`, `notepad.exe`, browser processes).
* Cross-session injection is often flagged.

## Mitigations
* Endpoint Detection and Response (EDR) solutions are the primary defense, monitoring API calls related to memory allocation and thread creation.
* Ensure Antivirus is running and updated.
