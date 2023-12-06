# Postman with Auth0 tokens
If your API uses Auth0 to get authentication/authorization tokens, you wouldn't want to have to go and get this for each request you make to your endpoint. In this Postman template that I have created here, you make a call to your auth0 endpoint once, it saves it as an environment variable and uses that token for all subsequent calls.

# Some notes
1. If your token expiry is set very frequently, this can be annoying when you're calling individual endpoints because you will need to get the new token. However, it will run the auth0 call first when you run your collection so that should be fine.
2. You will need to set your client_id, client_secret, audience for each enviornment file you create.
