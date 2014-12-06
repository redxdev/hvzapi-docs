# POST /register_infection

## Use

Register an infection

_Note: While this does require an API key, it does not limit you to who can be infected/who is doing the infecting (provided you have valid human/zombie ids). The system will, however, disable your API key if you make too many invalid requests to this endpoint (contact an admin if this happens, either something's wrong or you're trying to cheat)._

## Parameters

* _apikey (query):_ The API key
* _human (request):_ The human id
* _zombie (request):_ The zombie id
* _latitude (request):_ Latitude (default: null)
* _longitude (request):_ Longitude (default: null)

## Response

    {
        "status": "ok",
        "human_name": string,
        "human_id": int, // the user id, not the id string
        "zombie_name": string,
        "zombie_id": int
    }

## Possible Errors

_400:_ A JSON-formatted error will be sent. Errors include "Invalid API key", "API not enabled for user", and "Maximum API usage hit due to failure rate". Endpoint-specific errors may also be included, such as "Invalid human id".

# POST /antivirus

## Use

Use an antivirus

_Note: While this does require an API key, it does not limit you to who can be cured (provided you have valid antivirus/zombie ids). The system will, however, disable your API key if you make too many invalid requests to this endpoint (contact an admin if this happens, either something's wrong or you're trying to cheat)._

## Parameters

* _apikey (query):_ The API key
* _antivirus (request):_ The human id
* _zombie (request):_ The zombie id

## Response

    {
        "status": "ok",
        "zombie_name": string,
        "zombie_id": int
    }

## Possible Errors

_400:_ A JSON-formatted error will be sent. Errors include "Invalid API key", "API not enabled for user", and "Maximum API usage hit due to failure rate". Endpoint-specific errors may also be included, such as "Invalid zombie id".

# GET /antivirus/valid_time

## Use

Find out if an antivirus may be used at the current time.

## Parameters

None

## Response

    {
        "result": boolean
    }

## Possible Errors

None