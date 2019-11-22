# Q-Academico Lite - Authentication API

* [Guidelines](#guidelines)
* [HTTP Verbs](#http-verbs)
* [Responses](#responses)
* [Error handling](#error-handling)
* [Versions](#versions)
* [Request & Response Examples](#request--response-examples)

## Guidelines

This document provides guidelines and examples for Q-Academico Lite API.

This document borrows heavily from:
* [Designing HTTP Interfaces and RESTful Web Services](https://www.youtube.com/watch?v=zEyg0TnieLg)
* [API Facade Pattern](http://apigee.com/about/resources/ebooks/api-fa%C3%A7ade-pattern), by Brian Mulloy, Apigee
* [Web API Design](http://pages.apigee.com/web-api-design-ebook.html), by Brian Mulloy, Apigee
* [Fielding's Dissertation on REST](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)

### Good URL examples
* Add a new article to a particular magazine:
    * POST https://q-academico-lite.herokuapp.com/api/login
           http://q-academico-lite.herokuapp.com/api/login

### Bad URL examples
* Non-plural noun:
    * 
* Verb in URL:
    * 
* Filter outside of query string
    * 

## HTTP Verbs

HTTP verbs, or methods, should be used in compliance with their definitions under the [HTTP/1.1](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) standard.
The action taken on the representation will be contextual to the media type being worked on and its current state. Here's an example of how HTTP verbs map to create, read, update, delete operations in a particular context:

| HTTP METHOD | POST            |
| ----------- | --------------- | 
| operation   | Authentication  | 
| /api/login  | Validate student|

(Example from Web API Design, by Bruno Brown.)

## Responses

* No values in keys
* No internal-specific names (e.g. "node" and "taxonomy term")
* Metadata should only contain direct properties of the response set, not properties of the members of the response set


## Error handling

Error responses include a common HTTP status code, message for the developer, internal error code, links where developers can find more info. For example:

    {
      "status" : 400,
      "developerMessage" : "Verbose, plain language description of the problem.",
      "errorCode" : "99999",
      "moreInfo" : "http://www.example.gov/developer/path/to/help/for/99999,
    }

Use three simple, common response codes indicating (1) success, (2) failure due to client-side problem, (3) failure due to server-side problem:
* 200 - OK
* 400 - Bad Request
* 500 - Internal Server Error


## Versions

* Never release an API without a version number.
* Versions should be integers, not decimal numbers, prefixed with ‘v’. For example:
    * Good: v1
    * Bad: -
* Maintain APIs at least one version back.

## Request & Response Examples


### API Resources

  - [POST /api/login](#Post)


### POST /api/login

Example: Login – POST  https://q-academico-lite.herokuapp.com/api/login

Request body:

    {
        "login": "20191TIJG999",
        "senha": "12345",
        "estado": "PE"
    }
    
Response body:

    {
        "nome": "Lorem ipsum dolor sit amet",
        "curso": "Lorem ipsum dolor sit amet",
        "matriculado": true
        "status": {
            "erro": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            "situacao": "Concluído",
            "matriculado": true
        }
    }
