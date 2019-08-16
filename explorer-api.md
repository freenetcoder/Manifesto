## API
### status
GET https://freenetcoder.com/status

Description: Gets current blockchain status.

Response:

{
 -  "chainwork": "0x1b14162b73dfd",
 -  "hash": "07142a2b61f84070b729f5f5a4a4f99cb01bbe70d24d5ffebd76d006cebe1229",
 -  "height": 1203,
 -  "low_horizon": 0,
 -  "timestamp": 1565024115
}
### block

GET https://freenetcoder.com/block?height={height}
or
GET https://freenetcoder.com/block?hash={hash}
or
GET https://freenetcoder.com/block?kernel={kernel}

Description: Gets block info for specified height, hash or kernel.

Response:

{
 -  "chainwork": "0x586bfaac3dfd",
 -  "difficulty": 48343.080078125,
 - "found": true,
 -  "hash": "57d79dfc37202abd7f03ac77307f168067360c98bb18a07525300618aa975e8a",
 -  "height": 1000,
 -  "inputs": [],
 -  "kernels": [
    {
    -   "excess": "0xe4e416bc7ddb1e0f0358771fe664ca42a7520a2e28b88013b1d225935b41f869",
    -   "fee": 0,
    -   "id": "4e4181f72f7e03306a9d8571f6f75697310abad90e3a95e3bdda4ebd863b2b0d",
    -   "maxHeight": 18446744073709551615,
    -   "minHeight": 1000
    }
  ],
  "outputs": [
    {
    -   "coinbase": true,
    -   "commitment": "0x720f80696c23eb550a7ec878394bf6e01ff203e518ccb57651521466e312b266",
    -   "incubation": 0,
    -   "maturity": 1090
    }
  ],
 -  "prev": "3ef8c4064f2874e1dc7900d4459c1974eee8da3c91975e35e466ff95a28f2b90",
 -  "subsidy": 10000000000,
 -  "timestamp": 1565015507
}
### blocks
GET http://freenetcoder.com/blocks?height={start}&n={count}

Description: Gets blocks info for specified range, where count should be <= 1500.
