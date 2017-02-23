# tumbumer.sshd

Manage openssh-server configuration.

## Requirements

None.

## Role Variables

var | default | choices | description
---|---|---|---
tumbumer_sshd_host_key_action | | create, update | Action for ssh host key
tumbumer_sshd_host_files_path | | | **Required if `tumbumer_sshd_host_key_action` is set.** Path on the localhost for keeping host ssh private and public keyfiles
tumbumer_sshd_address | `{{ ansible_default_ipv4.address }}` | | Sshd ipv4 address
tumbumer_sshd_port | 22 | | Sshd ipv4 port

## Dependencies

None.

## Example Playbook

```yaml
---
- hosts: all
  vars:
  - tumbumer_sshd_host_key_action: update
  - tumbumer_sshd_host_files_path: ./host_files
  - tumbumer_sshd_address: "{{ ansible_default_ipv4.address }}"
  - tumbumer_sshd_port: 22
  roles:
  - tumbumer.sshd
```

## License

Apache-2.0

## Author Information

Denis Dvoretskov aka tumbumer <denis@tumbum.com>
