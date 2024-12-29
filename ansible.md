# Ansible
## installation

# connect to ec2 instance
ssh -i <pem file path> ubuntu@<public ip address>

sudo apt-get update
sudo apt-get install ansible

pip3 install ansible

# enter the following line in ~/.bashrc
export PATH=~/.local/bin:$PATH
source ~/.bashrc

## configuring the inventory

# open file /etc/ansible/hosts
# or
# create a new file in your project directory
> mkdir ansible-demo
> cd ansible-demo
> vim inventory.ini

# add the following section with ip addresses of managed nodes
# [hosts]
# 172.31.16.114

# get the list of managed nodes
> ansible-inventory -i inventory.ini --list

# check if ansible and ssh into nodes without password
> ansible hosts -i inventory.ini -m ping



## configure passwordless authentication for ssh

- execute these commands on controller



# generate ssh key pair
> ssh-keygen

# copy the contents of public key (one with .pub extension) from
# ~/.ssh directory



- execute these commands on managed nodes



# paste the public key of controller node into
# ~/.ssh/authorized_keys



## install apache using ansible

yaml
# playbook-demo.yaml

- name: playbook demo
  hosts: hosts
  become: true

  tasks:
    - name: install apache2
      apt:
        name: apache2
        state: present




# execute the playbook
> ansible-playbook -i inventory.ini playbook-demo.yaml


