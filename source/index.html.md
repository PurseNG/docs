---
title: API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to our simple-to-use REST APIs, accepting payments in your applications with Purse is a only a request or two away. To get started, grab yourself a [free merchant account](https://purse.ng/register) you can test the endpoints against. Once you are logged into your account, you would have access to a test key so you can start making API requests with no further ado.

The sample requests shown here are made with [cURL](http://curl.haxx.se/) but you can make use of any HTTP client to test our endpoints. An easy pick to quickly start making API calls would be [POSTMAN](https://chrome.google.com/webstore/detail/postman-rest-client/fdmmgilgnpjigdojojpjoooidkmcomcm/), an awesome Chrome extension we love to use ourselves.

Both request body data and response data are formatted as JSON. Content type for responses will always be application/json.

# Authentication

To get authenticated on Purse, please include your API key in the Authorization header of every request you make to our endpoints.

> All you need to do is format your request header like:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Purse g4Cbu09M75w1kEYIKHRmXaRCINxglbR1uWkXyg1X"
```

> Make sure to replace `g4Cbu09M75w1kEYIKHRmXaRCINxglbR1uWkXyg1X` with your API key.

`Authorization: Purse g4Cbu09M75w1kEYIKHRmXaRCINxglbR1uWkXyg1X`

<aside class="notice">
You must replace <code>g4Cbu09M75w1kEYIKHRmXaRCINxglbR1uWkXyg1X</code> with your personal API key.
</aside>

# Invoices

## Create an Invoice


```shell
curl "https://staging.purse.ng/invoices" \
-H "Authorization: Purse API_KEY" \
-H "Content-Type: application/json" \
-d '{
  "customerCountryCode":"234",
  "customerPhoneNumber":"08052000000",
  "narration":"Coffee Payment",
  "totalAmount":3000
}' \ 
-X POST
```

> The above command returns JSON structured like this:

```json
{
  "code": "00",
  "message": "Hi, you are new with Purse. Please dial *206*4040#(GLO, ETISALAT, AIRTEL) or *510*4040#(MTN) to opt-in and authenticate this transaction.",
  "invoiceRef": "928397da-1ed1-11e7-bff5-0a80cc3ac5be"
}
```

> "message" fro above should be displayed to your customer to give direction on how to approve the invoice.

This endpoint creates an invoice on Purse.

### HTTP Request

`POST http://staging.purse.ng/api/invoices`

### Post Parameters

Parameter | Description
--------- | ------- 
walletMsisdn | Customer's ID on Purse.
narration | A description for the charge/transaction.
totalAmount | Total amount to charge in naira.


<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

