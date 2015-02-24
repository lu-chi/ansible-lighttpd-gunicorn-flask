ansible-lighttpd-gunicorn-flask
=========

An Ansible role to install lighttpd and gunicorn and to deploy your custom flask applications from GitHub.
If your repo is private:
- Create a new SSH key - without setting a password - into a local file using `ssh-keygen`
- Add this key to your repo's "Deployment Keys" on GitHub
- Specify the path to this file in `gf_app.ssh_keyfile`

Requirements
------------

None

Role Variables
--------------

```
# lighttpd settings
lgf_vhosts_dir: "/etc/lighttpd/vhosts.d"

# supervisor settings (not currently used on Debian)
lgf_supervisor_password: "PASSWORD"
lgf_supervisor_socket: "/tmp/supervisor.sock"

# settings for your app(s)
lgf_app:
  - server_name: "app"
    flask_app: "wsgi"
    host: "127.0.0.1"
    port: "80"
    gunicorn_port: "12345"
    app_dir: "/var/www/html/app"
    virtualenv_dir: "/var/www/html/app/env"
    media_dir: "/media"   # inside {{ app_dir }}
    python_3: false
    repo: "git@github.com:{user}/{repo-name}"
    ssh_keyfile: ""
    extra_files:
      - src: "app-settings-config.py"
        dest: "config.py"
  
  - ...

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
