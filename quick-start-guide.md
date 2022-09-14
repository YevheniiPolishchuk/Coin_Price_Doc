# Quick Start Guide

For developers eager to hit the ground running with the CPAY Rates API here are a few quick steps to make your first call with the API.

1. **Sign up.** You can sign up at [coinprice.cpay.world](https://coinprice.cpay.world/) - This is our live production environment with the latest market data. Select the free `Basic` plan if it meets your needs or upgrade to a paid tier.&#x20;
2. **Copy your API key.** After registration, you will be taken to the main page of your account. Copy your API key from the `API Key` field from the API Key section.
3. **Make a test call using your key.** You may use the code examples provided below to make a test call with your programming language of choice.This example retrieves the AAVEBTC exchange rate history for one day within an hour. Be sure to replace the API key in the sample code with your own and use the `api.rates.cpay.world/ex` API domain. Please note that our sandbox API contains mock data and should not be used in your application.
4. **Implement your application.** Now that you've confirmed your API Key is working, get familiar with the API by reading the rest of this API Reference and commence building your application!

<details>

<summary>cURL command line</summary>

curl --location --request GET 'https://api.rates.cpay.world/ex/api/exchanges/history?symbol=AAVEBTC\&from=2022-02-02 14:12:10\&to=2022-02-03 14:12:10\&interval=hourly\&exchangeId=1'\
\--header 'x-exchange-api-key: Z300BHR-WT6MPRZ-PEHNBZ8-9SGXK91'

</details>

<details>

<summary>Node.js</summary>

```javascript
/* Example in Node.js */
const axios = require('axios');

let response = null;
new Promise(async (resolve, reject) => {
  try {
    response = await axios.get('https://api.rates.cpay.world/ex/api/exchanges/history?symbol=AAVEBTC&from=2022-02-02 14:12:10&to=2022-02-03 14:12:10&interval=hourly&exchangeId=1', {
      headers: {
        'x-exchange-api-key': 'Z300BHR-WT6MPRZ-PEHNBZ8-9SGXK91',
      },
    });
  } catch(ex) {
    response = null;
    // error
    console.log(ex);
    reject(ex);
  }
  if (response) {
    // success
    const json = response.data;
    console.log(json);
    resolve(json);
  }
});
```

</details>

<details>

<summary>Python</summary>

```python
#This example uses Python 2.7 and the python-request library.

from requests import Request, Session
from requests.exceptions import ConnectionError, Timeout, TooManyRedirects
import json

url = 'https://api.rates.cpay.world/ex/api/exchanges/history'
parameters = {
  'symbol':'AAVEBTC',
  'from':'2022-02-02 14:12:10',
  'to':'2022-02-03 14:12:10',
  'interval':'hourly',
  'exchangeId':'1',
}
headers = {
  'Accepts': 'application/json',
  'x-exchange-api-key': 'Z300BHR-WT6MPRZ-PEHNBZ8-9SGXK91',
}

session = Session()
session.headers.update(headers)

try:
  response = session.get(url, params=parameters)
  data = json.loads(response.text)
  print(data)
except (ConnectionError, Timeout, TooManyRedirects) as e:
  print(e)
  
```

</details>

<details>

<summary>PHP</summary>

```php
/**
 * Requires curl enabled in php.ini
 **/

<?php
$url = 'https://api.rates.cpay.world/ex/api/exchanges/history';
$parameters = [
  'symbol' => 'AAVEBTC',
  'from' => '2022-02-02 14:12:10',
  'to' => '2022-02-03 14:12:10',
  'interval' => 'hourly',
  'exchangeId' => '1'
];

$headers = [
  'Accepts: application/json',
  'x-exchange-api-key: Z300BHR-WT6MPRZ-PEHNBZ8-9SGXK91'
];
$qs = http_build_query($parameters); // query string encode the parameters
$request = "{$url}?{$qs}"; // create the request URL


$curl = curl_init(); // Get cURL resource
// Set cURL options
curl_setopt_array($curl, array(
  CURLOPT_URL => $request,            // set the request URL
  CURLOPT_HTTPHEADER => $headers,     // set the headers 
  CURLOPT_RETURNTRANSFER => 1         // ask for raw response instead of bool
));

$response = curl_exec($curl); // Send the request, save the response
print_r(json_decode($response)); // print json decoded response
curl_close($curl); // Close request
?>
```

\


</details>

<details>

<summary>Java</summary>

```java
/** 
 * This example uses the Apache HTTPComponents library. 
 */

import org.apache.http.HttpEntity;
import org.apache.http.HttpHeaders;
import org.apache.http.NameValuePair;
import org.apache.http.client.methods.CloseableHttpResponse;
import org.apache.http.client.methods.HttpGet;
import org.apache.http.client.utils.URIBuilder;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.message.BasicNameValuePair;
import org.apache.http.util.EntityUtils;

import java.io.IOException;
import java.net.URISyntaxException;
import java.util.ArrayList;
import java.util.List;

public class JavaExample {

  private static String apiKey = "Z300BHR-WT6MPRZ-PEHNBZ8-9SGXK91";

  public static void main(String[] args) {
    String uri = "https://api.rates.cpay.world/ex/api/exchanges/history";
    List<NameValuePair> paratmers = new ArrayList<NameValuePair>();
    paratmers.add(new BasicNameValuePair("symbol","AAVEBTC"));
    paratmers.add(new BasicNameValuePair("from","2022-02-02 14:12:10"));
    paratmers.add(new BasicNameValuePair("to","2022-02-03 14:12:10"));
    paratmers.add(new BasicNameValuePair("interval","hourly"));
    paratmers.add(new BasicNameValuePair("exchangeId","1"));

    try {
      String result = makeAPICall(uri, paratmers);
      System.out.println(result);
    } catch (IOException e) {
      System.out.println("Error: cannont access content - " + e.toString());
    } catch (URISyntaxException e) {
      System.out.println("Error: Invalid URL " + e.toString());
    }
  }

  public static String makeAPICall(String uri, List<NameValuePair> parameters)
      throws URISyntaxException, IOException {
    String response_content = "";

    URIBuilder query = new URIBuilder(uri);
    query.addParameters(parameters);

    CloseableHttpClient client = HttpClients.createDefault();
    HttpGet request = new HttpGet(query.build());

    request.setHeader(HttpHeaders.ACCEPT, "application/json");
    request.addHeader("x-exchange-api-key", apiKey);

    CloseableHttpResponse response = client.execute(request);

    try {
      System.out.println(response.getStatusLine());
      HttpEntity entity = response.getEntity();
      response_content = EntityUtils.toString(entity);
      EntityUtils.consume(entity);
    } finally {
      response.close();
    }

    return response_content;
  }

}
```

</details>

<details>

<summary>C#</summary>

```csharp
using System;
using System.Net;
using System.Web;

class CSharpExample
{
  private static string API_KEY = "Z300BHR-WT6MPRZ-PEHNBZ8-9SGXK91";

  public static void Main(string[] args)
  {
    try
    {
    Console.WriteLine(makeAPICall());
    }
    catch (WebException e)
    {
    Console.WriteLine(e.Message);
    }
  }

  static string makeAPICall()
  {
    var URL = new UriBuilder("https://api.rates.cpay.world/ex/api/exchanges/history");

    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString["symbol"] = "AAVEBTC";
    queryString["from"] = "2022-02-02 14:12:10";
    queryString["to"] = "2022-02-03 14:12:10";
    queryString["interval"] = "hourly";
    queryString["exchangeId"] = "1";

    URL.Query = queryString.ToString();

    var client = new WebClient();
    client.Headers.Add("x-exchange-api-key", API_KEY);
    client.Headers.Add("Accepts", "application/json");
    return client.DownloadString(URL.ToString());

  }

}
 
```

</details>

<details>

<summary>Go</summary>



```go
package main

import (
  "fmt"
  "io/ioutil"
  "log"
  "net/http"
  "net/url"
  "os"
)

func main() {
  client := &http.Client{}
  req, err := http.NewRequest("GET","https://api.rates.cpay.world/ex/api/exchanges/history", nil)
  if err != nil {
    log.Print(err)
    os.Exit(1)
  }

  q := url.Values{}
  q.Add("symbol", "AAVEBTC")
  q.Add("from", "2022-02-02 14:12:10")
  q.Add("to", "2022-02-03 14:12:10")
  q.Add("interval", "hourly")
  q.Add("exchangeId", "1")

  req.Header.Set("Accepts", "application/json")
  req.Header.Add("x-exchange-api-key", "Z300BHR-WT6MPRZ-PEHNBZ8-9SGXK91")
  req.URL.RawQuery = q.Encode()


  resp, err := client.Do(req);
  if err != nil {
    fmt.Println("Error sending request to server")
    os.Exit(1)
  }
  fmt.Println(resp.Status);
  respBody, _ := ioutil.ReadAll(resp.Body)
  fmt.Println(string(respBody));

}
```

\


</details>
