# Ansible Role: Shadowsocks Server

An Ansible Role that installing Shadowsocks Server  on Linux

## Requirements

Debian 9/Ubuntu 18.04

## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

```yaml
ss_server_method: 'aes-256-cfb'
ss_server_password: '1234567890'
ss_server_ports:
  begin: 9000
  end: 9009
```

This configuration will create 10 shadowsocks instances with the same method and password, and listening on port from 9000 to 9009(exclude).

## Dependencies

None.

## Example Playbook

Clone the project to a directory named `ss-server`:

```shell
git clone git@github.com:devops-templates/ansible-roles-shadowsocks-server.git ss-server
```

Move `hosts.example` and `ss-server.yml` to the same parent directory of `ss-server`:

```yaml
---
- hosts: all
  remote_user: sysops
  become: yes
  # remote_user: user
  # become: yes
  # become_method: sudo
  roles:
    - role: 'ss-server'
      vars:
        ss_server_method: 'aes-256-cfb'
        ss_server_password: '1234567890'
        ss_server_ports:
          begin: 9000
          end: 9009
```

Then run the playbook, like this:

```shell
ansible-playbook -i hosts ss-server.yml
```

If use a SSH Key with custom name, run the playbook like this:

```shell
ansible-playbook -i hosts ss-server.yml  --become --key-file ~/.ssh/vps-ssh-key
```

## License

MIT / BSD

## Author Information

This role was created by [小碼哥](https://thisiswangle.com/)
