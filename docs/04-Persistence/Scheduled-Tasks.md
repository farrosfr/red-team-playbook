# Scheduled Tasks (T1053.005)

## Overview
Adversaries may abuse task scheduling functionality to facilitate initial or recurring execution of malicious code. Utilities exist within all major operating systems to schedule programs or scripts to be executed at a specified date and time.

## Windows (schtasks)
Creating a scheduled task to execute a payload on user logon or at regular intervals.

### Create Task via Command Line
```cmd
schtasks /create /tn "UpdaterService" /tr "C:\Windows\Temp\payload.exe" /sc onlogon /ru System
```

## Linux (cron)
Adding entries to crontab to execute scripts periodically.

### Crontab Entry
```bash
echo "* * * * * /tmp/payload.sh" >> /etc/crontab
```

## OPSEC Considerations
* Avoid obvious task names. Blend in with legitimate tasks (e.g., `GoogleUpdateTaskMachineUA`, `Adobe Acrobat Update Task`).
* Scheduled tasks created by adversaries may generate Event ID 4698 (A scheduled task was created).
* Ensure payload execution does not spawn visible windows to the user.

## Mitigations
* Monitor for Event ID 4698.
* Restrict the ability of users to create scheduled tasks.
* Regularly audit scheduled tasks and crontab entries.
