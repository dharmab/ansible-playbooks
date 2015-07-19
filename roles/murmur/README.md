Provisions a server as a Murmur server for the Mumble VoIP program.

## Variables
* `murmur_motd` (string) - Message displayed when users connect to the server. A generic default is provided.
* `murmur_password` (string) - Password required to connect to the server. The default is no password requirement.
* `murmur_superuser_password` (string) - Password required to connect to the server as SuperUser.

## Usage Notes
After the playbook is complete, log into the server as SuperUser using the superuser password (defined with `murmur_superuser_password`) to configure the server.
