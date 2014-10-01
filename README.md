This repository contains my personal library of Ansible playbooks for CentOS 7.

Using Windows? A Vagrantfile and provisioning script are included to create a virtual machine to run Ansible Core. Install [Vagrant](http://www.vagrantup.com) and [VirtualBox](https://www.virtualbox.org/), navigate a command prompt to the directory containing the Vagrantfile, and type the following commands:

    vagrant up
    vagrant ssh
    cd ansible-playbooks

You can now run Ansible commands from within the VM while editing the playbook using your favorite Windows editor.

# Roles

## ArmA 3 Dedicated Server
Supported OS: CentOS 7.0 x64

Provisions a server as an ArmA 3 Dedicated server.

1. Edit `steam_credentials.json` with valid steam credentials. Do not use a Steam account that has purchases- create a new Steam account with no purchases for use here.
1. Create an inventory file and add the server to the `arma` group.
1. Copy `host_vars/arma_example` to `host_vars/<hostname>` and edit the variables accordingly. While host variables are normally considered a bad practice, they make sense for game servers where each host is a self-contained instance.
1. Run `ansible-playbook -i inventory -u <remote user> --extra-vars="@steam_credentials.json" site.yml`
1. The playbook will stop after installing SteamCMD and ask you to authorize the server with Steam Guard. Follow the instructions to verify the account and run the playbook again.
1. After the playbook is complete, log into the server manually.
1. Start a screen or tmux session.
1. Navigate to the ArmA 3 server directory with `cd /home/steam/arma3`.
1. Start the server with `sudo -u steam ./arma3server -name=server -config=server.cfg`
1. Detach from the screen or tmux session. You may now disconnect from the server.

## Murmur (Mumble Server)
Supported OS: Debian 7.X x64

Provisions a server as a Murmur server for the Mumble VoIP program.

1. Create an inventory file and add the server to the `murmur` group.
1. Copy `host_vars/murmur_example` to `host_vars/<hostname>` and edit the variables accordinly. While host variables are normally considered a bad practice, they make sense for Murmur servers where each host is a self-contained instance.
1. Run `ansible-playbook -i inventory -u <remote user> site.yml`
1. After the playbook is complete, log into the server as SuperUser using the superuser password from defined in the host_vars file.
