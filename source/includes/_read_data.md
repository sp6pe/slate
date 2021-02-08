# Read Data
These endpoint enable reading of network data from the blockckchain

All endpoints in this section return a meta object

**`Meta Object`**

| Field      | Type      | Description                                                                                               |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |                                             
| latestBlockNumber     | integer | The block number of the latest block as seen by Coinbase |
| latestBlockTimestamp | integer | The block UNIX timestamp in seconds of the latest block as seen by Coinbase |
| timestamp | integer | The server UNIX timestamp in seconds when the API request is made |



## Get Chain Height

This endpoint returns the latest block height for a specific asset


```shell
curl https://eth-mainnet.api.coinbase.com/v1/API-KEY \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"get_assetHeight"},"id":7}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": 7,
  "result": 
    {
      "height": 21312323
    },
    "meta":{
      "latestBlockNumber": 7909779,
      "latestBlockTimestamp": 1559879572,
      "timestamp": 1540474596
    }
}
```

## Get Transaction By Hash 
This endpoint returns the transaction data for a specific asset

```shell
curl https://eth-mainnet.api.coinbase.com/v1/API-KEY \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"get_assetTxnInfo", "params":{"txnHash":"0x342432"}},"id":7}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": 7,
  "result": 
    {
      "symbol": "eth",
      "txnHash": "0x323",
      "to": "0x2e2",
      "from": "0x233"
    },
    "meta":{
      "latestBlockNumber": 7909779,
      "latestBlockTimestamp": 1559879572,
      "timestamp": 1540474596
    }
}
```



## Get Address Balance


## Get Txns by Address