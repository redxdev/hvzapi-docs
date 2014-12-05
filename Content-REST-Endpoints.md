# GET /rules

## Use

Retrieve the list of rules

## Parameters

None

## Response

    {
        "rulesets": [ // array of ruleset objects in the following format
            {
                "id": int,
                "title": string,
                "body": string
            }
        ]
    }

## Possible Errors

None

# GET /missions

## Use

Retrieve the list of missions for your team.

## Parameters

* _apikey (query):_ The API key

## Response

    {
        "missions": [ // array of mission objects in the following format
            {
                "id": int,
                "title": string,
                "body": string,
                "team": "human" or "zombie",
                "post_date": datetime
            }
        ]
    }

## Possible Errors

_400:_ A JSON-formatted error will be sent. Errors include "Invalid API key", "API not enabled for user", and "Maximum API usage hit due to failure rate".