# Notify customer delivery status #

This API provides notification with customer payment confirmation.

## URL ##

|              |                           |
| ------------ | ------------------------- |
| **Method**   | POST                      |
| **Endpoint** | `/client/delivery-status` |

## Header Params ##

| Key           | Value  | Required | Description      |
| ------------- | ------ | -------- | ---------------- |
| Content-Type  | string | true     | application/json |
| Authorization | string | true     |                  |

## Data Params ##

| Key       | Value                | Required                         | Description       |
| --------- | -------------------- | -------------------------------- | ----------------- |
| email     | string               | true                             | Customer's email  |
| orderID   | string               | true                             | Order's ID        |
| invoiceNo | string               | true                             | Invoice No        |
| status    | enum [ pending/sent] | true                             | Delivery's status |
| delivery  | object               | **require** when status = 'sent' | Delivery property |

## delivery Object ##

| Key            | Value  | Required | Description            |
| -------------- | ------ | -------- | ---------------------- |
| company        | string | true     | Delivery's company     |
| type           | string | true     | Delivery type          |
| trackingNumber | string | true     | Tracking Number        |
| duration       | string | true     | Delivery's duration    |
| statusURL      | string | true     | URL of tracking system |

## Example request body ( pending case ) ##

```json
{
  "email": "test@noti.com",
  "orderID": "XCXX1",
  "invoiceNo": "SSKX",
  "status": "pending"
}
```

## Example request body ( sent case ) ##

```json
{
  "email": "test@noti.com",
  "orderID": "XCXX1",
  "invoiceNo": "SSKX",
  "status": "sent",
  "delivery": {
    "company": "Kerry Express",
    "type": "ส่งด่วน EMS",
    "trackingNumber": "XXII1122",	
    "duration": "1-2 วันทำการ",
    "statusURL": "http://www.kerry-express.com/XXII1122"
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
