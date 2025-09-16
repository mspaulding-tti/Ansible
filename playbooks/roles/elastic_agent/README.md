
# elastic_agent (Ansible Role) — v4.1

**Changes in v4.1**
- Skip install if Elastic Agent service is already **running** and `force_install: false` (one-time installer policy).
- Keep ability to **reinstall** by setting `force_install: true` (role will attempt uninstall then install).
- Inherits v4: x86_64/amd64-only, version sanitization, idempotent install, cleanup.

## Requirements
- Ansible 2.12+
- Linux targets (**x86_64 only**)
- Privilege escalation (`become: true`)

## Variables
- `version_source_url` (default: TAMUS version file)
- `fleet_url` (Fleet enrollment URL)
- `enrollment_token` (**required**)
- `agent_tags` (default: `TTI`)
- `force_install` (default: `false`)
- `work_dir` (default: `/tmp`)
- `version_override` (optional)

## Example
```yaml
- hosts: elastic_agents
  become: true
  roles:
    - role: elastic_agent
      vars:
        enrollment_token: "{{ vault_enrollment_token }}"
        # version_override: "8.19.2"
        # force_install: true
```
