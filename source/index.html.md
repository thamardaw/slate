---
title: API Reference

language_tabs:
  - api
  - android
  - laravel

toc_footers:
  - <a href='thamardaw.com'>Sign Up for Thamardaw</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the **THAMARDAW API!** You can use our API to access THAMARDAW API endpoints, which can get information on various pharmacy items, inventory, prices and transaction history in our database.

Thamardaw uses Dingo API package with JWT(JSON Web Token) on Laravel.

The Dingo API package is meant to provide you, the developer, with a set
of tools to help you easily and quickly build your own API.

We have sample language using this API in Java (Android), and Laravel! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation page was created with [Slate](https://github.com/tripit/slate).

# Authentication

Thamardaw uses API keys(JWT) to allow access to the API.

Thamardaw expects for the token key to be included in all API requests to the server.


## Sign Up


> returns JSON Response:

```json
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjExMiwiaXNzIjoiaHR0cDpcL1wvdG1kLWRldi50aGFtYXJkYXcuY29tXC9hcGlcL2F1dGhcL3NpZ251cCIsImlhdCI6MTQ5MzYyNDkzNiwiZXhwIjoxNDk0ODM0NTM2LCJuYmYiOjE0OTM2MjQ5MzYsImp0aSI6Ijc0ZWJjOWRiODBiYjBhODEzZWVkNzRlZDg3YjdlOTIzIn0.7fmIjspYMEX0bEyexpaiLPH0HO7HkYGCj5kg3_yuHDA",
  "user": {
    "id": "111",
    "name": "user",
    "email": "user@gmail.com",
    "type": "Buyer",
    "password": "$2y$10$f6DsO9FUtV7urCo1lt9VTex0zsGeNmACHf0CeIajfogAUsZDspPXu",
    "remember_token": null,
    "created_at": "2017-05-01 07:48:56",
    "updated_at": "2017-05-01 07:48:56",
    "address": "7/110, Pazundaung Township, Yangon",
    "phone": "09 250277385  "
  }
}
```
This endpoint retrieves registered user's information.

### HTTP Request

`POST http://tmd-dev.thamardaw.com/api/auth/signup`


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name | - | Type your name
email | - | Type your email
password | - | Type your password
type | - | Register as Buyer or Seller

<aside class="success">
Remember — a user can only register with single email account!
</aside>

## Log in

> returns JSON structured like this:

```json
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjk5LCJpc3MiOiJodHRwOlwvXC90bWQtZGV2LnRoYW1hcmRhdy5jb21cL2FwaVwvYXV0aFwvbG9naW4iLCJpYXQiOjE0OTM2Mjg4MzAsImV4cCI6MTQ5NDgzODQzMCwibmJmIjoxNDkzNjI4ODMwLCJqdGkiOiIwNzkzYjZlZTI2OGM2YmQ3YzBhY2RhNDdhMDdhYTk3MyJ9.NYgA_Xo29nqSwIp06cdpOvtoN4X0-QUPRqSvfQZoPa0",
  "user": {
    "id": "111",
    "name": "user",
    "email": "user@gmail.com",
    "type": "Buyer",
    "password": "$2y$10$EaELAgVbiv5XtXoc46a9fe8zFBcA68AMUjz/E6y76SYY/X5JsQaI6",
    "remember_token": null,
    "created_at": "2017-02-08 04:11:21",
    "updated_at": "2017-02-08 04:11:21",
    "address": "7/110,Pazundaung Tsp, Yangon",
    "phone": "09250277385"
  }
}
```

This endpoint retrieves token and user's information.

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
email | Type your email
password | Type your password

<aside class="notice">
You must replace <code>token</code> with your personal API key.
</aside>

# Items

## Get All Items

```API
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```API
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```laravel
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```
This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

# Item 

##Get All Item
<aside class="notice">
It will return all drug catalog items.
</aside>

###Routes : http://tmd-dev.thamardaw.com/api/item?token=x (GET)

###x=token logging from app
> returns JSON structured like this:
```json
[
  {
    "id": "1",
    "drug_code": "RegG60",
    "brand_name": "brandname",
    "generic_name": "genreir name",
    "strength_concentration": "500 Mg",
    "base_unit_of_measure": "Bottle",
    "purchase_order_unit_of_measure": "Box",
    "country_of_manufacture": "USA",
    "gross_weight": "50",
    "net_weight": "30",
    "weight_unit": "Gram",
    "size_dimension": "3cm x 3cm x 10cm",
    "description_en": "descriptoin",
    "created_at": "2016-08-07 09:58:02",
    "updated_at": "2016-08-07 09:58:25",
    "image_url": "jpg",
    "price": "7000",
    "category": null,
    "FDA_DRC_NO": null
  },
  ....
 ] 
```
##Search Item

<aside class="notice">
It will return all searched items.
</aside>

###Routes:http://tmd-dev.thamardaw.com/api/item/search/{str}?token=x (GET)
###x =token logging from app
##str = item name you want to search

##eg.http://tmd-dev.thamardaw.com/api/item/search/R?token=x
>return json structured like this
```json
[
  {
    "id": "1",
    "drug_code": "RegG60",
    "brand_name": "Redfdfdfdf",
    "generic_name": "genric",
    "strength_concentration": "500 Mg",
    "base_unit_of_measure": "Bottle",
    "purchase_order_unit_of_measure": "Box",
    "country_of_manufacture": "USA",
    "gross_weight": "50",
    "net_weight": "30",
    "weight_unit": "Gram",
    "size_dimension": "3cm x 3cm x 10cm",
    "description_en": "description",
    "created_at": "2016-08-07 09:58:02",
    "updated_at": "2016-08-07 09:58:25",
    "image_url": ".jpg",
    "price": "7000",
    "category": null,
    "FDA_DRC_NO": null
  },
  ...
 ] 

```

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

```API
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```laravel
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

# Inventory

> To check inventory, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```API
# With API, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```laravel
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>token</code> with your personal API key.
</aside>

# Transaction



## Transaction (Buyer)
<aside class="notice">

-It will store drug transaction detail in backend database.

</aside>
##Routes :http://tmd-dev.thamardaw.com/api/strTransaction?token=x 
##(POST)
##(x= token get from logging in app)
##(parameters :  drug_code, quantity, payment, discount,  bonus,  unit_price, total_price)

>return the json structured like this
```json


```

<aside class="notice">
	-It will return drug transaction detail made by that user from backend database.
</aside>

##Routes :http://tmd-dev.thamardaw.com/api/strTransaction?token=x (POST)
##parameters :user_id
##x=token get from logging in app

>return the json structured like this
```json


```


```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```API
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```laravel
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Transaction (Seller)
<aside>
   -It will return drug transaction detail of all users from backend database.
</aside>
###Routes :http://tmd-dev.thamardaw.com/api/TransactionBySeller?token=x 
###x= token get from logging in app
###parameter none

>return json structured like this
```json


```


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

```API
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```laravel
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

#Interaction(Seller)

<aside>
    -It will return all order/delivery/payment interaction status.
</aside>
##Routes :http://tmd-dev.thamardaw.com/api/InteractionBySeller?token=x (get)
##x = token get from logging in app
##parameter none

>return json structure like this

```json

```

<aside>
   -update all order/delivery/payment interaction status.
</aside>
##Routes :http://tmd-dev.thamardaw.com/api/updateOrderStatus?token=x (POST)
##x = token get from logging in app
##parameter none

>return json structure like this

```json

```

#pagnination

##for item catalog

<aside>
	-It will return limited item(eg.1 to 8-->8 item will return) 
</aside>

###Routes:http://tmd-dev.thamardaw.com/api/item/pagnination/{current}/{page}?token=x
###x=token logging from app
###current = start position(eg if 8 per page,current will start 0)
###page = end position(eg if 8 per page,page will start 8)

###eg http://tmd-dev.thamardaw.com/api/item/pagnination/0/8?token=x
>return json structure like this

```json
{
  "count": 19,
  "result": [
    {
      "id": "1",
      "drug_code": "RegG60",
      "brand_name": "Regenerix GOLD: Rapid Recovery",
      "generic_name": "generic",
      "strength_concentration": "500 Mg",
      "base_unit_of_measure": "Bottle",
      "purchase_order_unit_of_measure": "Box",
      "country_of_manufacture": "USA",
      "gross_weight": "50",
      "net_weight": "30",
      "weight_unit": "Gram",
      "size_dimension": "3cm x 3cm x 10cm",
      "description_en": "description",
      "created_at": "2016-08-07 09:58:02",
      "updated_at": "2016-08-07 09:58:25",
      "image_url": "rg1.jpg",
      "price": "7000",
      "category": null,
      "FDA_DRC_NO": null
    },
    ...
 }   
```
##for interactionBySeller

<aside>
    -It will return all order/delivery/payment interaction status.
</aside>
###Routes:http://tmd-dev.thamardaw.com/api/interactionBySeller/pagination/{current}/{page}?token=x
###x=token logging from app
###current = start position(eg if 8 per page,current will start 0)
###page = end position(eg if 8 per page,page will start 8)

###eg http://tmd-dev.thamardaw.com/api/interactionBySeller/pagination/0/8?token=x
>return json structure like this
```json
{
  "interaction": [
    {
      "phone": "999",
      "address": "Home",
      "name": "MichaelMaung",
      "id": "108",
      "user_id": "127",
      "tr_doc_no": "dfdf",
      "order_status": "order status",
      "delivery_status": null,
      "payment_status": null,
      "drug_code": null,
      "created_at": "2017-05-07 04:52:11",
      "updated_at": "2017-05-07 04:52:11"
    },
    ....
 ]   
```
##for transactionbyseller

<aside>
   -It will return drug transaction detail of all users from backend database.
</aside>

###Routes:http://tmd-dev.thamardaw.com/api/transactionBySeller/pagination/{current}/{page}?token=x
###x=token logging from app
###current = start position(eg if 8 per page,current will start 0)
###page = end position(eg if 8 per page,page will start 8)

###eg http://tmd-dev.thamardaw.com/api/transactionBySeller/pagination/0/8?token=x
>return json structure like this
```json
{
  "transaction": [
    {
      "id": "number",
      "user_id": null,
      "username": null,
      "tr_doc_no": "no",
      "tr_item_no": "1",
      "drug_code": null,
      "description_": null,
      "quantity": null,
      "base_uom": null,
      "trans_uom": null,
      "payment": null,
      "discount": null,
      "bonus": null,
      "unit_price": null,
      "total_price": null,
      "created_at": "2017-05-07 07:44:39",
      "updated_at": "2017-05-07 07:44:39"
    },

    ....
 ]   
```
	



