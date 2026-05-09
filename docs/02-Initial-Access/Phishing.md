# Phishing (T1566)

## Overview
Phishing is the practice of sending fraudulent communications that appear to come from a reputable source, usually through email. The goal is to steal sensitive data like login credentials or to install malware on the victim's machine.

## Techniques

### 1. Spearphishing Attachment (T1566.001)
Sending an email with a malicious attachment (e.g., `.xlsm`, `.zip`, `.pdf`).
* **Tooling:** Gophish, Evilginx2.
* **Payloads:** Macro-enabled documents, LNK files.

### 2. Spearphishing Link (T1566.002)
Sending an email with a link to a malicious website or a credential harvesting page.
* **Credential Harvesting:** Cloning a login page using `httrack` or `Social-Engineer Toolkit (SET)`.

## OPSEC Considerations
* **Domain Age:** Use domains that have been registered for at least 30 days.
* **SMTP Reputation:** Ensure the mail server has proper SPF, DKIM, and DMARC records to avoid spam filters.
* **Tracking Pixels:** Use sparingly as they can be detected by modern mail gateways.

## Mitigations
* User awareness training.
* Multi-Factor Authentication (MFA).
* Email filtering and sandboxing solutions.
