# ecommerce_server


```
weird admin cms

admin login
email : tio@mail.com
password : tiotio

env
SALT= 8
SECRET=grootnyasiapa
```

## Restful endpoints
#
# URL
```
Client URL : http://localhost:8080/ || https://cms-admin-tio.web.app/
Server URL : http://localhost:3000/ || https://cms-server-tio.herokuapp.com/
Customer URL : https://e-commerce-tio.web.app/
```

### GET/login
>login

_Request Header_
```
none
```
_Request Body_
```
email : tio@mail.com
password : tiotio
```
_Response(200)_
```
{
  access_token : "token string"
}
```
_Response(404)_
```
{
  message : 'email is not registered'
}
```
_Response(400)_
```
{
  message : "invalid"
}
```
_Response(400)_
```
{
  message : "field can not be empty"
}
```
_Response(500)_
```
{
  message : "internal server error"
}
```
### POST /products
>create product

_Request Header_
```
access_token : 'token string'
```
_Request Body_
```
{
  name : 'jam 2',
  "image_url": "https://www.jakartanotebook.com/images/products/72/63/22590/67/,
  price : 200000,
  stock : 10
}
```
_Response(201)_
```
{
  "id": 8,
  "name": "jam 2",
  "image_url": "https://www.jakartanotebook.com/images/products/72/63/22590/67/jam-dinding-bulat-european-style-34cm-colorful-vintage-multi-color-70.jpg",
  "price": 200000,
  "stock": 10
}
```
_Response(404)_
```
{
  message : 'email is not registered'
}
```
_Response(400)_
```
{
  message : "invalid"
}
```
_Response(400)_
```
{
  message : "field can not be empty"
}
```
_Response(500)_
```
{
  message : "internal server error"
}
```

### GET /products
>fetch all products

_Request Header_
```
access_token : 'token string'
```
_Request Body_
```
{
  none
}
```
_Response(200)_
```
{
  "products": [
        {
            "id": 3,
            "name": "groot",
            "image_url": "https://ae01.alicdn.com/kf/H21b16fc89a5b4e6c87e9d80ef495b4f1k/Lucu-Marvel-Avangers-Baby-Groot-Action-Figure-Mainan-PVC-Pahlawan-Model-Bayi-Manusia-Pohon-Lucu-Model.jpg",
            "price": 300000,
            "stock": 1,
            "createdAt": "2020-12-09T09:24:14.712Z",
            "updatedAt": "2020-12-09T12:35:27.052Z"
        },
        ...
    ]
}
```
_Response(500)_
```
{
  message : "internal server error"
}
```

### GET /products/:id
>find by id

_Request Header_
```
access_token : 'token string'
```
_Request Body_
```
{
  none
}
```
_Request Params_
```
{
  id : 3
}
```
_Response(200)_
```
{
  {
      "id": 3,
      "name": "groot",
      "image_url": "https://ae01.alicdn.com/kf/H21b16fc89a5b4e6c87e9d80ef495b4f1k/Lucu-Marvel-Avangers-Baby-Groot-Action-Figure-Mainan-PVC-Pahlawan-Model-Bayi-Manusia-Pohon-Lucu-Model.jpg",
      "price": 300000,
      "stock": 1,
      "createdAt": "2020-12-09T09:24:14.712Z",
      "updatedAt": "2020-12-09T12:35:27.052Z"
  },
}
```
_Response(500)_
```
{
  message : "internal server error"
}
```
### put /products/:id
>edit product

_Request Header_
```
access_token : 'token string'
```
_Request Params_
```
id : 3
```
_Request Body_
```
{
  name : 'groot2',
  image_url : 'https://ecs7.tokopedia.net/img/cache/900/product-1/2018/5/25/10897244/10897244_f9732383-bd09-4102-b740-75aab701b410_800_800.jpg',
  price : 20000,
  stock : 20
}
```
_Response(200)_
```
{ 
  id : 3
  name : 'groot2',
  image_url : 'https://ecs7.tokopedia.net/img/cache/900/product-1/2018/5/25/10897244/10897244_f9732383-bd09-4102-b740-75aab701b410_800_800.jpg',
  price : 20000,
  stock : 20
}
```
_Response(404)_
```
{ 
  "message": "product not found"
}
```
_Response(401)_
```
{ 
  "message": "please logoin first"
}
```
_Response(401)_
```
{ 
  "message": "you are not an admin"
}
```
_Response(400)_
```
{ 
  "message": [
    "stock can not lower than 0",
    "price can not lower than 0",
    "stock must be a number",
    "price must be a number"
  ]
}
```
### delete /products/:id
>delete product

_Request Header_
```
access_token : 'token string'
```
_Request Params_
```
id : 3
```
_Request Body_
```
{
  none
}
```
_Response(200)_
```
{ 
  "message": "succesfully delete a product"
}
```
_Response(401)_
```
{ 
  "message": "please logoin first"
}
```
_Response(401)_
```
{ 
  "message": "you are not an admin"
}
```
### GET/register
>register

_Request Header_
```
none
```
_Request Body_
```
email : tio@mail.com
password : tiotio
```
_Response(200)_
```
{
  {
    "id": 3,
    "email": "tio2@mail.com",
    "password": "$2a$08$OXugZS7CtcODtT5Nd8/lbe1e5dJbQr4aBkykkJ0JdCDbofyIym.Yi",
    "role": "user",
    "updatedAt": "2020-12-15T03:43:40.823Z",
    "createdAt": "2020-12-15T03:43:40.823Z"
    }
}
```
_Response(400)_
```
{
  {
    "messages": [
        "email must be unique",
        "must be between 6 to 20 characters"
    ]
  }
}
```

