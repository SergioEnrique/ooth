# A protected graphql API

This is an example of a protected graphql API,
to which the user will need to authenticate using a JWT.
This example API needs to be running for these example projects to work:

* [ooth-create-react-app](../ooth-create-react-app)

## Start it

Copy `settings.dist.js` to `settings.js` and adapt.

Run

```
npm start
```

The GraphQL endpoint is `/graphql`. Visit `/graphiql` to play with the data.

Notice how you can query posts and comments, but not insert any without having logged in.

## Logging in with a client

[ooth-client](../../packages/ooth-client) of course is supposed to do all of this for you - see its usage in [ooth-create-react-app](../ooth-create-react-app).

## Logging in (low level)

To be able to login you need to start the companion example [ooth](../ooth) server.

Once started register as a guest:

```
curl -XPOST {oothserver}/guest/register
```

will get you a JWT token

then

```
curl -XPOST {apiserver}/login --header "Authorization: JWT {enterjwttokenhere}" -c -
```

this will print the session cookie created by the server
- if you had done this request in a browser you could now start performing write queries to the graphql api.