# Management system - API. v1

## Authentication

```
Url : /api-token-auth/  method: POST  

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

## -----------------VARIANTS-----------------


## Get One Variant

```
Url : service/variants  method: GET  

Header with authentication is needed

request: 

    {
        "variant_id": String
    }

Response: 

    [
        {
            "width": Integer,
            "product_id": String,
            "tax_category_id": String,
            "shipping_category_id": String,
            "code": String,
            "position": Integer,
            "on_hold": Integer,
            "on_hand": Integer,
            "tracked": Boolean,
            "height": Integer,
            "depth": Integer,
            "weight": Integer,
            "shipping_required": Boolean,
            "volume": Integer,
            "enabled": Boolean,
            "minimumAmount": Integer,
            "maximumAmount": Integer,
            "channel_pricing": Array [
                {
                    "price": Integer,
                    "original_price": Integer,
                    "channel_code": String,
                    "finalConsumerPrice": Integer,
                    "originalFinalConsumerPrice": Integer
                }
            ]
        }
    ]

```

| Field           |                       Description                        |
|-----------------|:--------------------------------------------------------:|
| code    |                easycommerce variant code                 |
| on_hand         |                 single stock of variant                  |
| channel_pricing |  price associated with the channel to which it updates   |



## get all variants

```
Url : service/variant/  method: GET  

Header with authentication is needed

request: 

    None
    
response:
[
        {
            "width": Integer,
            "product_id": String,
            "tax_category_id": String,
            "shipping_category_id": String,
            "code": String,
            "position": Integer,
            "on_hold": Integer,
            "on_hand": Integer,
            "tracked": Boolean,
            "height": Integer,
            "depth": Integer,
            "weight": Integer,
            "shipping_required": Boolean,
            "volume": Integer,
            "enabled": Boolean,
            "minimumAmount": Integer,
            "maximumAmount": Integer,
            "channel_pricing": Array [
                {
                    "price": Integer,
                    "original_price": Integer,
                    "channel_code": String,
                    "finalConsumerPrice": Integer,
                    "originalFinalConsumerPrice": Integer
                }
            ]
        }
    ]
    
```

| Field           |                       Description                        |
|-----------------|:--------------------------------------------------------:|
| code    |                easycommerce variant code                 |
| on_hand         |                 single stock of variant                  |
| channel_pricing |  price associated with the channel to which it updates   |
| weight          |                      variant weight                      |

## Update variant

```
Url : service/variant/  method: PUT  

Header with authentication is needed

request: 

    [
        {
            "variant_id": String,
            "width": Integer = None,
            "product_id": String = None,
            "tax_category_id": String = None,
            "shipping_category_id": String = None,
            "position": Integer = None,
            "on_hold": Integer = None,
            "on_hand": Integer = None,
            "tracked": Boolean = None,
            "height": Integer = None,
            "depth": Integer = None,
            "weight": Integer = None,
            "shipping_required": Boolean = None,
            "volume": Integer = None,
            "enabled": Boolean = None,
            "minimumAmount": Integer = None,
            "maximumAmount": Integer = None,
        },
        {
            "variant_id": String,
            "width": Integer = None,
            "product_id": String = None,
            "tax_category_id": String = None,
            "shipping_category_id": String = None,
            "position": Integer = None,
            "on_hold": Integer = None,
            "on_hand": Integer = None,
            "tracked": Boolean = None,
            "height": Integer = None,
            "depth": Integer = None,
            "weight": Integer = None,
            "shipping_required": Boolean = None,
            "volume": Integer = None,
            "enabled": Boolean = None,
            "minimumAmount": Integer = None,
            "maximumAmount": Integer = None,
        }.
        ...
    ]
    
response:

    
```

| Field           |                       Description                        |
|-----------------|:--------------------------------------------------------:|
| variant_id    |                easycommerce variant code                 |
| on_hand         |                 single stock of variant                  |
| weight          |                      variant weight                      |


## ---------- CHANNEL PRICING VARIANTS ----------

## Get all channels in Easycommerce

```
Url : service/channel-pricing  method: GET  

Header with authentication is needed

request: 

    None
    
response:
  [
    {
        "code": String
    }, ...
]


  
```


| Field                |        Description        |
|----------------------|:-------------------------:|
| code                 |   code name of channel    |
|

## Get Channel Pricing by variant

```
Url : service/channel-pricing  method: GET  

Header with authentication is needed

request: 

    {
        "variant_id": String
    }
    
response:
     [
        {
            "price": Integer,
            "original_price": Integer,
            "channel_code": String,
        }, ...
    ]


  
```


| Field |            Description            |
|-------|:---------------------------------:|
| price | price for this variant in channel |
| original_price |      price without discount       |
| channel_code |           channel code            |
|

## Edit Channel Pricing by variant

```
Url : service/channel-pricing  method: PUT  

Header with authentication is needed

request: 

    [
        {
            "variant_id": String,
            "channel_code": String,
            "price": Integer,
            "original_price": Integer
        }, ...
    ]
    
response:  Status code 200
     


  
```


| Field |            Description            |
|-------|:---------------------------------:|
| price | price for this variant in channel |
| original_price |      price without discount       |
| channel_code |           channel code            |
|



## -- ORDERS --

## Get Orders

```
Url : /orders  method: GET  

Header with authentication is needed

request: 

{
    "date_from": Datetime = Null,
    "date_to": Datetime = Null,
    "order_id": String = Null
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
