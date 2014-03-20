Ansible Lighttpd
========

An Ansible Role that installs lighttpd 1.4.x on RHEL/CentOS 6.x.

Requirements
------------

Epel repo: 
Lighttpd is not supported from the official CentOS repositories, lets go ahead and add the EPEL repositories to CentOS.

:-) No worries, if not found, we do for you.

Role Variables
--------------

The port on which lighttpd should be listening. Useful if you have another service (like a reverse proxy) listening on port 80

    vars:
 	server_port: 80


Dependencies
------------

None

License
-------

GPL

Author Information
------------------
Ravi Bhure <ravibhure@gmail.com>

[GitHub project page](https://github.com/ravibhure/ansible-lighttpd)
