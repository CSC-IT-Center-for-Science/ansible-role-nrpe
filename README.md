ansible-role-nrpe
=========

Installs and configures NRPE or opsview-agent

 - Templates in a file that changes allowed_hosts of nrpe.cfg
 - Templates in a file that has custom nrpe/opsview checks

Requirements
------------

 - opsview-agent requires that the yum repo is installed before running this role
 - if a firewall is used then it should allow access to TCP port 5666 from nagios_allowed_hosts variable
 - custom checks are installed separately
  - If they are available in yum add them to the nrpe_extra_rpms set
  - By default this installs a few rpms from EPEL.


Role Variables
--------------

See defaults/main.yml for a complete listing.

These are the two primary settings:
<pre>
install_opsview: True
install_nrpe: False
</pre>

install_opsview assumes that the server's yum is configured to talk to a repository that has the opsview-agent rpm.

Other important ones:

<pre>
nagios_plugins:
  - { command: "name", path: "path/to/where/plugin/is/installed", arguments: "arguments to this check" }
opsview_plugins:

nagios_allowed_hosts: "127.0.0.1,10.1.1.1"
</pre>

extra rpms:
<pre>
nrpe_extra_rpms:
 - nagios-common
 - nagios-plugins-smtp
</pre>

Dependencies
------------

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: ansible-role-nrpe }

License
-------

MIT

Author Information
------------------
