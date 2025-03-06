# Ansible Role: Grafana Dashboard Import

![Grafana Logo](https://raw.githubusercontent.com/grafana/grafana/main/public/img/grafana_icon.svg)

Ansible role for importing dashboards into Grafana:

## Description

This Ansible role is designed to automate the process of importing dashboards into Grafana.

- Dashboards should be located in the `dashboards` folder.
- Subfolders within the `dashboards` folder will be created as folders in Grafana.
- Dashboards located within these subfolders will be imported into their respective folders in Grafana.

**Important Notes**:

- Make sure to set `export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES` environment variable if running on macOS Catalina (10.15) or later to avoid issues with Ansible's forking behavior.
- When running the playbook, use the `--ask-become-pass` flag to provide the sudo password if necessary.

## Requirements

## Role Variables

- `env`: Specifies the environment (dev or prod). Set it to `prod` when deploying to production.

## Run Playbook

Using extra-var to call a defined mac user password "--ask-become-pass"

```bash
ansible-playbook -i hosts playbooks/grafana.yaml --extra-vars "env=dev" --ask-become-pass
```

## Example Playbook

Here's an example playbook using the role:

```yaml
- hosts: localhost
  gather_facts: false
  roles:
    - ansible-role-grafana
```
