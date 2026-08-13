# megaploit-community / playbooks

Community engagement playbooks for the [Megaploit C2](https://github.com/your-org/megaploit) framework.

Playbooks are plain `.rc` files — one Megaploit console command per line.  
Install them with a single command from the Megaploit console:

```
community install playbook ad-full-compromise
community install playbook ransomware-simulation
community install playbook cloud-pivot-aws
community install playbook linux-priv-esc-chain
```

Or load any `.rc` file directly:

```
resource ./playbooks/ad_full_compromise.rc
```

---

## Available Playbooks

| Name | File | Description |
|------|------|-------------|
| `ad-full-compromise` | `ad_full_compromise.rc` | Full AD compromise chain: foothold → DA via Kerberoast + DCSync |
| `ransomware-simulation` | `ransomware_sim.rc` | Ransomware simulation for detection engineering (no real encryption) |
| `cloud-pivot-aws` | `cloud_pivot_aws.rc` | AWS pivot: IMDSv1/v2 credential harvest → lateral movement via SSM |
| `linux-priv-esc-chain` | `linux_privesc.rc` | Linux privesc: SUID → sudo -l → cron → writable service chain |

---

## Playbook Format

`.rc` files are executed by `megaploit.core.resource_runner`.  
Syntax rules:

```rc
# This is a comment — ignored
# Blank lines are ignored

session 3                    # switch to session 3
shell whoami                 # run a shell command
kiwi logonpasswords          # call a built-in handler

# Variable interpolation — set at run time
setopt LHOST ${LHOST}
setopt PORT  ${PORT}
```

Built-in variables: `${LHOST}`, `${PORT}`, `${DATE}`, `${TIME}`, `${TIMESTAMP}`.

---

## Contributing

1. Fork this repo
2. Write your `.rc` playbook (follow the header comment format above)
3. Test it with `resource /path/to/playbook.rc` in Megaploit
4. Open a pull request — include what TTPs it covers and what it was tested against

Use `community share <path>` in Megaploit to auto-generate a PR-ready Markdown snippet.
