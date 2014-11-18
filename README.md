ansible-lighttpd-gunicorn-flask
=========

An Ansible role to install lighttpd and gunicorn and to deploy your custom flask applications from github.

Requirements
------------

None

Role Variables
--------------

```
# lighttpd settings
lgf_vhosts_dir: "/etc/lighttpd/vhosts.d"

# supervisor settings
lgf_supervisor_password: "PASSWORD"
lgf_supervisor_socket: "/tmp/supervisor.sock"

lgf_app:
  - lgf_server_name: "APP1"
    lgf_virtualenv_dir: "/var/www/html/venv_APP1"
    lgf_app_dir: "/var/www/html/APP1"
    lgf_media_dir: "/media"
    lgf_gunicorn_port: "12345"
    lgf_host: "192.168.100.25"
    lgf_port: "80"
    lgf_repo: "https://github.com/USER/APP1"

  - lgf_server_name: "APP2"
    lgf_virtualenv_dir: "/var/www/html/venv_APP2"
    lgf_app_dir: "/var/www/html/APP2"
    lgf_media_dir: "/media"
    lgf_gunicorn_port: "12346"
    lgf_host: "192.168.100.25"
    lgf_port: "8080"
    lgf_repo: "https://github.com/USER/APP2"

```

Dependencies
------------

None

Example Playbook
----------------
```
- hosts: webserver
  roles:
  - role: ansible-lighttpd-gunicorn-flask
```

License
-------

GPLv2

Author Information
------------------

Sebastian Gumprich
https://www.zufallsheld.de
