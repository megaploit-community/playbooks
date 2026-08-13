<div align="center">

<img src="https://raw.githubusercontent.com/megaploit-community/.github/main/profile/banner.png" width="100%" alt="megaploit-community">

# megaploit-community

**Open community for the [Megaploit C2](https://github.com/Josefifir/Megaploit) framework.**  
Engagement playbooks · BOF kits · GUI operator console · Post-exploitation modules · Detection content

[![Playbooks](https://img.shields.io/badge/playbooks-4-blue?style=flat-square)](https://github.com/megaploit-community/playbooks)
[![GUI](https://img.shields.io/badge/GUI-Qt6%20%2B%20QML-purple?style=flat-square)](https://github.com/megaploit-community/Megaploit-GUI)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](https://github.com/megaploit-community/playbooks/blob/main/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](https://github.com/megaploit-community/playbooks/blob/main/CONTRIBUTING.md)

</div>

---

## What is this?

This organisation hosts community-maintained content and tooling for the **Megaploit C2 framework** — a professional-grade open-source command-and-control platform with three independent agents (C/Windows, Go/cross-platform, Python/cross-platform), a custom WDM kernel driver, X25519 ECDH per-session crypto, and UEFI firmware implant capability.

---

## Repositories

| Repo | Description | Stack |
|------|-------------|-------|
| [Megaploit-GUI](https://github.com/megaploit-community/Megaploit-GUI) | Native Qt6/QML operator console — dark-themed, GPU-accelerated, single binary | C++ · Qt 6.11 · QML |
| [playbooks](https://github.com/megaploit-community/playbooks) | Engagement playbooks (`.rc` scripts) for common attack chains | RC scripts |

---

## Megaploit GUI

A native desktop operator console for Megaploit. Single binary, dark-themed, GPU-accelerated. Runs on **Windows x64** and **Linux x64**.

**Views:**
- 🖥️ **Sessions** — live session table with detail panel  
- 💻 **Console** — per-session terminal + quick-command palette  
- 📡 **Listeners** — listener cards + new-listener dialog  
- 🔧 **Payload Builder** — C agent compile-flag configurator  
- 🗂️ **Loot Browser** — loot file registry  
- 🔑 **Credentials** — credential store table  
- ⚙️ **Jobs** — background job monitor  
- 🌐 **Network Map** — canvas-drawn host graph  
- ⚙️ **Settings** — server config + engagement metadata  

```bash
# Build on Windows
build_win.bat

# Build on Linux
./build_linux.sh
```

→ **[Megaploit-GUI repo](https://github.com/megaploit-community/Megaploit-GUI)**

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

**Playbooks** — Have a script from a real engagement?  
Use `community share <playbook.rc>` in Megaploit to generate a PR-ready snippet, then open a pull request.

**GUI** — Qt6/QML/C++ improvements welcome — open a PR against [Megaploit-GUI](https://github.com/megaploit-community/Megaploit-GUI).

Read the [contribution guide](https://github.com/megaploit-community/playbooks/blob/main/CONTRIBUTING.md) for playbook format requirements and review criteria.

---

<div align="center">
<sub>For authorized security testing only. Use responsibly.</sub>
</div>
