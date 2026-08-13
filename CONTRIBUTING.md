# Contributing to megaploit-community/playbooks

Thank you for contributing. Every playbook here comes from real engagement experience — that's what makes this library valuable.

## Quick start

1. **Fork** this repository
2. Copy [`PLAYBOOK_TEMPLATE.rc`](PLAYBOOK_TEMPLATE.rc) to a new file
3. Write your playbook (see format below)
4. Test it in Megaploit
5. Open a pull request

Or use the built-in share command in Megaploit to auto-generate a PR snippet:
```
community share /path/to/your_playbook.rc
```

---

## Playbook format

Every playbook must start with this header block:

```rc
# ===========================================================================
# Megaploit Community Playbook
# ===========================================================================
# Name        : your-playbook-name      (matches catalog entry name, kebab-case)
# Version     : 1.0
# Author      : your-github-handle
# Tested on   : OS name + version you tested against
# Description : One paragraph describing what this playbook does and when
#               to use it.
#
# MITRE ATT&CK
# ------------
# T####.### Tactic: Technique Name
# T####.### Tactic: Technique Name
#
# Variables
# ---------
#   ${VAR_NAME} — description of what to set here
#
# Usage
# -----
#   community install playbook your-playbook-name
#   resource community/playbooks/your-playbook-name.rc
#
# Phases
# ------
#   1  Phase name
#   2  Phase name
# ===========================================================================
```

All fields are **required** for a PR to be accepted.

---

## Naming rules

| Rule | Detail |
|------|--------|
| Filename | `snake_case.rc` — all lowercase, underscores, `.rc` extension |
| Catalog name | `kebab-case` — matches the `name` field in `community_hub.py` |
| No spaces in filename | Use `ad_full_compromise.rc`, not `AD Full Compromise.rc` |
| Max filename length | 64 characters |

---

## MITRE ATT&CK tagging

Every playbook must tag every phase with the relevant ATT&CK technique ID.  
Use the [ATT&CK Matrix](https://attack.mitre.org/) to look up technique IDs.

Format: `# T####.### Tactic: Technique Name`  
Example: `# T1003.001 Credential Access: OS Credential Dumping: LSASS Memory`

---

## Variables

- Use `${UPPER_CASE}` for all variables
- Document every variable in the header block
- Built-in auto-variables you can use without documenting: `${DATE}`, `${TIME}`, `${TIMESTAMP}`
- Never hardcode IPs, passwords, or hostnames — always use variables

---

## Safety requirements

All playbooks must follow these rules or they will not be accepted:

1. **No real destructive operations without a clear `# WARNING` block** — shadow copy deletion, disk wipes, etc. must be flagged
2. **Simulation playbooks must clean up after themselves** — any files written must be deleted
3. **No hardcoded credentials** — use `${VAR}` placeholders
4. **No offensive payloads embedded** — playbooks call Megaploit commands, they don't embed shellcode or binaries
5. **Must be tested** — "Tested on: ???" will be rejected. Specify the exact OS and version.

---

## What we accept

| Type | Description | Example |
|------|-------------|---------|
| `attack-chain` | Multi-phase attack simulation | AD full compromise, ransomware sim |
| `lateral-movement` | Pivot techniques | SMB relay, DCOM, WinRM |
| `credential-access` | Cred harvest chains | DPAPI, browser creds, cloud IAM |
| `persistence` | Establishing long-term access | Scheduled task, WMI, UEFI |
| `detection-engineering` | Purple team / detection validation | Log monitoring coverage |
| `cloud` | Cloud platform attacks | AWS, Azure, GCP |
| `linux` | Linux-specific attack chains | Privesc, container escape |

---

## Review criteria

PRs are reviewed for:

- [ ] Valid header block with all required fields
- [ ] MITRE ATT&CK tags for every phase
- [ ] Variables documented and used consistently
- [ ] No hardcoded values
- [ ] Tested on real environment (OS version specified)
- [ ] Phases are labelled and logically ordered
- [ ] Safety requirements met

---

## Adding to the built-in catalog

Once your PR is merged, open a second PR against the [main Megaploit repo](https://github.com/Josefifir/Megaploit) to add your playbook to `_BUILTIN_CATALOG` in `megaploit/bridges/community_hub.py`:

```python
{
    "name":        "your-playbook-name",
    "kind":        "playbook",
    "url":         "https://raw.githubusercontent.com/megaploit-community/playbooks/main/your_playbook.rc",
    "description": "One sentence description",
    "tags":        ["tag1", "tag2"],
    "author":      "your-github-handle",
},
```

---

## Code of conduct

This repository is for **authorized security testing only**.  
Do not submit playbooks designed to attack systems without permission.  
Submissions that violate this will be removed and the submitter banned.
