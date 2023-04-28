ansible-openldap
===

# OpenLDAP

## Install

```bash
sudo apt update
sudo apt install python3 python3-dev python3-venv build-essential libldap2-dev libsasl2-dev

git clone https://github.com/haccht/ansible-openldap
cd ansible-openldap

python3 -m venv env
source env/bin/activate

pip install ansible python-ldap python-docker
ansible-playbook --extra-vars="ansible_python_interpreter=$(which python)" site.yml -t openldap
```

## Defalut Variables

```yaml
ldap_domain:  "example.com"
ldap_base_dn: "dc=example,dc=com"
ldap_bind_dn: "cn=admin,{{ ldap_base_dn }}"
ldap_admin_password: "admin"
ldap_organisation: "Example Org."
```


# SSSD, SSHD, PAM for LDAP authentication.

## Install

```bash
sudo apt update
sudo apt install python3 python3-dev python3-venv

git clone https://github.com/haccht/ansible-openldap
cd ansible-openldap

python3 -m venv env
source env/bin/activate

ansible-playbook --extra-vars="ansible_python_interpreter=$(which python)" site.yml -t ldap_pam
```

## Default Variables

```yaml
ldap_base_dn: "dc=example,dc=com"
ldap_bind_dn: "cn=admin,{{ ldap_base_dn }}"
ldap_admin_password: "admin"
ldap_user_search_filter:
ldap_group_search_filter:
ldap_user_search_base:
ldap_group_search_base:
ldap_access_filter_groups: []
ldap_access_unix_groups: []
ldap_access_filter_users: []
```
