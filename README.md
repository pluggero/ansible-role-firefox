# Ansible Role: Firefox

[![CI](https://github.com/pluggero/ansible-role-firefox/actions/workflows/ci.yml/badge.svg)](https://github.com/pluggero/ansible-role-firefox/actions/workflows/ci.yml) [![Ansible Galaxy downloads](https://img.shields.io/ansible/role/d/pluggero/firefox?label=Galaxy%20downloads&logo=ansible&color=%23096598)](https://galaxy.ansible.com/ui/standalone/roles/pluggero/firefox)

An Ansible Role that installs a basic configuration of Firefox.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
firefox_version: "x.x"
```

The version of Firefox to install can be defined in the variable `firefox_version`.

```yaml
firefox_install_method: "dynamic"
```

The method used to install Firefox can be defined in the variable `firefox_install_method`.
The following methods are available:

- `source`: Installs Firefox from source
- `package`: Installs Firefox from the package manager of the distribution
  - **NOTE**: This method installs the latest version available in the package manager and not the version defined in `firefox_version`.
- `dynamic`: Installs Firefox from package manager if available in the correct version, otherwise installs from source

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - pluggero.firefox
```

## License

MIT / BSD

## Author Information

This role was created in 2025 by Robin Plugge.
