# Playbook Catalog

Full searchable index of all community playbooks.  
Install any playbook with: `community install playbook <name>`

---

## Active Directory / Windows

### `ad-full-compromise`
**File:** [`ad_full_compromise.rc`](ad_full_compromise.rc)  
**Author:** megaploit-community  
**Version:** 1.1  
**Platform:** Windows / Active Directory  
**Tested on:** Windows 10 21H2, Server 2019, Server 2022  

**Description:**  
Full Active Directory compromise chain from an unprivileged domain user foothold to Domain Admin. Covers UAC bypass, LSASS/SAM/DPAPI credential harvest, Kerberoasting, lateral movement via WinRM, DCSync, persistence via scheduled task and WMI, and evidence suppression.

**Phases:** Awareness → Privesc → Cred harvest → Kerberoast → Lateral move → DCSync → Persistence → Evidence suppression

**MITRE ATT&CK:**
- T1033 · T1082 · T1016 · T1087.002
- T1548.002 UAC bypass
- T1003.001 LSASS · T1003.002 SAM · T1003.006 DCSync
- T1558.003 Kerberoasting
- T1550.002 Pass-the-Hash
- T1021.006 WinRM
- T1053.005 Scheduled Task · T1546.003 WMI
- T1070.001 Log wipe · T1070.004 File delete · T1099 Timestomp

**Install:**
```
community install playbook ad-full-compromise
```

---

### `ransomware-simulation`
**File:** [`ransomware_sim.rc`](ransomware_sim.rc)  
**Author:** megaploit-community  
**Version:** 1.1  
**Platform:** Windows  
**Tested on:** Windows 10 21H2, Server 2019  

**Description:**  
Purple team ransomware simulation for detection engineering. No files are encrypted. Exercises every TTP a real ransomware operator uses — AV disable, file discovery, credential theft, shadow copy deletion, event log clearing — so defender detection coverage can be validated. All simulation artefacts are cleaned up automatically.

**Phases:** Disable defenses → Discovery → Cred access → Simulate encryption → VSS delete → Log clear → Cleanup

**MITRE ATT&CK:**
- T1562.001 Disable AV · T1562.002 Disable logging
- T1083 File discovery · T1082 Sysinfo
- T1003.001 LSASS · T1003.002 SAM
- T1486 Data encrypted for impact **[SIMULATED]**
- T1490 Inhibit system recovery (VSS)
- T1070.001 Event log clearing · T1070.004 File deletion

**⚠ WARNING:** Shadow copy deletion is real. Run in lab environments only.

**Install:**
```
community install playbook ransomware-simulation
```

---

## Cloud

### `cloud-pivot-aws`
**File:** [`cloud_pivot_aws.rc`](cloud_pivot_aws.rc)  
**Author:** megaploit-community  
**Version:** 1.1  
**Platform:** Linux (EC2), AWS  
**Tested on:** Amazon Linux 2, Ubuntu 22.04 on EC2  

**Description:**  
AWS lateral movement playbook. Starting from a shell on an EC2 instance with an attached IAM role, harvests credentials via IMDSv1 and IMDSv2, enumerates the AWS environment (IAM users, roles, EC2 instances, S3 buckets), pivots to other instances via SSM, and checks for IAM privilege escalation paths.

**Phases:** IMDSv1 harvest → IMDSv2 harvest → User-data scrape → Env enum → IAM discovery → S3 loot → SSM lateral move → Privesc check

**MITRE ATT&CK:**
- T1552.005 Cloud Instance Metadata API
- T1078.004 Cloud Accounts
- T1087.004 Cloud Account Discovery
- T1530 Data from Cloud Storage
- T1021.007 Cloud Services (SSM)
- T1619 Cloud Storage Object Discovery
- T1580 Cloud Infrastructure Discovery

**Prerequisites:** Session on EC2 with an attached IAM role. `aws` CLI available on the host.

**Install:**
```
community install playbook cloud-pivot-aws
```

---

## Linux

### `linux-priv-esc-chain`
**File:** [`linux_privesc.rc`](linux_privesc.rc)  
**Author:** megaploit-community  
**Version:** 1.1  
**Platform:** Linux  
**Tested on:** Ubuntu 20.04/22.04, Debian 11, CentOS 7/8, Amazon Linux 2  

**Description:**  
Systematic Linux privilege escalation enumeration chain. Checks 10 independent attack surfaces in order of likelihood and impact — SUID/SGID abuse, sudo misconfiguration, cron hijack, writable systemd units, PATH hijacking, LD_PRELOAD, credentials in files, writable /etc/passwd, Docker/LXC escape, and kernel exploit surface.

**Phases (10):** Awareness → SUID/SGID → sudo → Cron → Systemd → PATH/LD_PRELOAD → Creds in files → /etc/passwd → Container escape → Kernel → Harvest

**MITRE ATT&CK:**
- T1548.001 SUID/SGID · T1548.003 Sudo
- T1053.003 Cron
- T1574.006 Dynamic Linker Hijack · T1574.007 PATH Interception
- T1543.002 Systemd Service
- T1552.001 Creds in Files · T1552.004 Private Keys
- T1087.001 Local Account Discovery
- T1611 Container Escape (Docker/LXC)

**Install:**
```
community install playbook linux-priv-esc-chain
```

---

## Tags Index

| Tag | Playbooks |
|-----|-----------|
| `active-directory` | ad-full-compromise |
| `kerberos` | ad-full-compromise |
| `credential-access` | ad-full-compromise, ransomware-simulation |
| `lateral-movement` | ad-full-compromise, cloud-pivot-aws |
| `persistence` | ad-full-compromise |
| `defense-evasion` | ad-full-compromise, ransomware-simulation |
| `detection-engineering` | ransomware-simulation |
| `simulation` | ransomware-simulation |
| `cloud` | cloud-pivot-aws |
| `aws` | cloud-pivot-aws |
| `linux` | linux-priv-esc-chain |
| `privilege-escalation` | linux-priv-esc-chain, ad-full-compromise |
| `container-escape` | linux-priv-esc-chain |

---

## Contributing a playbook

See [CONTRIBUTING.md](CONTRIBUTING.md) — copy [PLAYBOOK_TEMPLATE.rc](PLAYBOOK_TEMPLATE.rc) to get started.
