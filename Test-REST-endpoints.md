This will likely be removed at some point.

# GET /test/key

## Use

Test an api key.

## Parameters

* _apikey (query):_ The API key

## Response

    {
        "status": "ok",
        "user_id": int // user id for the api key
    }

## Possible Errors

_400:_ A JSON-formatted error will be sent. Errors include "Invalid API key", "API not enabled for user", and "Maximum API usage hit due to failure rate".
