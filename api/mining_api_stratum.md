# Grimm mining protocol API

The protocol is based on JSON RPC and uses Long Polling to have a conversation between Miner and Node. 

## Miner to Node
### Login

Miner subscribes to the node to receive jobs.

api_key - miner registration key.
```
{
    "method" : "login", 
    "api_key": "skjdb7343636gucgjdjgd",
    "id":"login",
    "jsonrpc":"2.0" 
}
```
### Solution

Miner sends a solution to the node.

nonce - matched nonce for given solution.

output - Equhash solition for current difficulty.
```
{
"id":"212",
"jsonrpc":"2.0",
"method":"solution",
"nonce":"0bb11009afc29dbe",
"output":"a32a1e04ca447f895cfdd8fd1f96fe2ebdd8cd8f77e9c3010ca7231d5da5d0b0cee7ee857981389070eec196bfb4bd15439ef27dd370c4c763bdbad66d066f7cb2f06318e1a0c68c9f5aa8fe8112c479d9a227759d0f864136f265e9ffd3b276b9ba2243"
}
```
## Node to Miner
### Job

Miner will send new job automatically to connected miners.

id - is a job index

input - block header data hash (with current difficulty) as an input parameter for Equihash.

difficulty - current chain difficulty.
```
{ 
"difficulty":3441671469,
"id":"212",
"input":"636b90cc38bc7a347f074d9ca97c3a2158330f6844f8f52075a38a15ab483223",
"jsonrpc":"2.0",
"method":"job"
}
```
### Cancel

Miner will send a notification to cancel job with a given id

id - is a job index
```
{ 
"id":"212",
"jsonrpc":"2.0",
"method":"cancel"
}
```
### Result

This is what server will return to login or solution requests, identified by id string of message has been sent from the miner to the node.

Example 1 (login failed):
```
{
    "code":-32003,
    "description":"Login failed",
    "id":"login",
    "jsonrpc":"2.0",
    "method":"result"
}
```
Example 2 (solution accepted):
```
{
    "code":1,
    "description":"accepted",
    "id":"212",
    "jsonrpc":"2.0",
    "method":"result"
}
```
Example 3: (reply with nonce prefix)
```
{
    "code":0,
    "description":"Login successful",
    "id":"login",
    "jsonrpc":"2.0",
    "nonceprefix":"ab4e3a",
    "method":"result"
}
```
Note: "nonceprefix" is an optional component. If "nonceprefix" is given the first bytes of the used nonce must match the given pattern. Allowed is a prefix from 0 to 6 bytes. If "nonceprefix" is not given the miner may use the full nonce range.
