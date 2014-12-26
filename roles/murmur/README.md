## Murmur (Mumble Server)
Supported OS: Debian 7.X x64

Provisions a server as a Murmur server for the Mumble VoIP program.

1. Create an inventory file and add the server to the `murmur` group.
1. Copy `host_vars/murmur_example` to `host_vars/<hostname>` and edit the variables accordinly. While host variables are normally considered a bad practice, they make sense for Murmur servers where each host is a self-contained instance.
1. Run `ansible-playbook -i inventory -u <remote user> site.yml`
1. After the playbook is complete, log into the server as SuperUser using the superuser password from defined in the host_vars file.
