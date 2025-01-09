User
=========

A role for creating users, setting passwords, assigning sudo privileges, and adding SSH keys.

Requirements
------------

The role does not require additional dependencies except for standard Ansible modules. The following modules are necessary for all tasks: `ansible.builtin.user`, `ansible.posix.authorized_key` and `community.general.sudoers`.  

Role Variables
--------------
```yaml
users:
  - user_name: <имя пользователя>
    user_password: <пароль>
    user_sudo: <доступ к sudo (yes/no)>
    user_sudoers: <список команд sudo>
    user_ssh_key: <список публичных SSH-ключей>
```
`users`
A list of users to be managed by the role.

`user_name`
The name of the user to create or validate.

`user_password`
The password to assign to the user. If not provided, the user will be created with the  `default_user_password` from `defaults`.

`user_sudo`
Indicates whether the user should be added to the sudo group. Accepts `yes` or `no`.

`user_sudoers`
A list of specific commands the user can execute via sudo without requiring a password.

`user_ssh_key`
A list of public SSH keys to be added for the user.


Dependencies
------------

The role does not depend on any other roles.

Example Playbook
----------------

An example of using the role with variables passed:

```yaml
- hosts: all
  roles:
    - role: user
      vars:
        users:
          - user_name: "dev-user"
            user_password: $ANSIBLE_VAULT;
            user_sudo: "yes"
            user_sudoers:
            - /bin/systemctl stop systemd-journald
            - /bin/systemctl start systemd-journald
            user_ssh_key:
            - /root/.ssh/id_ed25519.pub
          - user_name: "prod-user"
            user_password: $ANSIBLE_VAULT;
            user_sudo: "yes"
            user_sudoers:
            - /bin/systemctl restart rsyslog
            - /bin/systemctl stop rsyslog
            user_ssh_key:
            - /root/.ssh/id_rsa.pub

```



License
-------

BSD

Author Information
------------------

Mikhail Merkushev
freeedomall@list.ru
