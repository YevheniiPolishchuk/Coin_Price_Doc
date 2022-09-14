# Errors and Rate Limits

**API Request Throttling**&#x20;

Use of the CPAY Coin Price API is subject to API call rate limiting or "request throttling". This is the number of HTTP calls that can be made simultaneously or within the same minute with your API Key before receiving an HTTP 429 "Too Many Requests" throttling error. This limit scales with the usage tier and resets depending on your plan. For Basic is 60 seconds.

**HTTP Status Codes** \
The API uses standard HTTP status codes to indicate the success or failure of an API call.

`400 (Bad Request)` The server could not process the request, likely due to an invalid argument.&#x20;

`401 (Unauthorized)` Your request lacks valid authentication credentials, likely an issue with your API Key.&#x20;

`403 (Forbidden)` Your request was rejected due to a permission issue, likely a restriction on the API Key's associated service plan. Here is a convenient map of service plans to endpoints.&#x20;

`429 (Too Many Requests)` The API Key's rate limit was exceeded; consider slowing down your API Request frequency if this is an HTTP request throttling error. Consider upgrading your service plan if you have reached your monthly API call credit limit for the day/month.&#x20;

`500 (Internal Server Error)` An unexpected server issue was encountered.
