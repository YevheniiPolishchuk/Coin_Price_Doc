# Standards and Conventions

Each HTTP request must contain the header `Accept: application/json`. You should also send an `Accept-Encoding: deflate, gzip` header to receive data fast and efficiently.

**Endpoint Response Payload Format** \
All endpoints return `data` in JSON format with the results of your query under data if the call is successful.

A `Status` object is always included for both successful calls and failures when possible.

