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

All endpoints in this section return a meta object

**`Meta Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                             
| latestBlockNumber     | integer | The block number of the latest block as seen by Coinbase |
| latestBlockTimestamp | integer | The block UNIX timestamp in seconds of the latest block as seen by Coinbase |
| timestamp | integer | The server UNIX timestamp in seconds when the API request is made |



## Token Balances

This endpoint returns the token balances for a specific address given a list of tokens.


```shell
curl https://eth-mainnet.api.coinbase.com/v1/API-KEY \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"get_tokenBalances","params":{"address":"0xecA41677558025c76BfD20e9289283cb4Ca85f46", "tokenSymbols":["mkr", "dai", "zrx"]},"id":7}'
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
        {"tokenSymbol": "mkr", "tokenBalance": 213, "priceUsd": "617.22"},
        {"tokenSymbol": "dai", "tokenBalance": 0, "priceUsd": "1.01"},
        {"tokenSymbol": "zrx","tokenBalance": 323.33, "priceUsd": "0.32"}
      ],
    },
    "meta":{
      "latestBlockNumber": 7909779,
      "latestBlockTimestamp": 1559879572,
      "timestamp": 1540474596
    }
}
```


### DATA

| Parameter | Type     | Description                                         |
| --------- | -------- | --------------------------------------------------- |
| address \*       | _string_ | The address (20 characters) to check for balance                                |
| tokenSymbols \*    | [_strings_] | Token symbols from the supported [table](#erc20-tokens)          |

<aside class="notice">
Note: All parameters with a * are requried
</aside>


### Response Overview

**`Result Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |
| address     | _string_ | The address for which token balances were checked (20 characters) |
| tokenBalances | [Object] | Returns an array of token balance objects (definition below)  |           


**`tokenBalances Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- 
| tokenSymbol     | _string_ | The symbol of the token |
| tokenBalance | _decimal_ | The decoded balance of the token in the `address`. `0` if no balance | 
| priceUsd | _string_ | The market price in USD of the token at the `timestamp` field in the meta object. Price sourced from Coinbase Pro |       


## Token Transfers by Address

This endpoint returns the token transfers for a specific address


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
          "tokenSymbol":"mkr",
          "tokenContract":"0xf8c35ab8bc40b7bcbf65ae47afc70b1424b5be90",
          "value":223,
          "transactionHash":"0x30ef9d430ac1ad6fa9807603048fd2abc79bc9dc43012a57da9a2899f15cb576",
          "blockNumber": 7909779,
          "blockTimestamp": 1559879512,
          "priceUsd": "673.23"
        },
        {
          "from":"0xecA41677558025c76BfD20e9289283cb4Ca85f46", 
          "to": "0x00cFBbaF7DDB3a1476767101c12a0162e241fbAD",
          "tokenSymbol":"zrx",
          "tokenContract":"0xf8c35ab8bc40b7bcbf65ae47afc70b1424b5be90",
          "transactionHash":"0x30ef9d430ac1ad6fa9807603048fd2abc79bc9dc43012a57da9a2899f15cb576",
          "value":24223, 
          "blockNumber": 6909779,
          "blockTimestamp": 1559879572,
          "priceUsd": "0.23"
        },
      ],
    },
    "meta":{
      "latestBlockNumber": 7909779,
      "latestBlockTimestamp": 1559879572,
      "timestamp": 1540474596
    }
}
```



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
| tokenTransfers | [Object] | Returns an array of token transfer objects (definition below) |                              


**`tokenTransfers Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                                                           |
| from     | string | Address of the sender (20 characters) |
| to | string| Address of the receiver (20 characters) |                              
| tokenSymbol     | string | The symbol of the token |
| tokenContract | string | Address of the token contract (20 characters)|
| value | decimal | Value of the tokens transferred|
| transactionHash     | integer | String representing the hash (32 characters) of the transaction |
| blockNumber     | integer | The block in which the token transfers occured |
| blockTimestamp | integer | The unix timestamp for when the block was mined |
| priceUsd | _string_ | Price in USD of the `tokenSymbol` at `blockTimestamp`. Price sourced from Coinbase Pro|

## Token Transfers by Transaction Hash

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
          "from": "0xecA41677558025c76BfD20e9289283cb4Ca85f46", 
          "to": "0x00cFBbaF7DDB3a1476767101c12a0162e241fbAD",
          "tokenSymbol": "mkr",
          "tokenContract": "0xf8c35ab8bc40b7bcbf65ae47afc70b1424b5be90",
          "value": 223, 
          "logIndex": 3,
          "priceUsd": "273.23"
        }
      ],
      "blockNumber": 7909779,
      "blockTimestamp": 1559879572
    },
    "meta":{
      "latestBlockNumber": 7909779,
      "latestBlockTimestamp": 1559879572,
      "timestamp": 1540474596
    }
}
```




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
| transactionHash     | _string_ | The hash of the transaction (32 characters) |
| tokenTransfers | [Object] | Returns an array of token transfer objects (definition below) |                              
| blockNumber     | _intege_ | The block in which the token transfers occured |
| blockTimestamp | _integer_ | The UNIX timestamp in seconds for when the block was mined |

**`tokenTransfers Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                                                           |
| from     | _string_ | Address of the sender (20 characters) |
| to | _string_| Address of the receiver (20 characters) |                              
| tokenSymbol     | _string_ | The symbol of the token |
| tokenContract | _string_ | Address of the token contract (20 characters) |
| value | _decimal_ | Value of the tokens transferred|
| priceUsd | _string_ | Price in USD of the `tokenSymbol` at `blockTimestamp`. Price sourced from Coinbase Pro|
| logIndex | _integer_ | integer of the transfer events position in the block; useful when there are multiple transfers in one transaction |



## Token Balance at Block

## Token Metadata

## Token Allowance
