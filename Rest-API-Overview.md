There is a public facing REST api that is available for anyone to use in order to develop applications, collect
statisticts, etc.

Before you start
================

* The current version of the API is v1
* The API only responds with JSON
* The API currently only supports data collection. Registering tags and working with user profiles are not yet
implemented.

Accessing the API
=================

All API endpoints are found at the path `/api/v1`.

Handling Errors
===============

As of now, server errors must be handled based on their error code. That means you need to check to see if the response
is an HTTP error code such as 404 or 500, as the server will not serve these errors in a JSON format.

Errors having to do directly with the endpoint will generally have an HTTP error code of 400 and a JSON response
describing the error. These will be explained in each endpoint's documentation. These errors have the following format:

    {
        "status": "error",
        "errors": [] // array of strings
    }