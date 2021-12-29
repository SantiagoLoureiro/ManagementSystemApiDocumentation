# Management system - API. v1

## Authentication

```
Url : /auth/login  method: POST  

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
| channel_pricing      | price associated with the channel to which it updates     |
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

## Set WebHook Orders
```
Url : /orders/set-webhook  method: POST  

Header with authentication is needed

request: 

{
    "url": String ,
}

response: Status code 200 is OK
{
    
}
```

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
[ 
   
       'order': string,
       'payment_details': Array {
            'client_id': String,
            'dni': String,
            'email': String,
            'total': Integer,
            'currency_code': String,
            'payment_method': String,
       },
       'billing_address': Array {
            'first_name': String,
            'last_name': String,
            'address': String,
            'postal_code': String,
            'city': String,
            'province_or_departament': String,
            'country': String,
            'phone_number': String,
            'company': String,
            'email': String,
            'dni': String,
        },
       'shipping_address': Array {
            'first_name': String,
            'last_name': String,
            'address': String,
            'postal_code': String,
            'city': String,
            'province_or_departament': String,
            'country': String,
            'phone_number': String,
            'email': String,
       },
       'items': Array {
            'id': String,
            'variant_name': String,
            'amount': Float,
            'unit_price': Float,
            'subtotal': Float,
            'description': String,
            'code_variant': String,
            'price_whit_discount': Float,
            'dto': Float
       }
]

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

