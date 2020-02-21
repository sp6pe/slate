# ERC20 Tokens

The tokens supported for this endpoint are:

| Name                 | Symbol       |
| -------------------- | ------------ |
| USD Coin             | `usdc`       |
| Multi-Collateral Dai | `dai`        |
| Single-Collateral Dai | `sai`        |
| Compound Dai | `cdai`        |
| Maker                 | `mkr`   |
| Basic Attention Token | `bat`   |
| OmiseGo               | `omg`   |
| Synthetix                 | `snx`   |
| Augur                 | `rep`   |
| Golem                 | `gnt`   |
| ZRX                   | `zrx`   |
| Decentraland          | `mana`  |
| Numerai               | `nmr`   |
| Tokencard             | `tkn`   |
| Bancor                | `bnt`   |
| Loom Network          | `loom`  |
| Status                | `snt`   |
| Civic                 | `cvc`   |
| Kyber Network         | `knc`   |
| iExec RLC             | `rlc`   |
| ChainLink             | `link`  |
| Fetch.ai.             | `fet`   |
| Tether               | `usdt_erc20` |
| Paxos Standard Token | `pax`        |
| TrueUSD              | `tusd`       |
| Gemini Dollar        | `gusd`       |

All endpoints return a meta object

**`Meta Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                             
| latestBlockNumber     | integer | The block number of the latest block as seen by Coinbase |
| latestBlockTimestamp | integer | The block timestamp number of the latest block as seen by Coinbase |



## Token Balances

This endpoint returns the token balances for a specific address given a list of tokens.


```shell
curl https://eth-mainnet.api.coinbase.com/v1/api_key \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"get_tokenBalances","params":{"address":"0xecA41677558025c76BfD20e9289283cb4Ca85f46", "tokens":["mkr", "dai", "zrx"]},"id":7}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": 7,
  "result": 
    {
      "address": "0xecA41677558025c76BfD20e9289283cb4Ca85f46",
      "tokenBalances": 
      [
        {"tokenName":"mkr", "tokenBalance": 213},
        {"tokenName":"dai", "tokenBalance": null},
        {"tokenName":"zrx","tokenBalance": 323.33}
      ],
    },
    "meta":{
      "latestBlockNumber": 7909779,
      "latestBlockTimestamp": 1559879572
    }
}
```


### HTTP Request

`GET https://eth-mainnet.api.coinbase.com/v1/api_key?`

### DATA

| Parameter | Type     | Description                                         |
| --------- | -------- | --------------------------------------------------- |
| address \*       | _string_ | The address (20 characters) to check for balance                                |
| tokens \*    | [_strings_] | Token(s) from the [table](#erc20-tokens) that we support by name               |

<aside class="notice">
Note: All parameters with a * are requried
</aside>


### Response Overview

**`Result Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                                                           |
| address     | _string_ | The address for which token balances were checked (20 characters) |
| tokenBalances | [Object] | Returns an array of token balance objects. Each object has a `tokenName` field that is a `string` and a `tokenBalance` field, which is either `decimal` or `null` (if no token balance exists) |                              
| blockNumber     | integer | The token balances are calculated as of this block |
| blockTimestamp | integer | The unix timestamp for when the block was mined |


## Token Transfers

This endpoint returns the token transfers for a specific transaction hash


```shell
curl https://eth-mainnet.api.coinbase.com/v1/api_key \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"get_tokenTransfersByHash","params":{"transactionHash":"0xb5c8bd9430b6cc87a0e2fe110ece6bf527fa4f170a4bc8cd032f768fc5219838"},"id":7}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": 7,
  "result": 
    {
      "transactionHash": "0xb5c8bd9430b6cc87a0e2fe110ece6bf527fa4f170a4bc8cd032f768fc5219838",
      "tokenTransfers": 
      [
        {
          "from":"0xecA41677558025c76BfD20e9289283cb4Ca85f46", 
          "to": "0x00cFBbaF7DDB3a1476767101c12a0162e241fbAD",
          "tokenName":"mkr",
          "tokenContract":"0xf8c35ab8bc40b7bcbf65ae47afc70b1424b5be90",
          "value":223, 
          "logIndex":3
        }
      ],
      "blockNumber": 7909779,
      "blockTimestamp": 1559879572
    },
    "meta":{
      "latestBlockNumber": 7909779,
      "latestBlockTimestamp": 1559879572
    }
}
```


### HTTP Request

`GET https://eth-mainnet.api.coinbase.com/v1/api_key?`

