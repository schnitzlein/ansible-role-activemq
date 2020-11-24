# Ansible Role: ActiveMQ

An Ansible role that installs [ActiveMQ](http://activemq.apache.org/) on:

* Centos/RHEL 7.x
* Ubuntu Xenial
* Ubuntu Bionic

## Role Variables

Available variables are listed below, along with default values:

What version to install:
```
activemq_version: 5.16.0
```

Where to install to:
```
activemq_install_root: /opt
```

User\group to install as:
```
activemq_user: ubuntu
```

Whether to create user if not present:
```
activemq_create_user: yes
```

## Dependencies

* None
  
## Example Playbook

    - hosts: webservers
      roles:
        - { role: Islandora-Devops.activemq }
        
## HowTo run this thingy?
be in a fresh project directory and installed ansible.
create a directory called roles.
git clone <this-repo> to roles/activemq
create this file below as playbook.yml
  
```
---
- name: Web01
  hosts: all
  become: yes
  gather_facts: False
  pre_tasks:
    - name: Install python for Ansible
      raw: test -e /usr/bin/python || (apt -y update && apt install -y python-minimal)
      changed_when: False
    - setup: # aka gather_facts

  roles:
    #- base
    #- docker
    - activemq
```
create an inventory file with localhost or with remote hosts (need ssh keys or passwd)
run this with: ansible-playbook playbook.yml
with -i fetch custom inventory non default.

## License

MIT
