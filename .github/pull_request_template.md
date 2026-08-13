---
name: Pull Request
about: Submit a new playbook or fix an existing one
---

## Summary

<!-- One sentence: what does this PR add or fix? -->

## Type

- [ ] New playbook
- [ ] Fix / improvement to existing playbook
- [ ] Documentation update
- [ ] Template / tooling update

## Playbook checklist (for new playbooks)

- [ ] Header block complete: Name, Version, Author, Tested on, Description, MITRE ATT&CK, Variables, Usage, Phases
- [ ] Every phase tagged with at least one MITRE ATT&CK technique ID
- [ ] All variables documented in header and used with `${VAR_NAME}` syntax
- [ ] No hardcoded IPs, passwords, domain names, or hostnames
- [ ] Tested successfully — "Tested on" field specifies exact OS + version
- [ ] Destructive operations (VSS delete, disk wipe, etc.) flagged with `# WARNING`
- [ ] Simulation artefacts cleaned up at end of playbook
- [ ] File name: `snake_case.rc`
- [ ] Added entry to `CATALOG.md`
- [ ] Read [CONTRIBUTING.md](CONTRIBUTING.md)

## Testing evidence

<!-- Describe how you tested this playbook. What environment? What output confirmed it worked? -->

## Related issues

<!-- Closes #XX -->
