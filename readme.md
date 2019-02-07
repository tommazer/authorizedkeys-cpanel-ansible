# authorized_keys mass updater for WHM/cPanel

When you have access to cPanel account via SSH key you can update easy.

## Usage

Install Ansible on OSX:
https://hvops.com/articles/ansible-mac-osx/

Clone this project to your Mac.

Edit files/authorized_keys with your new authorized_keys files.

Get WHM API token with list-accounts rights:
https://documentation.cpanel.net/display/64Docs/Manage+API+Tokens

Run command and replace vars:
ansible-playbook main.yml --extra-vars="whmhostname=#WHMHOSTNAME# whmusername=#WHMUSER# whmtoken=#APITOKEN#"

Example:
ansible-playbook main.yml --extra-vars="whmhostname=s1108.myfasthosting.com whmusername=reseller1 whmtoken=BXXXV5QW2XXX82VX5NLY5XXXIL9ASGW