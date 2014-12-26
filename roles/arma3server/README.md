# ArmA 3 Dedicated Server
Supported OS: CentOS 7.0 x64

Provisions a server as an ArmA 3 Dedicated server.

## Variables
* `steam_user_name` (string) - A valid Steam username. Do not use a Steam account that has purchased content or is used for playing games. Create a new Steam account with no purchases for use with dedicated server software.
* `steam_user_password` (string) - The password to the Steam account defined by `steam_user_name`.
* `arma_server_hostname` (string) - The server name displayed in the in-game server browser.
* `arma_server_password` (string) - The server password required to connect to the server.
* `arma_server_admin_password` (string) - The password to obtain admin privileges while in-game.
* `arma_server_max_players` (int) - Maximum number of players the dedicated server will allow to connect.
`arma_server_vote_threshold` (decimal in range 0.01 - 1.00 inclusive) = Percentage of players required to pass a vote, e.g. to change missions or elect a server admin.
* `arma_server_enable_battleye` (int) - 0 to disable BattlEye anti-cheat, 1 to enable BattlEye anti-cheat. Reccomended setting is to disable for private servers with active moderation and enable otherwise.
* `arma_server_disable_voice` (int) - 0 to enable in-game voice chat, 1 to disable in-game voice chat. Reccomended setting is to disable if server is using a thiry-party voice chat solution (e.g. TeamSpeak) and enable otherwise.
* `arma_server_enable_persistent` (int) - 0 to disable persistent battlefield, 1 to enable persistent battlefield. When persistent battlefield is enabled, make missions that have either BASE or INSTANT respawn will continue to run when all players disconnect. This is opposed to the normal behavior, where the current mission ends if all players disconnect.
* `arma_server_voice_quality` (int in range 0-30 inclusive) - If in-game voice chat is enabled, this setting determines the audio quality. 0 is the lowest quality and 30 is the highest quality.

## Usage Notes
The playbook will stop after installing SteamCMD and ask you to authorize the server with Steam Guard. Follow the instructions to verify the account and run the playbook again.

You will need to use screen or tmux to daemonize the server process:
1. Start a screen or tmux session.
1. Navigate to the ArmA 3 server directory with `cd /home/steam/arma3`.
1. Start the server with `sudo -u steam ./arma3server -name=server -config=server.cfg`
1. Detach from the screen or tmux session. You may now disconnect from the server.
