# ansible-playbook

Ansible Playbook for an OpenLDAP server and client on CentOS

## Installation

- Clone the repository, replace <institution> with the actual name of your institution

        git clone  https://github.com/ubuntunet/ansible-playbook_LDAPS.git
        cd ansible-playbook_LDAPS

### Inventory File

- Create the inventory file for your institution, for more information: http://docs.ansible.com/ansible/intro_inventory.html

        cp inventories/template inventories/<institution>

Open the inventory file with your favorite editor and change the ansible_host and ansible_user to your server environment. Don't forget to again replace <institution>.

### Variables File

- Create the variables file for your institution, more information: http://docs.ansible.com/ansible/playbooks_variables.html

        cp group_vars/template group_vars/<institution>

Open the variable files in your favorite editor and adapt the values to your setup.


### Secrets File

Some values - passwords, credentials - are sensitive and should never be submitted to the Github repository. They are therefore stored in a file called secrets.yml, which is being ignored by Github.

- Create the secrets.yml file

        cp group_vars/secrets.yml.example group_vars/secrets.yml

- Open the secrets.yml file and add the sensitive values.<br>There are many ways to create random passwords/passphrases/salt, I prefer to use openssl for this task. You can replace 12 with a higher number for longer strings.

        openssl rand -base64 12

### Run the playbook

- As follows.
```
        ansible-playbook -i inventories/<institution> ldap_server.yml
        ansible-playbook -i inventories/<institution> ldap_client.yml
```

### Open Ports on Firewall

- The following ports need to be in order for LDAP/S to work properly:
```
TCP 636
```

## TODO

Some explanations are missing. I will fix it later.
