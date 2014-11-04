lighttpd-gunicorn-flask
=========

An Ansible role to install lighttpd and gunicorn and to deploy your custom flask application from github.

Requirements
------------

None

Role Variables
--------------

```# The github repo containing the python source code
repo: "https://github.com/USER/REPO"

# lighttpd settings
server_name: "APP"
vhosts_dir: "/etc/lighttpd/vhosts.d"

# supervisor settings
supervisor_password: "PASSWORD"
supervisor_socket: "/tmp/supervisor.sock"

# python settigns
virtualenv_dir: "/var/www/html/venv_APP"
app_dir: "/var/www/html/APP"
media_dir: "uploads"
```

Dependencies
------------

None

Example Playbook
----------------
```
- hosts: webserver
  roles:
  - role: lighttpd
```

License
-------

GPLv2

Author Information
------------------

Sebastian Gumprich
https://www.zufallsheld.de
