mmartinello.msmtp
=================

This Ansible role install and configures the **msmtp** service on Debian and
CentOS based systems.

Requirements
------------

This role works on Debian and CentOS based systems, but it's tested on the
following systems:
* Debian 10 Buster
* CentOS 8

Role Variables
--------------

This role has 3 main variables:
* `msmtp_defaults`: msmtp default settings
* `msmtp_accounts`: a list of accounts, each with its own configuration
* `msmtp_default_account`: the name of the default account

Each account supports the following parameters:

| Parameter | Description                                          | Required |
| ----------| ---------------------------------------------------- | -------- |
| comment   | A comment string for this account                    | NO       |
| name      | The account name                                     | YES      |
| host      | The SMTP hostname                                    | YES      |
| port      | The SMTP port (default `25`)                         | NO       |
| from      | The sender e-mail address (default: `account.user`)  | NO       |
| user      | The SMTP login user                                  | YES      |
| password  | The SMTP login password                              | YES      |

Please see `defaults/main.yml` for details.

**NOTE:** these settings are saved into a `/etc/msmtprc`file which is the
msmtp system-wide configuration file, so that every system user uses it.
I know this could not be the more secure configuration but it suits the most
cases. Please don't use sensitive accounts (a dedicated SMTP account is
reccomended).

**TODO:** this role does not support user-wide configuration yet.

Dependencies
------------

This role has no dependencies.

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: mmartinello.msmtp

License
-------

MIT License

Author Information
------------------

Mattia Martinello
