# Q-Academico Lite - Authentication API

* [Guidelines](#guidelines)
* [HTTP Verbs](#http-verbs)
* [Error handling](#error-handling)
* [Request & Response Examples](#request--response-examples)
* [Supported States](#currently-supported-states)
* [More](#more)

## Guidelines

This document provides guidelines and examples for Q-Academico Lite - Authentication API.

This document borrows heavily from:
* [Designing HTTP Interfaces and RESTful Web Services](https://www.youtube.com/watch?v=zEyg0TnieLg)
* [API Facade Pattern](http://apigee.com/about/resources/ebooks/api-fa%C3%A7ade-pattern), by Brian Mulloy, Apigee
* [Fielding's Dissertation on REST](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)

### URL examples
* Authenticate an IF student:
    * POST https://q-academico-lite.herokuapp.com/api/validate
    * POST http://q-academico-lite.herokuapp.com/api/validate

## HTTP Verbs

HTTP verbs, or methods, should be used in accordance with their definitions in the HTTP / 1.1 standard. The actions taken in the representation will be contextual to the type of media being worked on and its current state. Here is an example of how HTTP verbs are mapped to authenticate a particular student:

| HTTP METHOD  | POST            |
| -------------| --------------- | 
| operation    | Authentication  | 
| /api/validate| Validate student|

## Error handling

Error responses include a common HTTP status code, message for the developer, internal error code, links where developers can find more info. For example:

    {
         "timestamp": "2019-11-23T10:33:29.726+0000",
         "status": 400,
         "error": "Bad Request",
         "message": "JSON parse error: Unexpected character ('}' (code 125)): expected a value; nested exception is        com.fasterxml.jackson.core.JsonParseException: Unexpected character ('}' (code 125)): expected a value\n at [Source:    (PushbackInputStream); line: 5, column: 2]",
      "path": "/api/validate"
    }

Server response code:
* 200 - OK
* 400 - Bad Request
* 404 - Not Found
* 504 - Gateway Timeout

## Request & Response Examples

### API Resources

  - [POST /api/validate](#Post)


### POST /api/validate

Example: Validate – POST  https://q-academico-lite.herokuapp.com/api/validate

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
        "status": {
            "erro": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
            "situacao": "Concluído",
            "matriculado": true
        }
    }
    
## Currently supported states:

   AM; CE; ES; GO; MA; MG; PE; PI; RO; SE


## More
   * https://q-academico-lite.herokuapp.com/swagger-ui.html
