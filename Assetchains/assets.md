# Confidential Assets

## Create assets

For generate assets use: --asset_command 1 (option for creation) --asset_kid (set keyid for your new asset)

```  
./grimm-wallet --asset_command 1 --asset_kid 'key id' send -r 'youraddress' -a 'emission'
``` 
and waiting for response "Transaction completed"
```
I 2019-11-12.19:36:19.474 Confidential Assetchain Symbol: BTC
I 2019-11-12.19:36:19.475 BTC Wallet 10.3.5503
I 2019-11-12.19:36:19.475 Rules signature: 0-a2e96aa23e390b5605a71658074aeabb76332035e4777866d951afd394f4d6a1
I 2019-11-12.19:36:19.476 starting a wallet...
I 2019-11-12.19:36:19.544 wallet sucessfully opened...
D 2019-11-12.19:36:19.546 Async update started!
I 2019-11-12.19:36:19.546 WalletID 2e5c73327c954a35ee5bbbed2482194a672b79b663e774896b46aa1f344e60440f1 subscribes to BBS channel 741
I 2019-11-12.19:36:19.547 WalletID 37068f94e1cbdda8770cdf7818cb512e6fa906a23bdb57bc4dd504587d6bf3bd7d3 subscribes to BBS channel 880
I 2019-11-12.19:36:19.548 WalletID b67c5df650e3db70b69bb3bd00aea21f59b65c06bbfdaac4ca9fb4bf44be4b8d21 subscribes to BBS channel 182
I 2019-11-12.19:36:19.548 New address generated:

b67c5df650e3db70b69bb3bd00aea21f59b65c06bbfdaac4ca9fb4bf44be4b8d21

I 2019-11-12.19:36:19.548 Asset ID: 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.19:37:48.684 [f8deec80ab3045838572afb07a0e0409] Sending 0 centum  (fee: 100 centum )
I 2019-11-12.19:37:48.684 [f8deec80ab3045838572afb07a0e0409] Max height for response: 726
I 2019-11-12.19:37:48.684 [f8deec80ab3045838572afb07a0e0409] issues asset 100000000000000 with asset id: 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.19:37:48.725 Created emission kernel with amount 100000000000000 for asset id 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.19:37:48.726 [f8deec80ab3045838572afb07a0e0409][1] Transaction created. Kernel: 48b5ac84fb71a22ce175d42681f88f0796bcbb073506902083ae6232c7e55799 min height: 6 max height: 126
I 2019-11-12.19:37:48.726 Kernel commitment cc0bc3361b1757c06b3b216206c3f5469a5cf043b59f253b71f8690de9c674df
--- Asset emission: 100000000000000
D 2019-11-12.19:37:48.734 Async update finished!
D 2019-11-12.19:37:48.748 [f8deec80ab3045838572afb07a0e0409][1] register status 1
D 2019-11-12.19:37:48.749 Async update started!
I 2019-11-12.19:37:48.749 [f8deec80ab3045838572afb07a0e0409][1] Get proof for kernel: 48b5ac84fb71a22ce175d42681f88f0796bcbb073506902083ae6232c7e55799
I 2019-11-12.19:44:10.488 [f8deec80ab3045838572afb07a0e0409] Transaction completed
D 2019-11-12.19:44:10.489 Async update finished!

```
Then check wallet (copy your asset_id above)
```
./grimm-wallet --asset_id 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e info
```
```
I 2019-11-12.19:48:05.939 Confidential Assetchain Symbol: BTC
I 2019-11-12.19:48:05.939 BTC Wallet 10.3.5503
I 2019-11-12.19:48:05.939 Rules signature: 0-a2e96aa23e390b5605a71658074aeabb76332035e4777866d951afd394f4d6a1
I 2019-11-12.19:48:05.939 starting a wallet...
I 2019-11-12.19:48:06.001 wallet sucessfully opened...
I 2019-11-12.19:48:06.001 Parsing string 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.19:48:06.001 Parsing string ok. AssetID: 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
____Asset Wallet____

AssetID ..................5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e

Current height............8
Current state ID..........e33f637b12771a0f0644abd7a57e12c28ad1ec1632d75dd24dbd6852d22a789a

Available.................8779997 BTC  assets
Maturing..................0 centum 
In progress...............0 centum 
Unavailable...............0 centum 
Available coinbase .......0 centum 
Total coinbase............0 centum 
Avaliable fee.............0 centum 
Total fee.................0 centum 
Total unspent.............8779997 BTC  assets
```
## Send assets
```
./grimm-wallet --asset_command 2 --asset_id 'yourasset_id' send -r 'sendaddress' -a 'amount'
```
```
I 2019-11-12.20:18:14.926 Confidential Assetchain Symbol: BTC
I 2019-11-12.20:18:14.926 BTC Wallet 10.3.5503
I 2019-11-12.20:18:14.926 Rules signature: 0-a2e96aa23e390b5605a71658074aeabb76332035e4777866d951afd394f4d6a1
I 2019-11-12.20:18:14.926 starting a wallet...
I 2019-11-12.20:18:14.985 wallet sucessfully opened...
D 2019-11-12.20:18:14.985 Async update started!
I 2019-11-12.20:18:14.986 WalletID 113b663b5fecb21d113f2fe0caa4a9b0a7df2315340f567316746d320ece849fcb2 subscribes to BBS channel 275
I 2019-11-12.20:18:14.986 WalletID 647e397efc78d30464d3612bddee8353c0b12421575e40dc072296822312386bd2 subscribes to BBS channel 100
I 2019-11-12.20:18:14.986 WalletID b67c5df650e3db70b69bb3bd00aea21f59b65c06bbfdaac4ca9fb4bf44be4b8d21 subscribes to BBS channel 182
I 2019-11-12.20:18:14.986 WalletID 2e5c73327c954a35ee5bbbed2482194a672b79b663e774896b46aa1f344e60440f1 subscribes to BBS channel 741
I 2019-11-12.20:18:14.986 WalletID 37068f94e1cbdda8770cdf7818cb512e6fa906a23bdb57bc4dd504587d6bf3bd7d3 subscribes to BBS channel 880
I 2019-11-12.20:18:14.987 WalletID 3a0990cc51b7f1137a0c8c7d0e512bd78e7ad6d0ec9b41dd595e37992ed3eea584a subscribes to BBS channel 928
I 2019-11-12.20:18:14.987 New address generated:

3a0990cc51b7f1137a0c8c7d0e512bd78e7ad6d0ec9b41dd595e37992ed3eea584a

I 2019-11-12.20:18:14.987 Parsing string 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.20:18:14.987 Parsing string ok. AssetID: 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.20:18:15.088 [2fa684bd2ae94091ba6b4fa905735419] Sending 0 centum  (fee: 100 centum )
I 2019-11-12.20:18:15.088 [2fa684bd2ae94091ba6b4fa905735419] Max height for response: 737
I 2019-11-12.20:18:15.089 ----------------coin.m_ID,assetIDKey=chng-0:7181348963027024021, Value=999500000000005f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.20:18:15.089 -------------------m_AssetChange99900300000000
I 2019-11-12.20:18:15.150 [2fa684bd2ae94091ba6b4fa905735419][1] Transaction created. Kernel: 01990bc2d8cbcaa6b355f055a708fa9a4fbdb4ac1d10d3beb7fb7d5c0893ee52 min height: 17 max height: 137
I 2019-11-12.20:18:15.150 Kernel commitment 1f80b1ae447ed5e44ab482d8841e31ab92e7f877709fb1c53245a64a2c6c4292
I 2019-11-12.20:24:08.311 [2fa684bd2ae94091ba6b4fa905735419][1] Get proof for kernel: 01990bc2d8cbcaa6b355f055a708fa9a4fbdb4ac1d10d3beb7fb7d5c0893ee52
D 2019-11-12.20:24:08.311 Async update finished!
D 2019-11-12.20:24:08.311 Async update started!
I 2019-11-12.20:24:08.312 [2fa684bd2ae94091ba6b4fa905735419] Transaction completed
D 2019-11-12.20:24:08.312 Async update finished!
```