### DATA

| Parameter | Type     | Description                                         |
| --------- | -------- | --------------------------------------------------- |
| transactionHash \*       | _string_ | String representing the hash (32 characters) of the transaction                               |

<aside class="notice">
Note: All parameters with a * are requried
</aside>


### Response Overview

**`Result Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                                                           |
| transactionHash     | string | The hash of the transaction (32 characters) |
| tokenTransfers | [Object] | Returns an array of token transfer objects (definition below) |                              


**`tokenTransfers Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                                                           |
| from     | string | Address of the sender (20 characters) |
| to | string| Address of the receiver (20 characters) |                              
| tokenName     | string | Name of the token |
| tokenContract | string | Address of the token contract string |
| value | decimal | Value of the tokens transferred|
| logIndex | integer | integer of the transfer events position in the block; useful when there are multiple transfers in one transaction |



## Token Transfers by Address

This endpoint returns the token transfers for a specific transaction hash


```shell
curl https://eth-mainnet.api.coinbase.com/v1/api_key \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"get_tokenTransfersByAddress","params":{"address":"0xecA41677558025c76BfD20e9289283cb4Ca85f46"},"id":7}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": 7,
  "result": 
    {
      "address": "0xecA41677558025c76BfD20e9289283cb4Ca85f46",
      "tokenTransfers": 
      [
        {
          "from":"0xecA41677558025c76BfD20e9289283cb4Ca85f46", 
          "to": "0x00cFBbaF7DDB3a1476767101c12a0162e241fbAD",
          "tokenName":"mkr",
          "tokenContract":"0xf8c35ab8bc40b7bcbf65ae47afc70b1424b5be90",
          "value":223,
          "transactionHash":"0x30ef9d430ac1ad6fa9807603048fd2abc79bc9dc43012a57da9a2899f15cb576",
          "blockNumber": 7909779,
          "blockTimestamp": 1559879512
        },
        {
          "from":"0xecA41677558025c76BfD20e9289283cb4Ca85f46", 
          "to": "0x00cFBbaF7DDB3a1476767101c12a0162e241fbAD",
          "tokenName":"zrx",
          "tokenContract":"0xf8c35ab8bc40b7bcbf65ae47afc70b1424b5be90",
          "value":24223, 
          "blockNumber": 6909779,
          "blockTimestamp": 1559879572
        },
      ],
    },
    "meta":{
      "latestBlockNumber": 7909779,
      "latestBlockTimestamp": 1559879572
    }
}
```


### HTTP Request

`GET https://eth-mainnet.api.coinbase.com/v1/api_key?`

### DATA

| Parameter | Type     | Description                                         |
| --------- | -------- | --------------------------------------------------- |
| address \*       | _string_ | The address (20 characters) to check for token transfers          |

<aside class="notice">
Note: All parameters with a * are requried
</aside>


### Response Overview

**`Result Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                                                           |
| address     | string | The address to check for token transfer (20 characters) |
| tokenTransfers | [Object] | Returns an array of token transfer objects (definition below), empty array if no token transfers |                              


**`tokenTransfers Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                                                           |
| from     | string | Address of the sender (20 characters) |
| to | string| Address of the receiver (20 characters) |                              
| tokenName     | string | Name of the token |
| tokenContract | string | Address of the token contract string |
| value | decimal | Value of the tokens transferred|
| transactionHash     | integer | String representing the hash (32 characters) of the transaction |
| blockNumber     | integer | The block in which the token transfers occured |
| blockTimestamp | integer | The unix timestamp for when the block was mined |
