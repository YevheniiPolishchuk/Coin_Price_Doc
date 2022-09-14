# Authentication

**Acquiring an API Key** \
All HTTP requests made against the CPAY Coin Price API must be validated with an API Key. If you don't have an API Key yet visit the [https://rates.cpay.world/](https://coinprice.cpay.world/) to register for one.

**Using Your API Key** \
You may use any server side programming language that can make HTTP requests to target the CPAY Coin Price API. All requests should target domain `https://api.rates.cpay.world/ex`.

You can supply your API Key in REST API calls via a custom header named `x-exchange-api-key`.

#### API Key Usage Credits

Most API plans include a daily and monthly limit or "hard cap" to the number of data calls that can be made. This usage is tracked as API "call credits" which are incremented 1:1 against successful (HTTP Status 200) data calls made with your key with these exceptions: account management endpoints and error responses are not included in this limit.

You can log in to the[ ](https://coinprice.cpay.world/)[https://coinprice.cpay.world/](https://coinprice.cpay.world/) to view live stats on your API Key usage and limits including the number of credits used for each call.

**Note:** _The "day" and "month" credit usage periods are determined relative to your API subscription. For example, if you purchased a plan on January 5 at 06:00 am, then the next time you need to re-purchase the plan on February 5 at 06:00 am, otherwise you will be moved back to the Basic plan. The next day starts on February 6 at 06:00 am, credits are reset accordingly._
