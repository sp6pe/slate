---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell


toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - tokens
  - read_data
  - construct_transactions
  - cold_storage_ops
  - errors


search: true
---

# Introduction

Coinbase provides a simple, fast, and reliable **JSON-RPC API** for blockchain developers. We know it's hard to build on blockchains, and that's why we've built powerful endpoints that make key tasks trivial 

This API reference provides information on available endpoints and how to interact with them.



# Authentication

```shell
curl https://eth-mainnet.api.coinbase.com/v1/API-KEY \
-X POST \
-H "Content-Type: application/json" \
-d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":3}'
```


> Results:

```json
{

  "jsonrpc": "2.0",
  "id": 3,
  "result": "0x65a8db"
}
```

To use the Coinbase Blockchain API, you need an API key to authenticate your requests. To obtain your API key contact us [here](https://developers.coinbase.com/).

The API is designed according to the [JSON-RPC](https://www.jsonrpc.org/specification) standards 

###HTTP Request
`curl https://<network>.api.coinbase.com/v1/API-KEY`

<aside class="notice">
Replace `API-KEY` with your unique API-KEY
</aside>