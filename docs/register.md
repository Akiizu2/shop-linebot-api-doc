# Register member with line #

This API provides registering a member with line service.

## URL ##

|              |                           |
| ------------ | ------------------------- |
| **Method**   | POST                      |
| **Endpoint** | `/register` |

## Header Params ##

| Key           | Value  | Required | Description      |
| ------------- | ------ | -------- | ---------------- |
| Content-Type  | string | true     | application/json |
| Authorization | string | true     |                  |

## Data Params ##

| Key    | Value  | Required | Description      |
| ------ | ------ | -------- | ---------------- |
| email  | string | true     | Customer's email |
| userID | string | true     | line's userID       |

## Example request body ##

```json
{
  "email": "test@noti.com",
  "userID": "<XCXX1>"
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
