# GRIMM Solo Mining Guide
- Adapted from Raskul's guide
- With help from Freshminer and  Mikeyb

## Installation
- From [Releases](https://github.com/freenetcoder/grimm/releases/tag/10.1dev) download the following
  - grimm-wallet-cli
  - grimm-node
- Extract downloads into a folder called `grimm-mining`

## Setup
- Create SSL certificate & key in `grimm-mining` directory
  - `openssl req -newkey rsa:4096 -nodes -keyout stratum.key -x509 -days 365 -out stratum.crt
- Create a file called `stratum.api.keys` and add a alphanumeric string
  - Example: `Zmohq90bfgMvLB4gjL9NS5PeAJ7CReXO3G7aZ0aW`
  - You can add 1 string per line.  These are used at the `user` in your mining client
- Edit `grimm-wallet.cfg` file removing the `#` before `pass` and `node_addr`
  - `pass=abcdefghijklmnopqrstuvwxyz1234567890`
  - `node_addr=127.0.0.1:10000`
  - Leave the rest as is
- Initialize wallet by running this command in a terminal
  - `./grimm-wallet init`
  - Save the passphrase and address before continuing
- Export miner key by running this command in a terminal
  - `./grimm-wallet export_miner_key --subkey=1`
  - Take the key and put in the `grimm-node.cfg` file on the `key_mine=` line
- Export owner key by running this command in a terminal
  - `./grimm-wallet export_owner_key`
  - Take the key and put in the `grimm-node.cfg` file on the `key_owner=` line
- Get the `pass` in `grimm-wallet.cfg` and add it to the `pass=` line in `grimm-node.cfg`
- Add these entries to `grimm-node.cfg`
  - `port=10000`
  - `log_level=verbose`
  - `file_log_level=verbose`
  - `mining_threads=0`
  - `peer=67.205.185.92:8385,165.22.197.90:8385,134.209.157.140:8385,104.248.242.82:8385
  - `stratum_port=3333`
    - Make sure your firewall is allowing connections to this port if mining externally
  - `stratum_secrets_path=.`
- Start the node with the following command
  - `./grimm-node`
  - Leave this terminal open to keep the node running
- Wait for node to fully synchronize
- Open another terminal window in `grimm-mining` directory and run the command
  - `./grimm-wallet listen`
  - Leave this terminal open to keep the wallet listening
- Point your miner at the ip address of this device

## Config Examples
- `grimm-wallet.cfg`
```
pass=abcdefghijklmnopqrstuvwxyz1234567890
node_addr=127.0.0.1:10000
```

- `grimm-node.cfg`
```
port=10000
log_level=verbose
file_log_level=verbose
mining_threads=0
peer=67.205.185.92:8385,165.22.197.90:8385,134.209.157.140:8385,104.248.242.82:8385
stratum_port=3333
stratum_secrets_path=.
key_mine=export_miner_key string
key_owner=export_owner_key string
pass=abcdefghijklmnopqrstuvwxyz1234567890
```
