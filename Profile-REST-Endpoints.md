# GET /profile

## Use

Retrieve a player's profile info

## Parameters

* _apikey (query):_ The API key

## Response

    {
        "profile": {
            "id": int,
            "apikey": string,
            "fullname": string,
            "email": string,
            "clan": string // might be null
            "team": "human" or "zombie",
            "zombieId": string,
            "humansTagged": int,
            "badges" [], // array of badge objects, see the status api documentation for the format
            "avatar": string,
            "humanIds": [ // array of human id objects
                {
                    "id_string": string,
                    "active": boolean
                }
            ],
            "infections": [] // array of infection objects, see the status api documentation for the format
        }
    }

## Possible Errors

_400:_ A JSON-formatted error will be sent. Errors include "Invalid API key", "API not enabled for user", and "Maximum API usage hit due to failure rate".