There is a public facing REST api that is available for anyone to use in order to develop applications, collect
statisticts, etc.

# Before you start

* The current version of the API is v1
* The API only responds with JSON
* The API handles game information (player list, infection list, etc), registering tags, registering antiviruses, and some *basic* profile settings

# Accessing the API

All API endpoints are found at the path `/api/v1`.

# Handling Errors

As of now, server errors must be handled based on their error code. That means you need to check to see if the response
is an HTTP error code such as 404 or 500, as the server will not serve these errors in a JSON format.

Errors having to do directly with the endpoint will generally have an HTTP error code of 400 and a JSON response
describing the error. These will be explained in each endpoint's documentation. These errors have the following format:

    {
        "status": "error",
        "errors": [] // array of strings
    }

# API Keys

API keys are used to access the more restricted endpoints. Status and stats related endpoints do not require an API key. Actions such as registering an infection or viewing sensitive profile info (email, ids, etc) _do_ require an api key.

As of now, all users have an API key generated for them but they must have it manually activated for them (this will eventually be done through the admin panel).