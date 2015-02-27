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

# supervisor settings
lgf_supervisor_password: "PASSWORD"
lgf_supervisor_socket: "/tmp/supervisor.sock"

# settings for your app(s)
lgf_app:
  - server_name: "app"
    flask_app: "wsgi"
    proxy_host: "127.0.0.1"
    proxy_port: "80"
    gunicorn_port: "12345"
    app_dir: "/var/www/html/app"
    virtualenv_dir: "/var/www/html/app/env"
    # a media_dir will not run through wsgi and will prompt
    # lighttpd to spin up a server on the specified port.
    # set to "" if you don't need it
    media_dir: "/media"   # inside {{ app_dir }}
    python_3: false
    repo: "git@github.com:{user}/{repo-name}"
    ssh_keyfile: ""
    extra_files:
      - src: "app-settings-config.py"
        dest: "config.py"
  
  - ...

```

Notes:

- `lgf_app.server_name`: Used througout the configuration to refer to your app; for example log-files named _server-name.access.log_ will be created inside lighttpd's log directory, so don't use spaces in this name
- `lgf_app.flask_app`: The name of the main Flask app module
- `lgf_app.media_dir`: Directory inside the app-dir that will not be proxied through gunicorn, but directly served by lighttpd
- `lgf_app.ssh_keyfile`: A file with an SSH key that allows to clone a private GitHub repo
- `lgf_app.extra_files`: Files, treated as templates with "item.0" as lgf_app dict and "item.1" as extra_file dict, that will be copied into the app directory

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
