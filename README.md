# Chained-API-Requests

**Chained-API-Requests** is a sample API built in **WSO2 Synapse** that demonstrates how to perform **sequential API calls** and pass data between them.  

The API works by:
1. Calling an external API (Postman Echo) with fixed query parameters.
2. Extracting the `host` header value from the first response.
3. Using that extracted value to build a second request dynamically.
4. Returning the result of the second call back to the client.

## This repository includes:

- The Synapse API XML configuration (`chained-API-requests.xml`)
- Example Postman request & response
- Anonymized/sample data

## How to Run

1. **Deploy in WSO2 EI / Micro Integrator**  
   - Copy `chained-API-requests.xml` into your WSO2 Synapse `api` deployment folder.  
   - Restart WSO2.  

2. **Test with Postman or curl**  

**Example request:**
```http
GET http://localhost:8280/chained/requests
```

Example success response (200 OK):

{
    "args": {
        "foo1": "bar1",
        "foo2": "postman-echo.com"
    },
    "headers": {
        "host": "postman-echo.com",
        "x-request-start": "t1755222222.669",
        "connection": "close",
        "x-forwarded-proto": "https",
        "x-forwarded-port": "443",
        "x-amzn-trace-id": "Root=1-333ba333-263c273333fdecb0744aa836",
        "set-cookie": [
            "sails.sid=s%3AH6FpX5I52LT3mYzpc1111_4kMFrl4o5V.dbzUY%3FDxeIkL7AkiJrrrrrpkyPBUFINo%2F78wjDv9b6c; Path=/; HttpOnly"
        ],
        "etag": "W/\"247-kd/eM8werty7J4He7tVBggpc4+g\"",
        "content-type": "application/json; charset=utf-8",
        "user-agent": "Synapse-PT-HttpComponents-NIO"
    },
    "url": "https://postman-echo.com/get?foo1=bar1&foo2=postman-echo.com"
}
