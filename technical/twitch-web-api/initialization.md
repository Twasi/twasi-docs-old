# Initialization
If you use twitch-web-api via twasi core (for example in a twasi plugin),
you don't have to bother about initialization since that's already done for you.
Go ahead and fetch that juicy data!

If you want to use twitch-web-api in any other project (cool!), you have to call
the initialization method before you can use any of the static TwitchAPI methods.

If you forget to initialize it, all methods will throw an error.

To initialize, just call:

```java
AuthorizationContext authContext = new AuthorizationContext("clientId", "clientSecret", "redirectUri");
TwitchAPI.initialize(authContext);
```

After that you can use all methods. Have fun!
