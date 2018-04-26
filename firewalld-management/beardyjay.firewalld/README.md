beardyjay.firewalld
=========

Allows you to add firewall rules to systems running firewalld. 

Requirements
------------

Tested on RHEL 7 and CentOS 7 only. 

Ansible 1.5 or above 

Role Variables
--------------

The following variables are used to define a rule: 

    firewalld_rules: 
      name:
        port:
        protocol: 
        state: 
        zone: 
        permanent:

For example the default is to allow SSH on the public interface: 

    firewalld_rules: 
      ssh:
        port: 22
        protocol: tcp
        state: enabled
        zone: public
        permanent: true

Handlers
--------

These are the handlers that are defined in handlers/main.yml.

    restart firewalld

Example Playbook
----------------

    - hosts: server-name
      sudo: True
      roles:
        - beardyjay.firewalld
      vars:
        firewalld_rules:
          httpd:
            port: 80
            protocol: tcp
            state: enabled
            zone: public
            permanent: true
          mysqld:
            port: 3306
            protocol: tcp
            state: enabled
            zone: public
            permanent: true

License
-------

MIT

Author Information
------------------

