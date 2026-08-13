---
name: New Playbook Submission
about: Submit a new community engagement playbook
title: "[PLAYBOOK] your-playbook-name — one sentence description"
labels: new-playbook, needs-review
assignees: ''
---

## Playbook Details

**Name (kebab-case):** 
**File name (snake_case.rc):** 
**Platform:** Windows / Linux / macOS / Cloud / Multi
**Tested on (be specific):** 

## Description

<!-- One paragraph: what does this playbook do and when would an operator use it? -->

## Phases

<!-- List the phases your playbook covers -->
1. 
2. 
3. 

## MITRE ATT&CK Techniques Covered

<!-- List every T#### covered, one per line -->
- T
- T

## Variables Required

<!-- List all ${VAR} the operator needs to set -->
- `${SESSION}` — 
- `${LHOST}` — 

## Testing

- [ ] Tested successfully against the OS/version listed above
- [ ] All phases produce expected output
- [ ] Variables are documented in the header block
- [ ] All simulation artefacts are cleaned up (if applicable)
- [ ] No hardcoded IPs, passwords, or hostnames

## Checklist

- [ ] Header block is complete (Name, Version, Author, Tested on, Description, MITRE, Variables, Usage, Phases)
- [ ] File is named `snake_case.rc`
- [ ] Catalog name is `kebab-case`
- [ ] No destructive operations without a `# WARNING` comment
- [ ] Read [CONTRIBUTING.md](../CONTRIBUTING.md)

## Additional Notes

<!-- Anything else reviewers should know -->
