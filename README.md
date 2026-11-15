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

```yaml
firefox_policies_dir: "/etc/firefox/policies"
```

System-wide [enterprise policies](https://mozilla.github.io/policy-templates/) for all users. Check them in Firefox at `about:policies`.

```yaml
firefox_extensions:
  - id: "uBlock0@raymondhill.net"
    mode: "force_installed" # normal_installed | allowed | blocked
    url: "https://addons.mozilla.org/firefox/downloads/latest/ublock-origin/latest.xpi"
firefox_extensions_lockdown: false
```

Extensions to manage. If `firefox_extensions_lockdown` is `true`, all other extensions are blocked.

```yaml
firefox_certificates:
  - name: "corp-root-ca"
    content: "MIIDdzCCAl+gAwIBAgIE..."
firefox_certificates_dir: "/etc/firefox/certificates"
```

Trusted certificates. `content` is the base64-encoded DER certificate (`openssl x509 -in ca.pem -outform DER | base64 -w0`). Unlisted `*.pem` files in `firefox_certificates_dir` are removed.

```yaml
firefox_managed_bookmarks_folder: "Managed bookmarks"
firefox_managed_bookmarks:
  - name: "Wiki"
    url: "https://wiki.example.com"
  - name: "Tools"
    children:
      - name: "Grafana"
        url: "https://grafana.example.com"
firefox_bookmarks_toolbar_display: "always" # never | newtab | "" (unmanaged)
```

Read-only bookmarks folder on the bookmarks toolbar. Users' own bookmarks are kept.

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
