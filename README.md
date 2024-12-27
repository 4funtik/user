Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

users:
- user_name:
  user_password:
  user_sudo:
  user_sudoers:
  user_ssh_key:

users - список пользователей для выполнения роли

user_name - имя пользователя для проверки и создания

user_password - пароль, который будет присвоен пользователю

user_sudo - добавление пользователя в группу sudo

user_sudoers - команды, которые требуют повышения привелегий и  пользователь сможет выполнять без использования sudo

user_ssh_key - публичные ssh-ключи, которые будут добавлены для пользователя


A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
