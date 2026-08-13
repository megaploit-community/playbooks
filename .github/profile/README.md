<div align="center">

<img src="https://raw.githubusercontent.com/megaploit-community/.github/main/profile/banner.png" width="100%" alt="megaploit-community">

# megaploit-community

**Open community for the [Megaploit C2](https://github.com/Josefifir/Megaploit) framework.**  
Engagement playbooks · BOF kits · Post-exploitation modules · Detection content

[![Playbooks](https://img.shields.io/badge/playbooks-4-blue?style=flat-square)](https://github.com/megaploit-community/playbooks)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](https://github.com/megaploit-community/playbooks/blob/main/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](https://github.com/megaploit-community/playbooks/blob/main/CONTRIBUTING.md)

</div>

---

## What is this?

This organisation hosts community-maintained content for the **Megaploit C2 framework** — a professional-grade open-source command-and-control platform.

Everything here can be installed from the Megaploit console in one command:

```
community install playbook <name>
community install bof <name>
community refresh
```

---

## Repositories

| Repo | Description |
|------|-------------|
| [playbooks](https://github.com/megaploit-community/playbooks) | Engagement playbooks (`.rc` scripts) for common attack chains |

---

## Quick Start

```
# From the Megaploit console
community list
community search active-directory
community install playbook ad-full-compromise
resource community/playbooks/ad-full-compromise.rc
```

---

## Contributing

Have a playbook from a real engagement?  
Use `community share <playbook.rc>` in Megaploit to generate a PR-ready snippet, then open a pull request.

Read the [contribution guide](https://github.com/megaploit-community/playbooks/blob/main/CONTRIBUTING.md) for format requirements and review criteria.

---

<div align="center">
<sub>For authorized security testing only. Use responsibly.</sub>
</div>
