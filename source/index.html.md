---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Coin Match API! You can use our API to access cryptocurrency API endpoints and exchange API endpoints, which can get information on various coins, exchanges, and transactions in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation page was created with [Slate](https://github.com/lord/slate).


# Authentication

> To authorize, use this code:

```ruby
require 'coin_match'

api = coin_match::APIClient.authorize!('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
```

```python
import coin_match

api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD"
```

```javascript
const coin_match = require('coin_match');

let api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD');
```

> Make sure to replace `vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD` with your personal token.

Coin Match uses token-based authentication to allow access to the API. You can register a new user account at our [developer portal](http://example.com/developers). Tokens can be obtained by posting username and password via form-data to <code>/get-token</code>.

Coin Match expects the token to be included in all API requests to the server in a header that looks like the following:

`Authorization: vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD`

<aside class="notice">
You must replace <code>vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD</code> with your personal token.
</aside>

# CryptoCurrencies

## Get All CryptoCurrencies

```ruby
require 'coin_match'

api = coin_match::APIClient.authorize!('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.cryptocurrencies.get
```

```python
import coin_match

api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.cryptocurrencies.get()
```

```shell
curl "http://example.com/api/cryptocurrency"
  -H "Authorization: vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD"
```

```javascript
const coin_match = require('coin_match');

let api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD');
let cryptocurrencies = api.cryptocurrencies.get();
```

> The above command returns JSON structured like this:

```json
[
  {
      "name": "Bitcoin",
      "owner": "admin",
      "abbreviation": "BTC",
      "symbol": "₿",
      "supply_limit": 210000000,
      "founder": "Satoshi Nakatomo",
      "created_at": "2018-07-24T16:32:32.775971Z",
      "updated_at": "2018-07-24T16:32:32.776030Z",
      "trade": []
  },
  {
      "name": "Ethereum",
      "owner": "admin",
      "abbreviation": "ETH",
      "symbol": "Ξ",
      "supply_limit": 120204432,
      "founder": "Vitalik Buterin",
      "created_at": "2018-07-24T16:32:59.682815Z",
      "updated_at": "2018-07-24T16:32:59.682905Z",
      "trade": []
  }
]
```

This endpoint retrieves all CryptoCurrencies.

### HTTP Request

`GET http://example.com/api/cryptocurrencies`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy coin is an authenticated coin!
</aside>

## Get a Specific CryptoCurrency

```ruby
require 'coin_match'

api = coin_match::APIClient.authorize!('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.cryptocurrencies.get(2)
```

```python
import coin_match

api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.cryptocurrencies.get(2)
```

```shell
curl "http://example.com/api/cryptocurrency/2"
  -H "Authorization: vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD"
```

```javascript
const coin_match = require('coin_match');

let api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD');
let max = api.cryptocurrencies.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "name": "Bitcoin",
  "owner": "admin",
  "abbreviation": "BTC",
  "symbol": "₿",
  "supply_limit": 210000000,
  "founder": "Satoshi Nakatomo",
  "created_at": "2018-07-24T16:32:32.775971Z",
  "updated_at": "2018-07-24T16:32:32.776030Z",
  "trade": []
}
```

This endpoint retrieves a specific CryptoCurrency.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/cryptocurrency/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the CryptoCurrency to retrieve

## Delete a Specific CryptoCurrency

```ruby
require 'coin_match'

api = coin_match::APIClient.authorize!('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.cryptocurrencies.delete(2)
```

```python
import kittn

api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.cryptocurrencies.delete(2)
```

```shell
curl "http://example.com/api/cryptocurrency/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.cryptocurrencys.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific CryptoCurrency.

### HTTP Request

`DELETE http://example.com/cryptocurrency/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the CryptoCurrency to delete

# Exchanges

## Get All Exchanges

```ruby
require 'coin_match'

api = coin_match::APIClient.authorize!('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.exchanges.get
```

```python
import coin_match

api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.exchanges.get()
```

```shell
curl "http://example.com/api/exchange"
  -H "Authorization: vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD"
```

```javascript
const coin_match = require('coin_match');

let api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD');
let exchanges = api.exchanges.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "name": "Cex.io",
    "owner": "admin",
    "buy_fee": "0.25%",
    "sell_fee": "0.16%",
    "desc": "The exchange has developed a multi-level account system with individual approach to each customer,
    from Bitcoin beginners to institutional traders. Worldwide coverage, multiple payment options, and 24/7
    support are accompanied by time-proven platform stability that guarantees safety of assets and data.",
    "products": [
        1,
        2,
        4,
        5,
        6
    ],
    "created_at": "2018-07-24T16:43:16.699539Z",
    "updated_at": "2018-07-24T17:14:27.916056Z",
    "past_trades": []
  },
  {
    "name": "Coinbase",
    "owner": "admin",
    "buy_fee": "1.49%",
    "sell_fee": "1.49%",
    "desc": "Founded in June of 2012, Coinbase is a digital currency wallet and platform where merchants and consumers
    can transact with new digital currencies like bitcoin, ethereum, and litecoin. We're based in San Francisco,
    California.",
    "products": [
        1,
        2,
        3,
        4
    ],
    "created_at": "2018-07-24T16:52:42.503987Z",
    "updated_at": "2018-07-24T17:14:45.123085Z",
    "past_trades": []
  }
]
```

This endpoint retrieves all Exchanges.

### HTTP Request

`GET http://example.com/api/exchanges`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy exchange is an authenticated exchange!
</aside>

## Get a Specific Exchange

```ruby
require 'coin_match'

api = coin_match::APIClient.authorize!('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.exchanges.get(2)
```

```python
import coin_match

api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.exchanges.get(2)
```

```shell
curl "http://example.com/api/exchanges/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const coin_match = require('coin_match');

let api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD');
let max = api.exchanges.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "name": "Cex.io",
  "owner": "admin",
  "buy_fee": "0.25%",
  "sell_fee": "0.16%",
  "desc": "The exchange has developed a multi-level account system with individual approach to each customer,
  from Bitcoin beginners to institutional traders. Worldwide coverage, multiple payment options, and 24/7 support
  are accompanied by time-proven platform stability that guarantees safety of assets and data.",
  "products": [
      1,
      2,
      4,
      5,
      6
  ],
  "created_at": "2018-07-24T16:43:16.699539Z",
  "updated_at": "2018-07-24T17:14:27.916056Z",
  "past_trades": []
}
```

This endpoint retrieves a specific Exchange.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/exchange/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Exchange to retrieve

## Delete a Specific Exchange

```ruby
require 'coin_match'

api = coin_match::APIClient.authorize!('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.exchanges.delete(2)
```

```python
import coin_match

api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD')
api.exchanges.delete(2)
```

```shell
curl "http://example.com/api/exchange/2"
  -X DELETE
  -H "Authorization: vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD"
```

```javascript
const coin_match = require('coin_match');

let api = coin_match.authorize('vK5GzgXlI73UjuoR37hpZAXcfeyAV38XXfvzPvPD');
let max = api.exchanges.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific Exchange.

### HTTP Request

`DELETE http://example.com/exchange/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the Exchange to delete

