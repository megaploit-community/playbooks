<div align="center">

# 📋 megaploit-community / playbooks

**Community engagement playbooks for the [Megaploit C2](https://github.com/Josefifir/Megaploit) framework.**

[![Playbooks](https://img.shields.io/badge/playbooks-4-blue?style=flat-square)](#catalog)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey?style=flat-square)]()
[![GUI](https://img.shields.io/badge/GUI-Megaploit--GUI-purple?style=flat-square)](https://github.com/megaploit-community/Megaploit-GUI)

</div>

---

## What are playbooks?

Playbooks are plain-text `.rc` files — one Megaploit console command per line.  
They automate multi-phase attack chains so operators can focus on decision-making rather than typing.

```rc
# Example — one command per line, # for comments
session 3
shell whoami /all
kiwi logonpasswords
log_wipe Security
```

Variables like `${LHOST}`, `${DOMAIN}`, `${SESSION}` are interpolated at runtime.

---

## Install in one command

From the **Megaploit console**:

```
community install playbook ad-full-compromise
community install playbook ransomware-simulation
community install playbook cloud-pivot-aws
community install playbook linux-priv-esc-chain
```

Or load any `.rc` file directly without installing:

```
resource /path/to/playbook.rc
```

---

## Catalog

| Name | File | Platform | Phases | MITRE Tactics |
|------|------|----------|--------|---------------|
| [`ad-full-compromise`](ad_full_compromise.rc) | `ad_full_compromise.rc` | Windows / AD | 8 | Recon, CredAccess, LateralMovement, Persistence, DefenseEvasion |
| [`ransomware-simulation`](ransomware_sim.rc) | `ransomware_sim.rc` | Windows | 7 | Impact, DefenseEvasion, CredAccess, Discovery |
| [`cloud-pivot-aws`](cloud_pivot_aws.rc) | `cloud_pivot_aws.rc` | Linux / AWS | 8 | CredAccess, Discovery, LateralMovement |
| [`linux-priv-esc-chain`](linux_privesc.rc) | `linux_privesc.rc` | Linux | 10 | PrivilegeEscalation, CredAccess, Discovery |

Full details: **[CATALOG.md](CATALOG.md)**

---

## Playbook Details

### `ad-full-compromise`
> Full Active Directory compromise chain

**Phases:**
1. Situational awareness (whoami, domain enum)
2. Local privilege escalation (UAC bypass)
3. Credential harvest (LSASS, SAM, DPAPI)
4. Kerberoasting (SPN enumeration + TGS)
5. Lateral movement to Domain Controller (WinRM / PTH)
6. DCSync — dump all domain hashes
7. Persistence (scheduled task + WMI)
8. Evidence suppression (logs, USN journal, prefetch, timestomp)

**Requirements:** Unprivileged initial session on a domain-joined machine.

---

### `ransomware-simulation`
> Purple team ransomware simulation — no real encryption

**What it tests:**
- AV/EDR response to realtime monitoring disable
- Shadow copy deletion detection (T1490)
- Event log clearing detection (T1070.001)
- File creation in user directories (T1486 simulation)

**Safe for lab use.** No files are encrypted. All simulation markers are cleaned up automatically.

---

### `cloud-pivot-aws`
> AWS lateral movement via IMDS credential harvest

**Phases:**
1. IMDSv1 credential harvest
2. IMDSv2 token-based harvest (fallback)
3. User-data secret scraping
4. Environment variable enumeration
5. IAM account discovery
6. S3 bucket enumeration + data staging
7. SSM-based lateral movement to other EC2 instances
8. IAM privilege escalation path check

**Requirements:** Shell on an EC2 instance with an attached IAM role.

---

### `linux-priv-esc-chain`
> Systematic Linux privilege escalation

**Checks (10 phases):**
SUID/SGID abuse · Sudo -l misconfig · Cron job hijack · Writable systemd units · PATH hijacking · LD_PRELOAD · Private keys/credentials · Writable /etc/passwd · Docker/LXC escape · Kernel exploit surface

---

## Usage

### Basic
```
# Install and run
community install playbook ad-full-compromise
resource community/playbooks/ad-full-compromise.rc
```

### With variables
```
# Set variables before running
set lhost 10.10.10.1
set port 443
resource playbooks/ad_full_compromise.rc
```

### Variables reference

| Variable | Description | Example |
|----------|-------------|---------|
| `${LHOST}` | C2 listener IP | `10.10.10.1` |
| `${LPORT}` | C2 listener port | `443` |
| `${DOMAIN}` | Target domain | `corp.local` |
| `${DC}` | Domain controller IP/hostname | `dc01.corp.local` |
| `${SESSION}` | Target session ID | `3` |
| `${DATE}` | Current date (auto) | `2025-01-01` |
| `${TIMESTAMP}` | Datetime stamp (auto) | `20250101_120000` |

---

## Writing your own

Copy [`PLAYBOOK_TEMPLATE.rc`](PLAYBOOK_TEMPLATE.rc), fill in the header block, add your commands.

Required header fields:
```rc
# Objective  : one sentence
# Variables  : list all ${VAR} used
# MITRE ATT&CK: T####.### Name, ...
# Tested on  : Windows 10 21H2 / Server 2019
# Author     : your handle
```

Use `community share <path>` in Megaploit to auto-generate a PR snippet:
```
community share ./my_playbook.rc
```

See **[CONTRIBUTING.md](CONTRIBUTING.md)** for the full guide.

---

## Repository Layout

```
playbooks/
├── README.md                  ← you are here
├── CATALOG.md                 ← full searchable index
├── CONTRIBUTING.md            ← how to submit a playbook
├── PLAYBOOK_TEMPLATE.rc       ← starter template
├── LICENSE
│
├── ad_full_compromise.rc      ← AD compromise chain
├── ransomware_sim.rc          ← ransomware simulation
├── cloud_pivot_aws.rc         ← AWS cloud pivot
└── linux_privesc.rc           ← Linux privesc chain
```

---

## Security & Legal

These playbooks are for **authorized security testing only** — penetration tests, red team engagements, and detection engineering exercises where you have explicit written permission to test.

Do not use against systems you do not own or have permission to test.

---

## License

[MIT](LICENSE) — free to use, modify, and contribute back.
