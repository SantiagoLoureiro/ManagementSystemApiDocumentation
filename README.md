# Management system - API. v1

## Authenticacion

```
Url : /auth/login  method: POST  

Header with authentication is needed

request: 

{
    "username": String,
    "password": String,
}

response: 

{
    "token": String,
}

Header for endpoint with authentication

{
    "Authorization": token_value,
}

```

| Field  | Description |
| ------------- |:-------------:|
| username      | easycommerce user      |
| password      | easycommerce password     |




## Get Variants

```
Url : /variant/get-variants  method: GET  

Header with authentication is needed

request: 

    {
        variant_code: String = Null
    }

Response: 

    {
        "variant_code": String,
        "stock": Int,
        "channel_pricing" : array [
                price: Float,
                code: String
            ]
        "weight": Float 
    }

```

| Field  | Description |
| ------------- |:-------------:|
| variant_code      | easycommerce variant code      |
| stock      | single stock of variant     |
| channel      | price associated with the channel to which it updates     |
| weight      | variant weight     |


## Variant update

```
Url : /variant/update  method: POST  

Header with authentication is needed

request: 

{
    "variant_code": String,
    "stock": Int = Null,
    "channel_pricing" : array [
            price: Float,
            code: String
        ] = Null
    "weight": Float = Null
}

```

| Field  | Description |
| ------------- |:-------------:|
| variant_code      | easycommerce variant code      |
| stock      | single stock of variant     |
| channel_pricing      | price associated with the channel to which it updates     |
| weight      | variant weight     |


## Get Orders

```
Url : /orders/generate-orders  method: POST  

Header with authentication is needed

request: 

{
    "date_from": Datetime = Null,
    "date_to": Datetime = Null,
    "order_id": String
}

response: 
{
   
    [Working on this section]
    
}

```

| Field  | Description |
| ------------- |:-------------:|
| date_from      | order start date       |
| date_to      | order end date     |
| order_id      | easycommerce order id    |


## Get Orders IDS

```
Url : /orders/generate-orders/ids  method: POST  

Header with authentication is needed

request: 

{
    "date_from": Datetime = Null,
    "date_to": Datetime = Null,
    "order_id": String
}

response

{
    ids: Array [String]
}

```

| Field  | Description |
| ------------- |:-------------:|
| date_from      | order start date       |
| date_to      | order end date     |
| order_id      | easycommerce order id    |

