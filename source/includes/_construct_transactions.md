
# Construct Transactions

These endpoints manage all aspects of constructing and sending transactions 


## Construct Unsigned Transaction

This endpoint returns the currency definition for a specific asset


```shell
curl https://eth-mainnet.api.coinbase.com/v1/API-KEY \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"put_constructTxn", "params":{"symbol":"btc"}},"id":7}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": 7,
  "result": 
    {
      "symbol": "BTC",
      "name": "Bitcoin",
      "decimal_places" :10,
      "accounting_model":"UTXO",
      "destination_tag": false,
    }
}
```

## Validate Transaction


## Broadcast Transaction


## Estimate Fee