---
description: You can integrate the Api key into your system and then use the public api.
---

# Using the public API

{% swagger method="get" path="/api/exchanges/list" baseUrl="https://api.rates.cpay.world/ex" summary="Getting a list of available exchanges" %}
{% swagger-description %}
This endpoint allows you to get a list of all available exchanges, the Ids of which should be used in other requests.
{% endswagger-description %}

{% swagger-parameter in="query" name="search" type="String" %}
Search by exchange name
{% endswagger-parameter %}

{% swagger-parameter in="query" name="order" type="String" %}
Available values : ASC, DESC. Default value : ASC
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {
    "page": 0,
    "pages": 0,
    "countItems": 0,
    "entities": [
      {
        "id": 0,
        "name": "string",
        "slug": "string",
        "isActive": true,
        "firstHistoricalData": "string",
        "lastHistoricalData": "string"
      }
    ]
  }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}
```javascript
{
    "status": "fail",
    "data": {
        "message": "Unauthorized"
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/exchanges/pairs" baseUrl="https://api.rates.cpay.world/ex" summary="Getting cryptocurrency pairs on the selected exchange" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" required="true" name="exchangeId" type="String" %}
This parameter is the exchange Id that we get in the response to the GET /api​/exchanges​/list endpoint
{% endswagger-parameter %}

{% swagger-parameter in="query" name="search" type="String" %}
Search by crypto pair
{% endswagger-parameter %}

{% swagger-parameter in="query" name="order" type="String" %}
Available values : ASC, DESC. Default value : ASC
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-exchange-api-key" type="String" required="true" %}
We get the value of this parameter in the API Key block after log in to https://rates.cpay.world/
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {
    "page": 0,
    "pages": 0,
    "countItems": 0,
    "entities": [
      {
        "id": 0,
        "symbol": "string",
        "baseAsset": "string",
        "quoteAsset": "string",
        "price": 0,
        "volumeBaseAsset": 0,
        "volumeQuoteAsset": 0,
        "firstHistoricalData": "string",
        "lastHistoricalData": "string"
      }
    ]
  }
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}
```javascript
{
    "status": "fail",
    "data": {
        "message": "Unauthorized"
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="" %}
```javascript
{
    "status": "fail",
    "data": {
        "message": "Exchange not found."
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/exchanges/convert" baseUrl="https://api.rates.cpay.world/ex" summary="Cryptocurrency conversion" %}
{% swagger-description %}
This endpoint allows you to convert cryptocurrency to cryptocurrency, fiat currency to cryptocurrency, cryptocurrency to fiat currency, and fiat currency to fiat currency.
{% endswagger-description %}

{% swagger-parameter in="query" required="true" name="from" type="String" %}
Parameter containing which currency the conversion is being performed from
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to" required="true" type="String" %}
Parameter containing which currency the conversion is being performed to
{% endswagger-parameter %}

{% swagger-parameter in="query" name="exchangeId" type="String" required="true" %}
This parameter is the exchange Id that we get in the response to the GET /api​/exchanges​/list endpoint
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-exchange-api-key" type="String" %}
We get the value of this parameter in the API Key block after log in to https://rates.cpay.world/
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {
    "price": 0
  }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
```javascript
{
    "status": "fail",
    "data": {
        "message": "Pair not support."
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="" %}
```javascript
{
    "status": "fail",
    "data": {
        "message": "Unauthorized"
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/exchanges/history" baseUrl="https://api.rates.cpay.world/ex" summary="History of cryptocurrency pairs rates" %}
{% swagger-description %}
This endpoint returns the exchange rate history for the selected pair
{% endswagger-description %}

{% swagger-parameter in="query" name="symbol" type="String" required="true" %}
This parameter contains a crypto pair, the list of which can be obtained in the server response via the GET /api​/exchanges​/pairs endpoint
{% endswagger-parameter %}

{% swagger-parameter in="query" name="from" type="String" required="true" %}
This parameter contains the date and time from which the course history should be returned. 

_Example_

 : 2021-03-01 14:12:10
{% endswagger-parameter %}

{% swagger-parameter in="query" name="to" type="String" required="true" %}
This parameter contains the date and time to which the course history should be returned. 

_Example_

 : 2021-03-01 14:12:10
{% endswagger-parameter %}

{% swagger-parameter in="query" name="interval" type="String" required="true" %}
This parameter contains the interval with which you want to return the exchange rate history for the selected pair. Available values : hourly, daily, weekly, monthly. Default value: hourly.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="exchangeId" type="String" required="true" %}
This parameter is the exchange Id that we get in the response to the GET /api​/exchanges​/list endpoint
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-exchange-api-key" type="String" required="true" %}
We get the value of this parameter in the API Key block after log in to https://rates.cpay.world/
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": [
    {
      "symbol": "string",
      "baseAsset": "string",
      "quoteAsset": "string",
      "timestamp": "string",
      "price": 0,
      "volumeBaseAsset": 0,
      "volumeQuoteAsset": 0
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}
```javascript
{
    "status": "fail",
    "data": {
        "message": "Unauthorized"
    }
}
```
{% endswagger-response %}

{% swagger-response status="404: Not Found" description="" %}
```javascript
{
    "status": "fail",
    "data": {
        "message": "Exchange not found."
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/api/public/assets/list" baseUrl="https://api.rates.cpay.world/ex" summary="List of cryptocurrencies with price, marketCap and etc.." %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="search" type="String" required="false" %}
Search by cryptocurrency symbol
{% endswagger-parameter %}

{% swagger-parameter in="query" name="order" type="String" %}
Available values : ASC, DESC. Default value : ASC
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
  "data": {
    "page": 0,
    "pages": 0,
    "countItems": 0,
    "entities": [
      {
        "id": 0,
        "symbol": "string",
        "baseAsset": "string",
        "quoteAsset": "string",
        "price": 0,
        "volumeBaseAsset": 0,
        "volumeQuoteAsset": 0,
        "marketCap": 0,
        "circulatingSupply": 0,
        "change24H": 0,
        "change24HPercent": 0,
        "history7D": [
          {
            "symbol": "string",
            "baseAsset": "string",
            "quoteAsset": "string",
            "timestamp": "string",
            "price": 0,
            "volumeBaseAsset": 0,
            "volumeQuoteAsset": 0
          }
        ]
      }
    ]
  }
}
```
{% endswagger-response %}
{% endswagger %}