### GET/logincustomer
>login for customer

_Request Header_
```
none
```
_Request Body_
```
email : tio2@mail.com
password : tiotio
```
_Response(200)_
```
{
  access_token : "token string"
}
```
_Response(404)_
```
{
  message : 'email is not registered'
}
```
_Response(400)_
```
{
  message : "invalid"
}
```
_Response(400)_
```
{
  message : "field can not be empty"
}
```
_Response(500)_
```
{
  message : "internal server error"
}
```

### POST/carts
>creat or edit a cart for customer

_Request Header_
```
access_token: 'string'
```
_Request Body_
```
productId: number
```
_Response(201)_
```
{
  {
    "id": 28,
    "UserId": 3,
    "ProductId": 3,
    "quantity": 1,
    "status": false,
    "updatedAt": "2020-12-16T14:14:42.460Z",
    "createdAt": "2020-12-16T14:14:42.460Z"
  }
}
```
_Response(200)_
```
[
    1,
    [
        {
            "id": 28,
            "UserId": 3,
            "ProductId": 3,
            "status": false,
            "quantity": 2,
            "createdAt": "2020-12-16T14:14:42.460Z",
            "updatedAt": "2020-12-16T14:15:25.494Z"
        }
    ]
]

or

{
  message: 'successfully delete a cart'
}
```
_Response(401)_
```
{
  message: 'out of stock'
}
```
_Response(500)_
```
{
  message: 'internal server error'
}
```
### GET/carts
>fetch all unpaid carts for customer

_Request Header_
```
access_token: 'string'
```
_Request Body_
```
none
```
_Response(200)_
```
{
    "totalPrice": 600000,
    "carts": [
        {
            "id": 28,
            "UserId": 3,
            "ProductId": 3,
            "status": false,
            "quantity": 2,
            "createdAt": "2020-12-16T14:14:42.460Z",
            "updatedAt": "2020-12-16T14:15:25.494Z",
            "Product": {
                "id": 3,
                "name": "groot2",
                "image_url": "https://ae01.alicdn.com/kf/H21b16fc89a5b4e6c87e9d80ef495b4f1k/Lucu-Marvel-Avangers-Baby-Groot-Action-Figure-Mainan-PVC-Pahlawan-Model-Bayi-Manusia-Pohon-Lucu-Model.jpg",
                "price": 300000,
                "stock": 9,
                "createdAt": "2020-12-09T09:24:14.712Z",
                "updatedAt": "2020-12-16T13:22:40.078Z"
            }
        }
    ]
}
```
_Response(500)_
```
{
  message: 'internal server error'
}
```
### GET/carts/histories
>fetch histories for customer

_Request Header_
```
access_token: 'string'
```
_Request Body_
```
none
```
_Response(200)_
```
"carts": [
        {
            "id": 28,
            "UserId": 3,
            "ProductId": 3,
            "status": true,
            "quantity": 2,
            "createdAt": "2020-12-16T14:14:42.460Z",
            "updatedAt": "2020-12-16T14:15:25.494Z",
            "Product": {
                "id": 3,
                "name": "groot2",
                "image_url": "https://ae01.alicdn.com/kf/H21b16fc89a5b4e6c87e9d80ef495b4f1k/Lucu-Marvel-Avangers-Baby-Groot-Action-Figure-Mainan-PVC-Pahlawan-Model-Bayi-Manusia-Pohon-Lucu-Model.jpg",
                "price": 300000,
                "stock": 9,
                "createdAt": "2020-12-09T09:24:14.712Z",
                "updatedAt": "2020-12-16T13:22:40.078Z"
            }
        }
    ]
```
_Response(500)_
```
{
  message: 'internal server error'
}
```
### DELETE/carts/
>delete a cart for customer

_Request Header_
```
access_token: 'string'
```
_Request Body_
```
cartId
```
_Response(200)_
```
{
  message: 'succesfully deleted an item'
}
```
_Response(500)_
```
{
  message: 'internal server error'
}
```
### DELETE/carts/
>checkout all active cart for customer

_Request Header_
```
access_token: 'string'
```
_Request Body_
```
none
```
_Response(200)_
```
{
  {
    "success": [
        [
            1,
            [
                {
                    "id": 3,
                    "name": "groot2",
                    "image_url": "https://ae01.alicdn.com/kf/H21b16fc89a5b4e6c87e9d80ef495b4f1k/Lucu-Marvel-Avangers-Baby-Groot-Action-Figure-Mainan-PVC-Pahlawan-Model-Bayi-Manusia-Pohon-Lucu-Model.jpg",
                    "price": 300000,
                    "stock": 7,
                    "createdAt": "2020-12-09T09:24:14.712Z",
                    "updatedAt": "2020-12-16T14:26:22.830Z"
                }
            ]
        ],
        [
            1,
            [
                {
                    "id": 28,
                    "UserId": 3,
                    "ProductId": 3,
                    "status": true,
                    "quantity": 2,
                    "createdAt": "2020-12-16T14:14:42.460Z",
                    "updatedAt": "2020-12-16T14:26:22.830Z"
                }
            ]
        ]
    ]
}
}
```
_Response(400)_
```
  {
    message: [
      'failed to buy {product-name}',
      ...
  { ]
```