User management
=========

[![Build Status](https://travis-ci.org/ajsalminen/ansible-role-user_management.svg?branch=master)](https://travis-ci.org/ajsalminen/ansible-role-user_management)


This role manages user accounts and groups on a server.

Role Variables
--------------

`user_management_users:`
A dictionary of users that would typically be set in group_vars/all.
each entry is keyed by user name and has the following properties:

    real_name: The real name field for the account.
    public_key: Name of the public key file in the asset directory for the user.
    additional_public_key: A second public key for the user.
    old_public_key: A public key previously in use by this user, to be removed.

`user_management_active_users:`
A list of user accounts that should be active on
the server.

`user_management_removed_users:`
A list of user accounts that should be removed.

`user_management_active_admins:`
A  list of admin users.

`user_management_locked_users:`
List of user accounts that should be locked.

`user_management_admin_groups: adm,sudo`
A string of groups that every admin user should be added to.

    user_management_ssh_keys_path:
    "{{ PLAYBOOK_PRIVATE_ROLE_ASSETS_PATH}}/user_management/public_keys/"
The directory the role will look for the public keys in. The default value is
under your playbook dir in assets/private/roles/user_management/public_keys.

`user_management_server_groups: []`
 List of groups to create.

Example Playbook
----------------

Here is an example of using some of the role's features. In real use you'd want
to define the users separately so that you can redefine just the active ones for
each server.

    - hosts: servers
      roles:
        - role: ajsalminen.user_management
          user_management_users:
            snowden:
              real_name: Edward Snowden
              public_key: test_id_rsa.pub
          user_management_active_users:
            - snowden
          user_management_active_admins:
            - snowden

License
-------

MIT/Simplified BSD license

Author Information
------------------
Role created by Antti J. Salminen in 2014.
