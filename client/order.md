# Notify customer order #

This API provides notification with customer order.

## URL ##

|              |                 |
| ------------ | --------------- |
| **Method**   | POST            |
| **Endpoint** | `/client/order` |

## Header Params ##

| Key           | Value  | Required | Description         |
| ------------- | ------ | -------- | ------------------- |
| Content-Type  | string | true     | application/json    |
| Authorization | string | true     | token from auth API |

## Data Params ##

| Key   | Value  | Required | Description      |
| ----- | ------ | -------- | ---------------- |
| email | string | true     | Customer's email |
| order | object | true     | Order's detail   |

## Order structure ##

| Key         | Value                                | Required | Description                   |
| ----------- | ------------------------------------ | -------- | ----------------------------- |
| orderID     | string                               | true     | orderID from database         |
| orderItems  | array of object                      | true     | list of order's item          |
| orderStatus | enum [pending/available/not_enought] | true     | order's status                |
| totalPrice  | number                               | true     | total price of order          |
| cartURL     | string                               | true     | URL to cart system on website |

## OrderItems structure ##

| Key    | Value                                     | Required | Description           |
| ------ | ----------------------------------------- | -------- | --------------------- |
| title  | string                                    | true     | orderID from database |
| amount | number                                    | true     | list of order's item  |
| status | enum [pending/available/not_enought/sold] | true     | orderItem's status    |
| price  | number                                    | true     | list of order's item  |
| stock  | number                                    | false    | stock of item         |

## Example request body ( Pending Case ) ##

```json
{
  "email": "customer@shop.com",
  "order": {
    "cartURL": "",
    "orderID": "ORDER_001",
    "orderStatus": "pending",
    "orderItems": [{
      "title": "item_1",
      "status": "pending",
      "amount": 20,
      "price": 300
    }],
    "totalPrice": 1000.23
  }
}
```

## Example request body ( All Item is available ) ##

```json
{
  "email": "customer@shop.com",
  "order": {
    "cartURL": "http://www.cart.com",
    "orderID": "ORDER_001",
    "orderStatus": "available",
    "orderItems": [{
      "title": "item_1",
      "status": "available",
      "amount": 20,
      "price": 300
    }],
    "totalPrice": 1000.23
  }
}
```

## Example request body ( Some item is not available or not enougth ) ##

```json
{
  "email": "customer@shop.com",
  "order": {
    "cartURL": "http://www.cart.com",
    "orderID": "ORDER_001",
    "orderStatus": "not_enought",
    "orderItems": [{
      "title": "item_1",
      "status": "sold",
      "amount": 20,
      "price": 300
    },
    {
      "title": "item_1",
      "status": "not_enought",
      "stock": 3,
      "amount": 20,
      "price": 300
    }
    ],
    "totalPrice": 1000.23
  }
}
```

## Example success response ##

```json
{
  "data": true,
  "code": 200
}
```

## Example error response ##

```json
{
  "error": {
    "type": "authentication",
    "message": "Token is invalid.",
  },
  "code": 400
}
```

#### Error descriptions

| Http Code | Type           | Message                    |
| --------- | -------------- | -------------------------- |
| 410       | invalid        | this email does not exist. |
|           | authentication | Token is invalid.          |
