---
title: API Reference

language_tabs:
  - api
  - android
  - laravel

toc_footers:
  - <a href='thamardaw.com'>Sign Up for Thamardaw</a>

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
This endpoint will retrieves registered user's information.

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

`POST http://tmd-dev.thamardaw.com/api/auth/login`

### URL Parameters

Parameter | Description
--------- | -----------
email | Type your email
password | Type your password


# Items

##Get All Items
<aside class="notice">
It will return all drug catalog items.
</aside>


### HTTP Request

`GET http://tmd-dev.thamardaw.com/api/item?token=x`


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token


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
  }
  
 ] 
```

##Get All Items (Pagination)

<aside>
  -It will return limited item(eg.1 to 8-->8 item will return) 
</aside>

### HTTP Request

`GET http://tmd-dev.thamardaw.com/api/item/pagnination/{current}/{page}?token=x`

`eg. GET http://tmd-dev.thamardaw.com/api/item/pagnination/0/8?token=x`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
current | - | start position(eg if 8 per page,current will start 0)
page | - | end position(eg if 8 per page,page will start 8)

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
    }
    
 }   
```

##Search Items

<aside class="notice">
It will return all searched items.
</aside>

### HTTP Request

`GET http://tmd-dev.thamardaw.com/api/item/search/{str}?token=x`

`eg. GET http://tmd-dev.thamardaw.com/api/item/search/R?token=x`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
str | - | item name you want to search 

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
  
 ] 

```


# Inventory

##Get Item Inventory
<aside class="notice">
It will return inventory information of selected item.
</aside>


### HTTP Request

`POST http://tmd-dev.thamardaw.com/api/inventory?token=x`


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
drug_code | - | item drug code


> returns JSON structured like this:

```json
{
  "inventory": {
    "id": "1",
    "drug_code": "RegG60",
    "description": null,
    "quantity": "18",
    "base_uom": null,
    "unit_price": null,
    "average_price": "7000.00",
    "lead_time": "3 Day",
    "created_at": null,
    "updated_at": "2016-09-11 10:33:25"
  }
}
```
##Check Inventory

<aside class="notice">
It will return all searched items.
</aside>

### HTTP Request

`POST http://tmd-dev.thamardaw.com/api/inventoryCheck?token=x`


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
drug_code | - | item drug code
quantity | - | order quantity

>return json structured like this

```json
{"status":"valid","responseMessage":"succeed"} or
{"status":"invalid","responseMessage":"We do not have enough stock"}
```

# Transaction

##Send Order Transaction (Buyer)

<aside class="notice">
It will send order information to server and will generate order number.
</aside>

### HTTP Request

`POST tmd-dev.thamardaw.com/api/strTransaction?token=x`


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
user_id | - | user ID generated by system
username | - | username
drug_code | - | item drug code
quantity | - | order quantity
payment | - | order payment
discount | - | discount
bonus | - | item bonus
unit_price | - | unit price
total_price | - | total price

>return json structured like this

```json
{
  "order_no": "ORD000001"
}
```

## Transaction (Buyer)
<aside>
   -It will return drug transaction detail of all users from backend database.
</aside>

### HTTP Request

`POST http://tmd-dev.thamardaw.com/api/transaction/pagination/{current}/{page}?token=x`

`eg. GET http://tmd-dev.thamardaw.com/api/transaction/pagination/0/8?token=x`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
current | - | start position(eg if 8 per page,current will start 0)
page | - | end position(eg if 8 per page,page will start 8)
user_id | - | user ID

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
    }, {....},

    
 ]   
```


## Transaction (Seller)

<aside>
   -It will return drug transaction detail of all users from backend database.
</aside>

### HTTP Request

`GET http://tmd-dev.thamardaw.com/api/transactionBySeller/pagination/{current}/{page}?token=x`

`eg. GET http://tmd-dev.thamardaw.com/api/transactionBySeller/pagination/0/8?token=x`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
current | - | start position(eg if 8 per page,current will start 0)
page | - | end position(eg if 8 per page,page will start 8)

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
    }, {....},

    
 ]   
```

#Interaction

##Interaction (Buyer)
<aside>
    -It will return all order/delivery/payment interaction status of orders.
</aside>

### HTTP Request

`GET http://tmd-dev.thamardaw.com/api/interaction/{current}/{page}?token=x`

`eg. GET http://tmd-dev.thamardaw.com/api/interaction/0/8?token=x`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
current | - | start position(eg if 8 per page,current will start 0)
page | - | end position(eg if 8 per page,page will start 8)
>return json structure like this

```json
{
  "interaction": [
    {
      "phone": "09 123456",
      "address": "12/34 Botahtaung Township, Yangon",
      "name": "Username",
      "id": "108",
      "user_id": "1",
      "tr_doc_no": "ORD000001",
      "order_status": "Order Processed",
      "delivery_status": null,
      "payment_status": null,
      "drug_code": null,
      "created_at": "2017-05-07 04:52:11",
      "updated_at": "2017-05-07 04:52:11"
    }, {....},
    
  ]   
 }
```

##Interaction (Seller)
<aside>
    -It will return all order/delivery/payment interaction status.
</aside>

### HTTP Request

`GET http://tmd-dev.thamardaw.com/api/interactionBySeller/pagination/{current}/{page}?token=x`

`eg. GET http://tmd-dev.thamardaw.com/api/interactionBySeller/pagination/0/8?token=x`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
x | - | Token
current | - | start position(eg if 8 per page,current will start 0)
page | - | end position(eg if 8 per page,page will start 8)
>return json structure like this

```json
{
  "interaction": [
    {
      "phone": "09 123456",
      "address": "12/34 Botahtaung Township, Yangon",
      "name": "Username",
      "id": "108",
      "user_id": "1",
      "tr_doc_no": "ORD000001",
      "order_status": "Order Processed",
      "delivery_status": null,
      "payment_status": null,
      "drug_code": null,
      "created_at": "2017-05-07 04:52:11",
      "updated_at": "2017-05-07 04:52:11"
    }, {....},
    
  ]   
 }
```
