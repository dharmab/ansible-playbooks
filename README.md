This repository used to be my personal library of Ansible playbooks for CentOS 7, Debian and Arch Linux. It's mostly inactive now. See these repositories for more current work:

- https://github.com/dharmab/ansible-archlinux
- https://github.com/dharmab/ansible-annex
- https://github.com/dharmab/homelab

Using Windows? A Vagrantfile and provisioning script are included to create a virtual machine to run Ansible Core. Install [Vagrant](http://www.vagrantup.com) and [VirtualBox](https://www.virtualbox.org/), navigate a command prompt to the directory containing the Vagrantfile, and type the following commands:

    vagrant up
    vagrant ssh
    cd ansible-playbooks

You can now run Ansible commands from within the VM while editing the playbook using your favorite Windows editor.
