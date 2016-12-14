Ansible Role: Secure SSH
=========

Configure SSH to follow better security practices.

Requirements
------------

### SSH key logins.
By default, this role will prevent password logins in favor of ssh keys. Running the [login-user](https://github.com/dheles/ansible-role-login-user) role first will set this up for you. If you aren't going to use that role, you will want to either achieve a similar result by another means or override this role's behavior (by means of a mechanism not yet written).

Role Variables
--------------

This role sets sane OS-specific defaults and is not yet very configurable, so the variables are simple and few:

    ssh_service: ssh

The name of the service that provides SSH on your OS. Typically, ssh for Debian family and sshd of RedHat family. These two will be detected by the role. Override this variable to support other OSes, if necessary. Better yet, submit a pull request to fix it proper.

    ssh_config: "/etc/ssh/sshd_config"

Location of the system-wide (not per-user) SSH configuration file on your OS (see above).

Dependencies
------------

None, per se, but see "Requirements" above.

Example Playbook
----------------

    - name: secure SSH
      hosts: all
      become: true

      roles:
         - { role: secure-ssh }

License
-------

CC0

Author Information
------------------

Drew Heles