## Burn assets
```
./grimm-wallet --asset_command 3 --asset_kid 'neededkeyid' send -r 'youraddress' -a 'amount'
```
```
I 2019-11-12.20:04:16.718 Confidential Assetchain Symbol: BTC
I 2019-11-12.20:04:16.718 BTC Wallet 10.3.5503
I 2019-11-12.20:04:16.718 Rules signature: 0-a2e96aa23e390b5605a71658074aeabb76332035e4777866d951afd394f4d6a1
I 2019-11-12.20:04:16.719 starting a wallet...
I 2019-11-12.20:04:16.784 wallet sucessfully opened...
D 2019-11-12.20:04:16.786 Async update started!
I 2019-11-12.20:04:16.787 WalletID b67c5df650e3db70b69bb3bd00aea21f59b65c06bbfdaac4ca9fb4bf44be4b8d21 subscribes to BBS channel 182
I 2019-11-12.20:04:16.787 WalletID 2e5c73327c954a35ee5bbbed2482194a672b79b663e774896b46aa1f344e60440f1 subscribes to BBS channel 741
I 2019-11-12.20:04:16.787 WalletID 37068f94e1cbdda8770cdf7818cb512e6fa906a23bdb57bc4dd504587d6bf3bd7d3 subscribes to BBS channel 880
I 2019-11-12.20:04:16.788 WalletID 647e397efc78d30464d3612bddee8353c0b12421575e40dc072296822312386bd2 subscribes to BBS channel 100
I 2019-11-12.20:04:16.788 New address generated:

647e397efc78d30464d3612bddee8353c0b12421575e40dc072296822312386bd2

I 2019-11-12.20:04:16.789 Asset ID: 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.20:04:16.851 [f398b2c505a04dc481ea0626e2aa1065] Sending 0 centum  (fee: 100 centum )
I 2019-11-12.20:04:16.851 [f398b2c505a04dc481ea0626e2aa1065] Max height for response: 732
I 2019-11-12.20:04:16.852 ----------------coin.m_ID,assetIDKey=norm-0:11595221700596234295, Value=1000000000000005f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.20:04:16.852 -------------------m_AssetChange99950000000000
I 2019-11-12.20:04:16.884 Created emission kernel with amount 50000000000 for asset id 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.20:04:16.886 [f398b2c505a04dc481ea0626e2aa1065][1] Transaction created. Kernel: 56408712b79dddea322eb19b526df3cf0357c5d78a92f3cd2a637595dfc100cc min height: 12 max height: 132
I 2019-11-12.20:04:16.886 Kernel commitment c8750262b8a18f6cfa7b9a71b8279d320fa1fb001d11c45e0d265488e918f193
--- Asset emission: 50000000000
D 2019-11-12.20:04:16.894 Async update finished!
D 2019-11-12.20:04:16.913 [f398b2c505a04dc481ea0626e2aa1065][1] register status 1
D 2019-11-12.20:04:16.913 Async update started!
I 2019-11-12.20:04:16.914 [f398b2c505a04dc481ea0626e2aa1065][1] Get proof for kernel: 56408712b79dddea322eb19b526df3cf0357c5d78a92f3cd2a637595dfc100cc
I 2019-11-12.20:08:42.266 AssetID: 5f0556613b9586f000485ae1681fb80656377fcb8c68bcf3b5783d4a4273fb5e
I 2019-11-12.20:08:42.267 [f398b2c505a04dc481ea0626e2aa1065] Transaction completed
D 2019-11-12.20:08:42.267 Async update finished!
```
