# GET /status

## Use

Retrieve the status of the current (or next) game.

## Parameters

None

## Response

If there is no game scheduled:

    {
        "status": "no-game",
    }

If there is a game either upcoming or currently running:

    {
        "status": "pre-game" or "current-game",
        "start": timestamp,
        "end": timestamp,
        "time": {
            "days": int,
            "hours": int,
            "minutes": int,
            "seconds": int,
            "diff": timestamp
        }
    }

The "time" object will be based on the game start if the game is upcoming, and on the game end if the game is currently
running. "diff" is the difference (in unix time) between now and the time object.

## Possible Errors

# GET /status/teams

## Use

Retrieve the number of players on each team.

## Parameters

None

## Response

    {
        "humans": int,
        "zombies": int
    }

## Possible Errors

None

# GET /player/{id}

## Use

Retrieve information about a player.

## Parameters

* _id:_ Id number for the player

## Response

    {
        "id": int,
        "fullname": string,
        "team": "human" or "zombie",
        "humansTagged" int,
        "clan": string,
        "badges": [ // array of badge objects in the following format
            {
                "id": string,
                "name": string,
                "image": string, // relative to /assets/images/badges
                "description": string,
                "access": string // access is the minimum role needed to apply a badge to a player, and is
                                 // not useful outside of the scope of the server.
            }
        ],
        "avatar": string // relative to /
    }

This response format is a "player" object, and is used in other endpoint responses as well.

## Possible Errors

_404:_ A standard 404 will be sent if the id is invalid or not found.

# GET /players/{page}

## Use

Retrieve the list of players.

## Parameters

* _page:_ The page number to retrieve (default: 0)
* _maxPerPage (query)_: The maximum number of players to return per page (default: 10, max: 30)
* _sort (query):_ The order to return players in. Valid values are "team", "mods", and "clan" (default: "team")

## Response

    {
        "continues": boolean, // if true, there are more pages
        "players": [] // array of player objects
    }

## Possible Errors

_400:_ The maxPerPage is greater than 30. A JSON-formatted error will be sent.

# GET /players/search

## Use

Search for players.

## Parameters

* _term (query)_: The search term. Has a minimum length of 3 characters. Searches by name and clan

## Response

Same format as _/players_

## Possible Errors

_400:_ term is less than three characters. A JSON-formatted error will be sent.

# GET /infections/{page}

## Use

Retrieve the list of infections.

## Parameters

* _page:_ The page number to retrieve (default: 0)
* _maxPerPage (query)_: The maximum number of infections to return per page (default: 10, max: 30)

## Response

    {
        "continues": boolean, // if true, there are more pages
        "infections": [ // array of infection objects in the following form
            {
                "id": int,
                "human": string, // name of the human, for convenience
                "human_id": int, // player id
                "zombie": string, // name of the zombie, for convenience
                "zombie_id": int, // player id
                "time": timestamp,
                "latitude": number, // might be null
                "longitude": number // might be null
            }
        ]
    }

## Possible Errors

_400:_ The maxPerPage is greater than 30. A JSON-formatted error will be sent.
