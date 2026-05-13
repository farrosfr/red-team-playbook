# Contributing

Contributions are welcome for educational, defensive, and authorized security research content. Keep submissions practical, sourced, and mapped to MITRE ATT&CK where possible.

## Scope

Good contributions include:

- New technique notes for authorized red team operations.
- Improvements to existing methodology, OPSEC notes, and mitigations.
- Lab-safe examples that help readers understand a concept.
- References to vendor documentation, MITRE ATT&CK, or reputable research.
- Fixes for broken links, unclear wording, formatting, and navigation.

Do not submit:

- Content intended for unauthorized access or real-world abuse.
- Live targets, leaked data, credentials, tokens, or private infrastructure details.
- Malware, destructive payloads, persistence kits, or stealth code intended for misuse.
- Unverified claims without enough context for readers to validate them.

## Technique Format

Use this structure for new technique pages:

```md
# Technique Name

## Overview

Briefly explain what the technique is and when it appears in authorized assessments.

## MITRE ATT&CK Mapping

- Tactic: ...
- Technique: ...
- ID: ...

## Prerequisites

- Authorized test scope.
- Lab or target conditions required.

## Methodology

Explain the workflow at a high level. Prefer lab-safe commands and avoid unnecessary weaponization.

## OPSEC Considerations

- Logging artifacts.
- Detection opportunities.
- Noisy actions.

## Mitigations

- Defensive controls.
- Hardening guidance.
- Detection ideas.

## References

- [MITRE ATT&CK](https://attack.mitre.org/)
```

## Pull Request Checklist

- The content is legal, educational, and scoped to authorized testing.
- MITRE mapping is included when applicable.
- OPSEC and mitigation sections are included.
- Commands are lab-safe and clearly explained.
- References are included for non-obvious claims.
- Links and headings render correctly in MkDocs.

## Local Preview

Install MkDocs and preview the site locally:

```sh
pip install mkdocs mkdocs-material
mkdocs serve
```

