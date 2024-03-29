 
Grimm Node User Guide
====================

General
------------------------


Grimm Node is an essential part of the Grimm blockchain and is responsible for validating transactions and blocks. It runs on all platforms: Linux, Windows and Mac 

Grimm Node can be run in either Mining or Validating mode. 

Mining mode
------------------------

Grimm Node supports two options for mining Grimm:


1. Using Internal Miner

    Grimm Node has built in GPU and CPU miners. To start the node with internal miner, specify miner type using `miner_type` parameter. Built in GPU mining is only supported on Linux and Windows platforms.

2. Using External Miner via Statum Server API

    Grimm Node provides built in support for Startum API allowing to connect multiple external mining clients to a single node.  To start the node with stratum server use `stratum_port` and `stratum_secrets_path` parameters. Stratum clients can be run together with the Internal Miner

Mining keys management

        In order for the mining node to be able to attribute mining rewards to your wallet, it needs a special secret *mining key*. The mining key is derived from the primary secret key by running `export_miner_key` command with --subkey=<node id> parameter in the [Grimm CLI Wallet](https://github.com/freenetcoder/Manifesto/blob/master/wallet_cli_commands.md). You can generate a multiple separate mining keys for different mining nodes.

        Optionally, in order to allow each mining node to be able to see all rewards mined by all your mining nodes Grimm provides an additional option called `owner_key`. Owner key is a secret view key, it can not be used to spend coins, just to identify your mining rewards regardless of which node was used to mine it. Owner key is derived from primary secret key as well using the same `key_export` command, but without additional parameters.

        Both keys are protected using Wallet Password, which should also be provided





Validating mode
------------------------

By default (without `--miner_type` flag) Grimm Node is run in validating mode, meaning that mining is disabled. Validating nodes are still very important for the overall health and safety of the network since they:

1. Help in propagating transactions and blocks through the network 
2. Relay SBBS messages to enable Wallet to Wallet communication.
3. Serve as Dandelion Stem relays to improve P2P level security

If possible, always prefer running a local node either with or without mining!





Node Settings
------------------------

Grimm Node allows to provide the settings via command line or using a configuration file called grimm-node.cfg and located in the same folder as Grimm Node binary. 

Command line parameters override configuration file settings

   The configuration file is loaded automatically and sets all parameters that were not provided via command line. To reload configuration file after a change you should manually restart Grimm Node
```    
+-------------------------+----------------------------------------------------------------------------------------------------------+
|**Parameter**            | **Description & Example**                                                                                |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --port                  | Port to start the server on                                                                              |
|                         |                                                                                                          |
|                         |                                                                                  |
|                         |                                                                                                          |
|                         |    port=10000                                                                                            |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --log_level             | Log level [info|debug|verbose]                                                                           |
|                         |                                                                                                          |
|                         |                                                                                   |
|                         |                                                                                                          |
|                         |    log_level=info                                                                                        |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --file_log_level        | File log level [info|debug|verbose]                                                                      |
|                         |                                                                                                          |
|                         |                                                                                    |
|                         |                                                                                                          |
|                         |    file_log_level=info                                                                                   |
+-------------------------+----------------------------------------------------------------------------------------------------------+




+-------------------------+----------------------------------------------------------------------------------------------------------+
|**Parameter**            | **Description & Example**                                                                                |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --storage               | Path to node database file (defaults to node.db in the same folder)                                      |
|                         |                                                                                                          |
|                         |                                                                                   |
|                         |                                                                                                          |
|                         |    storage=node.db                                                                                       |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --history_dir           | Path to folder where compressed (cut-through) history files are stored. Defaults to same folder.         |
|                         |                                                                                                          |
|                         |                                                                                   |
|                         |                                                                                                          |
|                         |    history_dir=.                                                                                         |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --temp_dir              | Path to temp folder for compressed (cut-through) history files. Must be on the same volume as history_dir|
|                         |                                                                                                          |
|                         |                                                                                  |
|                         |                                                                                                          |
|                         |    temp_dir=.                                                                                            |
+-------------------------+----------------------------------------------------------------------------------------------------------+
```
Using CPU mining is not recommended

   Grimm uses Equihash mining algorith with (150,5) parameters and customized data path. It is efficiently mined on GPUs. Using CPU is most likely to be not cost effective.

```
+-------------------------+----------------------------------------------------------------------------------------------------------+
|**Parameter**            | **Description & Example**                                                                                |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --miner_key             | Secret key to attribute mining rewards mined by the node to your wallet                                  |
|                         | Created using CLI walelt `export_miner_key` command with --subkey=<miner id> parameter                   |
|                         |                                                       |
|                         |                                                                                                          |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --owner_key             | Secret key allowing the node to monitor mining rewards mined by all mining nodes marked by this key.     |
|                         | Created using CLI walelt `export_owner_key` command                                                      |
|                         |                                                    |
|                         |                                                                                                          |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --pass                  | Wallet password. It is required since both Miner Key and Owner Key are protected by walelt password      |
|                         |                                                                                                          |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --stratum_port          | Port on which stratum server will listen to incoming connections. 0 if stratum server is disabled.       |
|                         |                                                                                                          |
|                         |                                                                                   |
|                         |                                                                                                          |
|                         |    stratum_port=0                                                                                        |
+-------------------------+----------------------------------------------------------------------------------------------------------+
| --stratum_secrets_path  | Path to folder containing stratum certificates                                                           |
|                         |                                                                                                          |
|                         |                                                                                   |
|                         |                                                                                                          |
|                         |    stratum_secrets_path=.                                                                                |
+-------------------------+----------------------------------------------------------------------------------------------------------+
```
