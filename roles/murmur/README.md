# Murmur (Mumble Server)
Supported OS: Debian 7.X x64

Provisions a server as a Murmur server for the Mumble VoIP program.

## Variables
`murmur_motd` (string) - Message displayed when users connect to the server.
`murmur_password` (string) - Password required to connect to the server. Set to empty string for no password requirement.
`murmur_superuser_password` - Password required to connect to the server as SuperUser.

## Usage Notes
After the playbook is complete, log into the server as SuperUser using the superuser password (defined with `murmur_superuser_password`) to configure the server.
