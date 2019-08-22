# Authorization API #

This API provides authorization.

## URL ##

|              |         |
| ------------ | ------- |
| **Method**   | POST    |
| **Endpoint** | `/auth` |

## Header Params ##

| Key          | Value  | Required | Description                         |
| ------------ | ------ | -------- | ----------------------------------- |
| Content-Type | string | true     | application/json                    |
| X-Header     | string | true     | ***( must be "l;lyfu8iy[" )*** only |

## Example success response ##

```json
{
    "code": 200,
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwYXlsb2FkIjpudWxsLCJpYXQiOjE1NjYyMzAxMjMsIm5iZiI6MTU2NjIzMDEyMywiZXhwIjoxNTY2MjMwMTMzfQ.4oVAFpcZHYOKBsVUIkfkooKtZaQIk9p0APSF1IPULLg"
}
```

## Example error response  ##

```json
{
    "code": 400,
    "error": {
        "type": "invalid",
        "message": "X-Header is required"
    }
}
```

#### Error descriptions

| Http Code | Type    | Message              |
| --------- | ------- | -------------------- |
| 400       | invalid | X-Header is required |
|           |         | X-Header is invalid  |
