# Errors

<aside class="notice">
In addition to the standard <a href="https://github.com/ethereum/wiki/wiki/JSON-RPC-Error-Codes-Improvement-Proposal#json-rpc-standard-errors">Ethereum JSON-RPC error codes</a>, the Coinbase API will return the following error codes:
</aside>



Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
404 | Not Found -- The specified endpoint could not be found.
429 | Too Many Requests -- You've hit your rate limit. Contact us if you require a higher rate limit.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

