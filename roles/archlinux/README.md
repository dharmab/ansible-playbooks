This role is intended for automation of first-time setup of an Arch Linux development environment. It should not be used for day-to-day maintenance. **If you run this without first trialing it in a VM you are an idiot. If you run this without proper backups you are an idiot. If you use this playbook for regular maintenance of your Arch Linux installation you are an idiot.** Using this for regular updates violates [The Arch Way](https://wiki.archlinux.org/index.php/The_Arch_Way) and you're going to screw up your machine when manual intervention is required.

Wallpaper image credits: 
* Art copyright ZedEdge ([DeviantArt](http://zededge.deviantart.com/art/Korra-Mass-Effect-FSRX-492156216))
* Legend of Korra copyright Viacom International Inc
* Mass Effect copyright EA International (Studio and Publishing) Ltd

## Variables

* `normal_user` (string) - The username of the non-root user this role will create and configure
* `user_real_name` (string) - The non-root user's real name (used for git commits)
* `user_email` (string) - The non-root user's email address (used for git commits)
* `install_vmware` (boolean) - If true, VMware Workstation dependencies and configuration files will be installed. If false, these will not be installed. Workstation itself must be installed and and enabled manually (see usage notes)

## Usage Notes

Before running the playbook, perform a full upgrade and resolve any necessary manual interventions. This playbook must be run as root. Although I have tested the playbook and have found no destructive side effects, I cannot guarantee your system. Make sure your backups are current.

To run this role locally, create an inventory file named `localhost` with the following content

    [archlinux]
    localhost

Install Ansible from the official repositories:
```bash
pacman -S ansible
```

Install [Packer](https://aur.archlinux.org/packages/packer/) from the AUR.

Become the root user and run the playbook:
```bash
ansible-playbook -i localhost -c local --extra-vars "normal_user=john user_real_name='John Doe' user_email=john.doe@example.com" site.yml
```

You will have to set the non-root user's password and sudo privileges manually using `passwd` and `visudo`. Enabling sudo access for the `wheel` group should suffice, e.g. `%wheel ALL=(ALL) ALL`.

To install VMware Workstation, run the playbook with `install_vmware` set to true, then run the following:

```bash
sh <vmware installer file> --console --eulas-agreed --required
systemctl start vmware
systemctl enable vmware
```
