User
=========

Роль для создания пользователей, настройки паролей, назначения прав sudo и добавления SSH-ключей.

Requirements
------------

Роль не требует дополнительных зависимостей, за исключением стандартных модулей Ansible. Для работы всех задач необходимы модули `ansible.builtin.user`, `ansible.posix.authorized_key` и `community.general.sudoers`.  

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
Список пользователей для выполнения роли.

`user_name`
Имя пользователя, который будет создан или проверен.

`user_password`
Пароль, который будет установлен пользователю. Если не указан, пользователь будет создан с `default_user_password` из `defaults`.

`user_sudo`
Определяет, нужно ли добавлять пользователя в группу sudo. Принимает значения yes или no.

`user_sudoers`
Список команд, которые пользователь сможет выполнять через sudo без необходимости указывать пароль.

`user_ssh_key`
Список публичных SSH-ключей, которые будут добавлены для пользователя.


Dependencies
------------

Роль не зависит от других ролей.

Example Playbook
----------------

Примеры использования роли с переданными переменными:

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
