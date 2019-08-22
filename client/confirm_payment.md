# Notify customer payment confirmation #

This API provides notification with customer payment confirmation.

## URL ##

|              |                           |
| ------------ | ------------------------- |
| **Method**   | POST                      |
| **Endpoint** | `/client/confirm-payment` |

## Header Params ##

| Key           | Value  | Required | Description         |
| ------------- | ------ | -------- | ------------------- |
| Content-Type  | string | true     | application/json    |
| Authorization | string | true     | token from auth API |

## Data Params ##

| Key       | Value  | Required | Description      |
| --------- | ------ | -------- | ---------------- |
| email     | string | true     | Customer's email |
| orderID   | string | true     | Order's ID       |
| invoiceNo | string | true     | Invoice No       |

## Example request body ##

```json
{
  "email": "test@noti.com",
  "orderID": "XCXX1",
  "invoiceNo": "SSKX"
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
