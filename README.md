#mithril.postgrest [![Circle CI](https://circleci.com/gh/catarse/mithril.postgrest/tree/master.svg?style=svg)](https://circleci.com/gh/catarse/mithril.postgrest/tree/master) [![Code Climate](https://codeclimate.com/github/catarse/mithril.postgrest/badges/gpa.svg)](https://codeclimate.com/github/catarse/mithril.postgrest)

## Use cases
What this library is supposed to do:
  
  * Help you authenticating in a PostgREST server.
  * Keep some session information in the browser localStorage.
  * Provide wrappers arround the mithril request function to use JWT.
  
## Usage
First we should init the library so that it will build the functions to access the API.
The init function takes one argument which is the API endpoint prefix, 
containing the URI to which all addresses will be appended. 
If the API is being served from exactly the same location as the page running the JS
you can just initialize without any argument.

To use an API available at ```http://api.foo.com/v1``` you can use the code:
```javascript
m.postgrest.init("http://api.foo.com/v1")
```

This will create two functions:

  * m.postgrest.authenticate - which should be used to request and store a token so we can make calls with authentication.
  * m.postgrest.request - which should be used for anonymous API calls.

After authentication ```m.postgrest.request``` is redefined to use the JWT in it's header.
