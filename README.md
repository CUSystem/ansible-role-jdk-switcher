ansible-role-jdk-switcher
=========

A simple Ansible role to swap out JDK strings in scripts and XML.

Requirements
------------

This is almost always only used on WebLogic installs since pack and unpack don't also respect the symbolic links.

The template script assumes the java is installed under /usr/java/<whatever> with the 'whatever' being replaced.

Example Playbook
----------------

[source,yaml]
----

- hosts: admin
  become: yes
  become_user: root
  vars:
    script_owner: oracle
    script_group: oinstall
    scrub_locations:
      - /home/oracle
      - /u01/app/oracle
      - /opt/oracle/12212
    scripts_home: "/tmp"
    jdk_version_string: "jdk1.8.0_101"
    #Can also submit one long string to search and replace
    #jdk_version_string: "jdk1.8.0_101 jdk1.8.0_111"
  roles:
    - role: staylorx.jdk-switcher

----

License
-------

BSD, MIT

