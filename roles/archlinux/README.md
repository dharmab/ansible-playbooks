This role is intended for automation of first-time setup of an Arch Linux development environment. It should not be used for day-to-day maintenance. **If you run this without first trialing it in a VM you are an idiot. If you run this without proper backups you are an idiot. If you use this playbook for regular maintenance of your Arch Linux installation you are an idiot.** Using this for regular updates violates [The Arch Way](https://wiki.archlinux.org/index.php/The_Arch_Way) and you're going to screw up your machine when manual intervention is required.

Wallpaper image credits: 
* Art copyright ZedEdge ([DeviantArt](http://zededge.deviantart.com/art/Korra-Mass-Effect-FSRX-492156216))
* Legend of Korra copyright Viacom International Inc
* Mass Effect copyright EA International (Studio and Publishing) Ltd

## Usage
Create an inventory file named `localhost` with the following content

    [archlinux]
    localhost

Become the root user and run the following:
```bash
pacman -Syu ansible
ansible-playbook -i localhost -c local --extra-vars "ansible_python_interpreter=/usr/bin/python2 normal_user=john user_real_name='John Doe' user_email=john.doe@example.com" site.yml
```

Where `normal_user` is the username of the non-root user that will be created, `user_real_name` is the real name used for git commits and `user_email` is the email address used for git commits.` You will have to set the non-root user's password and sudo privileges manually.
