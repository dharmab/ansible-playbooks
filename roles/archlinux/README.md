This role is intended for automation of first-time setup of an Arch Linux development environment. It should not be used for day-to-day maintenance.

## Usage
Create an inventory file named `localhost` with the following content

    [archlinux]
    localhost

Become the root user and run the following:
```bash
pacman -Syu ansible
ansible-playbook -i localhost -c local --extra-vars "ansible_python_interpreter=/usr/bin/python2 normal_user=john user_real_name='John Doe' user_email=john.doe@example.com"
```

Where `normal_user` is the username of the non-root user that will be created, `user_real_name` is the real name used for git commits and `user_email` is the email address used for git commits.`
