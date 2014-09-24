This repository contains my personal library of Ansible playbooks for CentOS 7.

# Roles

## ArmA 3 Dedicated Server
This role provisions a server as an ArmA 3 Dedicated server.

1. Edit `steam_credentials.json` with valid steam credentials. Do not use a Steam account that has purchases- create a new Steam account with no purchases for use here.
1. Create an inventory file and add the server to the `arma3` group.
1. Copy `host_vars/arma3_example` to `host_vars/<hostname>` and edit the variables accordingly. While host variables are normally considered a bad practice, they make sense for game servers where each host is a self-contained instance.
1. Run `ansible-playbook -i inventory -u root --extra-vars="@steam_credentials.json" site.yml`
1. The playbook will stop after installing SteamCMD and ask you to authorize the server with Steam Guard. Follow the instructions to verify the account and run the playbook again.
1. After the playbook is complete, log into the server manually.
1. Start a screen or tmux session.
1. Navigate to the ArmA 3 server directory with `cd /home/steam/arma3`.
1. Start the server with `sudo -u steam ./arma3server -name=server -config=server.cfg`
1. Detach from the screen or tmux session. You may now disconnect from the server.

