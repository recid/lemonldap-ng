# LemonLDAP-NG

This tool based on ansible automates LemonLDAP-NG software installation.

LemonLDAP-NG is a modular WebSSO (Single Sign On) based on Apache::Session modules.
It simplifies the build of a protected area with a few changes in the application.
It manages both authentication and authorization and provides headers for accounting.

## Installation

* Clone the repository
```
git clone https://github.com/recid/lemonldap-ng.git
```

* Get the latest version of Ansible
```
git clone git://github.com/ansible/ansible.git --recursive
cd ansible
source hacking/env-setup
```

* Get virtualenvwrapper

See the following link : http://virtualenvwrapper.readthedocs.org/en/latest/install.html

* Prepare ansible environment
```
mkvirtualenv -p /usr/bin/python2 --no-site-packages lemonldap-ng
pip install paramiko PyYAML Jinja2 httplib2 six pyasn1 pycrypto python-keyczar
cat > ~/.virtualenvs/lemonldap-ng/bin/postactivate << EOF
#!/bin/bash
cd $(pwd)
source ansible/hacking/env-setup
EOF
workon lemonldap-ng
```

## Playbook Configuration

In the config.yml file, you can indicate
 - the web domain used and managed by LemonLDAP-NG,
 - the different URLs used by it
 - EPEL URLs
 - enable or not the packages upgrade

## Playbook Running
```
ansible-playbook -i inventory all.yml
```
