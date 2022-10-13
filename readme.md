# authorized_keys mass updater for WHM/cPanel

When you have access to cPanel account via SSH key you can update easy.

## Usage

Install Ansible on OSX:
https://hvops.com/articles/ansible-mac-osx/

Clone this project to your Mac:  
```
git clone https://github.com/tommazer/authorizedkeys-cpanel-ansible.git
```

The file ``` tasks/cpanel-tasks.yml ``` contain the tasks run in the cPanel account. Currently there are two demo keys added to the authorized_keys file. You can add more keys by adding to the list:  
```
- name: "Add public key"
  authorized_key:
    user: "{{ ansible_user }}"
    state: present
    key: "{{ item }}"
  with_items:
    - "ssh-rsa AAAAXXXX....XXXXXX"
    - "ssh-rsa BBBBXXXX....XXXXXX"
```

Get WHM API token with:  
- Initial Privileges
- Account Information

https://documentation.cpanel.net/display/64Docs/Manage+API+Tokens

Run command and replace vars:  
```
ansible-playbook main.yml --extra-vars="whmhostname=#WHMHOSTNAME# whmusername=#WHMUSER# whmtoken=#APITOKEN#"
```

Example:  
```
ansible-playbook main.yml --extra-vars="whmhostname=s1108.myfasthosting.com whmusername=reseller1 whmtoken=BXXXV5QW2XXX82VX5NLY5XXXIL9ASGW
```