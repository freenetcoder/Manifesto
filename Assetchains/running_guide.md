# Confidential assetchain running guide

## Getting binaries

Сhoose a branch "[assetchain](https://github.com/freenetcoder/grimm/tree/assetchain)"- it's the latest released version with support CAC. You can get binaries from [Github Releases - Assetchains init pre-release ](https://github.com/freenetcoder/grimm/releases/tag/CAC_10_3) or build yourself from the sources.

Detailed instructions on how to build a project for Windows, Linux, Mac platforms you can find [here](https://github.com/freenetcoder/Manifesto/blob/master/build.md).

    Add -DGRIMM_NO_QT_UI_WALLET=On command line parameter to the Cmake for only CLI version of the wallet without UI and QT5 library dependencies. P.s. GUI will support CAC&CA soon

You will need to build 2 binaries for running your own assetchain:

- grimm-node
- grimm-wallet

And copy 2 files in folder with binaries:

- grimm-node.cfg
- grimm-wallet.cfg

## Set Assetchains params

At grimm-node.cfg && grimm-wallet.cfg find section with tittle Assetchains. To enable option from list you need to uncomment it.

```
################################################################################
# Confidential Assetchains (CAC) options:
################################################################################

# Assetchain symbol/ticker
# cac_symbol=

# Assetchain port to start the server on
# cac_port=

# Assetchain pre-mine at 1st block in the smallest unit of the coin (1 coin = 10^8 units)
# cac_premine=

# Assetchain initial coinbase emission in a single block in the smallest unit of the coin (1 coin = 10^8 units)
# cac_blockreward=

# Enable assets (default 'false', to switch on - 'true')
# asset_enabled=

# Asset exchange in main coins (default 'false', to switch on - 'true')
# asset_exchange=

# Assetchain height of the last block that still has the initial emission, the drop is starting from the next block
# cac_drop0=

# Each such a cycle there's a new halving (in heights)
# cac_drop1=

# Coinbase coins can spend after blocks
# cac_coinbasematurity=

# Standart coins can spend after blocks
# cac_standartmaturity=

# Blocksize
# cac_blocksize=

# Block time in sec
# cac_blocktime=

# Timestamps ahead by more than FTL won't be accepted (in sec)
# cac_ftl=

# Start difficulty, default 2^1 (set 0 for start cpu mining)
# cac_diff=

# Non-confidential regular UTXO (default 'false', to switch on - 'true')
# cac_publicutxo=

```
## Init wallet

To create a new wallet run the following command:
```
$ ./grimm-wallet init
```
Output example (in this example we are creating assetchain with ticker BTC):
```
I 2019-11-12.17:14:34.937 Confidential Assetchain Symbol: BTC
I 2019-11-12.17:14:34.937 BTC Wallet 10.3.5502
I 2019-11-12.17:14:34.937 Rules signature: 0-b4b647b673423f97bf656281b0b82b02dad83b9281b7fce51ad1a0cd5064c9df
I 2019-11-12.17:14:34.937 starting a wallet...
I 2019-11-12.17:14:34.937 Generating seed phrase...
======
Generated seed phrase: 

	soft;film;then;primary;chicken;dress;obscure;skirt;science;mom;rare;mother;

	IMPORTANT

	Your seed phrase is the access key to all the cryptocurrencies in your wallet.
	Print or write down the phrase to keep it in a safe or in a locked vault.
	Without the phrase you will not be able to recover your money.
======
I 2019-11-12.17:14:35.012 wallet successfully created...
I 2019-11-12.17:14:35.012 New address generated:

6c7d3c1eec51827c6ceb33e4832f50d9e4ef72060a4492a0aba61f1250699d8d2a

I 2019-11-12.17:14:35.012 comment = default

```
## Export Owner Key
Once wallet is initialised, you have to export your Owner Key.
```
$ ./grimm-wallet export_owner_key
```
```
I 2019-11-12.17:43:52.254 Confidential Assetchain Symbol: BTC
I 2019-11-12.17:43:52.254 BTC Wallet 10.3.5502
I 2019-11-12.17:43:52.254 Rules signature: 0-b4b647b673423f97bf656281b0b82b02dad83b9281b7fce51ad1a0cd5064c9df
I 2019-11-12.17:43:52.254 starting a wallet...
Owner Viewer key: WBw+MAPw/0BcIVQABCp4Xr0U3Lr8q7BQCJT0cWPgUbMxiNpR+JAEYNWCNlbiLIogbyPGKcE0j8AVjKX7vW7TZ4a303FZ4xOOzGNkV11Ph3K3PdE1Nm/mddghmefVYvKqojCxEutSluWgDz+F
```
## Export miner key
```
$./grimm-wallet export_miner_key --subkey=1
```
```
I 2019-11-12.17:58:43.537 Confidential Assetchain Symbol: BTC
I 2019-11-12.17:58:43.537 BTC Wallet 10.3.5502
I 2019-11-12.17:58:43.537 Rules signature: 0-b4b647b673423f97bf656281b0b82b02dad83b9281b7fce51ad1a0cd5064c9df
I 2019-11-12.17:58:43.537 starting a wallet...
Secret Subkey 1: XEj9fDUAzjN/IVQABCp4Xr0U3Lr8q7BQCJT0cWPgUbMxiNpR+JAEYNX7VYPwum4WwvPLdkUFQB/958lSGTazibvIMHkCmRpy6lI=
```
## Copy your miner_key and owner_key to grimm-node.cfg in the appropriate lines ( do not forget to uncomment them)
```
.......
# Owner viewer key
owner_key=WBw+MAPw/0BcIVQABCp4Xr0U3Lr8q7BQCJT0cWPgUbMxiNpR+JAEYNWCNlbiLIogbyPGKcE0j8AVjKX7vW7TZ4a303FZ4xOOzGNkV11Ph3K3PdE1Nm/mddghmefVYvKqojCxEutSluWgDz+F


# Standalone miner key
miner_key=XEj9fDUAzjN/IVQABCp4Xr0U3Lr8q7BQCJT0cWPgUbMxiNpR+JAEYNX7VYPwum4WwvPLdkUFQB/958lSGTazibvIMHkCmRpy6lI=

.......
```
## Set number of CPU mining threads (1,2,3,..) to mine your own coin (at grimm-node.cfg)
```
# number of mining threads(there is no mining if 0)
 mining_threads=1
```
## Start your own mimblewimble blockchain
```
./grimm-node
```
```
I 2019-11-12.18:14:54.462 Confidential Assetchain Symbol: BTC
I 2019-11-12.18:14:54.462 BTC Node 10.3.5502
I 2019-11-12.18:14:54.462 Rules signature: 0-b4b647b673423f97bf656281b0b82b02dad83b9281b7fce51ad1a0cd5064c9df
I 2019-11-12.18:14:54.695 starting a node on 10015 port...
I 2019-11-12.18:14:54.718 Settings configuration
I 2019-11-12.18:14:54.718 Loading UTXOs...
I 2019-11-12.18:14:54.718 Node ID=6891cd366450b078519c580b3e6a826ac398fbb3ac933e7ab81f529daf0163bd
I 2019-11-12.18:14:54.718 Initial Tip: 0-00000000000000000022fa3804b58adb900511dd1a8a75b5d793a7d372ac93b2
I 2019-11-12.18:14:54.718 Tx replication is OFF
I 2019-11-12.18:14:54.718 Rescanning owned Txos...
I 2019-11-12.18:14:54.718 Recovered 0/0 unspent/total Txos
I 2019-11-12.18:14:54.719 GenerateNewBlock: size of block = 294; amount of tx = 0
I 2019-11-12.18:14:54.719 Block generated: Height=1, Fee=0, Difficulty=00-000000(1), Size=294
```
When 1st block will be find, you will see
```
I 2019-11-12.18:18:03.553 New block mined: 1-3bf30ca99fc71f9a21b72fd61744e3c8d5f4cf8310ba889615bc07fc9d6a11a1
I 2019-11-12.18:18:03.566 1-3bf30ca99fc71f9a21b72fd61744e3c8d5f4cf8310ba889615bc07fc9d6a11a1 Header accepted
I 2019-11-12.18:18:03.586 My Tip: 1-3bf30ca99fc71f9a21b72fd61744e3c8d5f4cf8310ba889615bc07fc9d6a11a1, Work = 1
I 2019-11-12.18:18:03.590 GenerateNewBlock: size of block = 294; amount of tx = 0
I 2019-11-12.18:18:03.590 Block generated: Height=2, Fee=0, Difficulty=00-000000(1), Size=294

```

## Now, your mining node work and you need connect your wallet

By default, assetchain node start at 10015 port. Open grimm-wallet.cfg and find node address (if you run on same machine, you need set 127.0.0.1:10015)
```
# address of node
 node_addr=127.0.0.1:10015
```
Then run:
```
$ ./grimm-wallet listen
```
```
I 2019-11-12.18:31:39.083 Confidential Assetchain Symbol: BTC
I 2019-11-12.18:31:39.084 BTC Wallet 10.3.5502
I 2019-11-12.18:31:39.084 Rules signature: 0-b4b647b673423f97bf656281b0b82b02dad83b9281b7fce51ad1a0cd5064c9df
I 2019-11-12.18:31:39.084 starting a wallet...
I 2019-11-12.18:31:39.143 wallet sucessfully opened...
D 2019-11-12.18:31:39.144 Async update started!
I 2019-11-12.18:31:39.144 WalletID 6c7d3c1eec51827c6ceb33e4832f50d9e4ef72060a4492a0aba61f1250699d8d2a subscribes to BBS channel 108
D 2019-11-12.18:31:39.144 Async update finished!
I 2019-11-12.18:31:39.247 Sync up to 4-b8445e9d6282e443d757b51f39da969ac307217eb751ea510c2df28c59edefd5
I 2019-11-12.18:31:39.247 Synchronizing with node: 0% (0/1)
I 2019-11-12.18:31:39.293 CoinID: Key=mine-1:1, Value=99999999999 AssetID=0000000000000000000000000000000000000000000000000000000000000000 Maturity=91 Confirmed
I 2019-11-12.18:31:39.293 CoinID: Key=mine-1:2, Value=8000000000 AssetID=0000000000000000000000000000000000000000000000000000000000000000 Maturity=92 Confirmed
I 2019-11-12.18:31:39.293 CoinID: Key=mine-1:3, Value=8000000000 AssetID=0000000000000000000000000000000000000000000000000000000000000000 Maturity=93 Confirmed
I 2019-11-12.18:31:39.294 CoinID: Key=mine-1:4, Value=8000000000 AssetID=0000000000000000000000000000000000000000000000000000000000000000 Maturity=94 Confirmed
I 2019-11-12.18:31:39.294 Synchronizing with node: 100% (1/1)
I 2019-11-12.18:31:39.294 Current state is 4-b8445e9d6282e443d757b51f39da969ac307217eb751ea510c2df28c59edefd5
D 2019-11-12.18:31:39.294 Async update started!
D 2019-11-12.18:31:39.294 Async update finished!
I 2019-11-12.18:33:24.965 Sync up to 5-468ed2b0067379314b555793f3634340d3c33a2d454dbdeb82f8ac71cc9ede7f
I 2019-11-12.18:33:24.965 Synchronizing with node: 0% (0/1)
I 2019-11-12.18:33:24.967 CoinID: Key=mine-1:5, Value=8000000000 AssetID=0000000000000000000000000000000000000000000000000000000000000000 Maturity=95 Confirmed
I 2019-11-12.18:33:24.967 Synchronizing with node: 100% (1/1)

```
When you see Synchronizing with node: 100% you can check:
```
$ ./grimm-wallet info
```
```
I 2019-11-12.18:36:28.646 Confidential Assetchain Symbol: BTC
I 2019-11-12.18:36:28.646 BTC Wallet 10.3.5502
I 2019-11-12.18:36:28.646 Rules signature: 0-b4b647b673423f97bf656281b0b82b02dad83b9281b7fce51ad1a0cd5064c9df
I 2019-11-12.18:36:28.647 starting a wallet...
I 2019-11-12.18:36:28.706 wallet sucessfully opened...
____Wallet summary____

Current height............5
Current state ID..........468ed2b0067379314b555793f3634340d3c33a2d454dbdeb82f8ac71cc9ede7f

Available.................0 centum 
Maturing..................1319 BTC 99999999 centum 
In progress...............0 centum 
Unavailable...............0 centum 
Available coinbase .......0 centum 
Total coinbase............1319 BTC 99999999 centum 
Avaliable fee.............0 centum 
Total fee.................0 centum 
Total unspent.............1319 BTC 99999999 centum 
```
P.s coinbase and standart tx maturity set at assetchain params before starting node.

For sending coins and working with assets (tokens) needed 2nd node in validating mode (mean with mining_threads=0 and connected to first node by adding params peer=id:port of 1st mining node)
