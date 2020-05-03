# Bitwardenrs

[![Build Status](https://travis-ci.com/dmaes/ansible-role-bitwardenrs.svg?branch=master)](https://travis-ci.com/dmaes/ansible-role-bitwardenrs)

Builds, installs and configures [Bitwarden_RS](https://github.com/dani-garcia/bitwarden_rs) (without Docker).

Currently, only sqlite3 backend is supported.
Also, not all configuration can be done via role variables yet.

*Only tested on Debian 10*

## Requirements
* Requirements for the [unarchive](https://docs.ansible.com/ansible/latest/modules/unarchive_module.html)-module
* Requirements for the [package](https://docs.ansible.com/ansible/latest/modules/package_module.html)-module
* Systemd (optional)
* SQLite3

## Role Variables
```yaml
# Role settings
bitwardenrs_configure: yes # Do or do not configure bitwardenrs (must specify `bitwardenrs_domain` if set to `yes`)
bitwardenrs_domain: <domain> # must be specified if `bitwardenrs_configure` is set to `yes` (without `https://`)
bitwardenrs_systemd: yes # Do or do not setup systemd service
bitwardenrs_webvault: yes # Do or do not install webvault (https://github.com/dani-garcia/bw_web_builds)

# Installation settings
bitwardenrs_directory: /opt/bitwarden_rs # Where to install
bitwardenrs_version: 1.14.2 # Version to install
bitwardenrs_webvault_version: 2.13.2b # Webvault version to install

# Configuration settings (check Bitwarden_RS config file for more information)
bitwardenrs_admin_token: ''
bitwardenrs_admin_token_disabled: no
bitwardenrs_port: 8000
bitwardenrs_signup: yes
bitwardenrs_signup_domains: []
bitwardenrs_smtp: no
bitwardenrs_smtp_host: "{{ bitwardenrs_domain }}"
bitwardenrs_smtp_from: "bitwarden-rs@{{ bitwardenrs_domain }}"
bitwardenrs_smtp_from_name: Bitwarden_RS
bitwardenrs_smtp_port: 587
bitwardenrs_smtp_ssl: yes
bitwardenrs_smtp_username: ''
bitwardenrs_smtp_password: ''
```

## Example Playbook
```yaml
- hosts: servers
  vars:
    bitwardenrs_configure: no
  roles:
    - dmaes.bitwardenrs
```

## License
MIT
