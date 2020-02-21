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


## Token Balances

This endpoint returns the token balances for a specific address given a list of tokens.


```shell
curl https://eth-mainnet.api.coinbase.com/v1/api_key \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"get_tokenBalances","params":["address":"0xecA41677558025c76BfD20e9289283cb4Ca85f46", "tokens":["mkr", "dai", "zrx"]],"id":7}'
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
      "blockNumber": 7909779,
      "blockTimestamp": 1559879572
    }
}
```


### HTTP Request

`GET https://eth-mainnet.api.coinbase.com/v1/getTokenBalances?`

### DATA

| Parameter | Type     | Description                                         |
| --------- | -------- | --------------------------------------------------- |
| address \*       | _string_ | The address (20 bytes) to check for balance                                |
| tokens \*    | [_strings_] | Token(s) from the [table](#erc20-tokens) that we support by name               |

<aside class="notice">
Note: All parameters with a * are requried
</aside>


### Response Overview

**`Data Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                                                           |
| address     | string | The address for which token balances were checked |
| tokenBalances | [Object] | Returns an array of token balance objects. Each object has a `tokenName` field that is a `string` and a `tokenBalance` field, which is either `decimal` or `null` (if no token balance exists) |                              
| blockNumber     | integer | The token balances are calculated as of this block |
| blockTimestamp | integer | The unix timestamp for when the block was mined |

