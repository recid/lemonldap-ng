# lemonldap-ng

This tool based on ansible automates LemonLDAP-NG software installation.
 
LemonLDAP-NG is a modular WebSSO (Single Sign On) based on Apache::Session modules. 
It simplifies the build of a protected area with a few changes in the application. 
It manages both authentication and authorization and provides headers for accounting. 

## Installation

1. Clone the repository
```    
git clone https://github.com/recid/lemonldap-ng.git
```

2. Get the latest version of Ansible
```
git clone git://github.com/ansible/ansible.git --recursive
cd ansible
source hacking/env-setup
```

3. Get virtualenvwrapper
    See the following link : http://virtualenvwrapper.readthedocs.org/en/latest/install.html

4. Prepare ansible environment
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

## Running the playbook
```
ansible-playbook -i inventory all.yml
``` 
