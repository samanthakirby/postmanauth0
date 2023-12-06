# Postman with Auth0 tokens
If your API uses Auth0 to get authentication/authorization tokens, you wouldn't want to have to go and get this for each request you make to your endpoint. In this Postman template that I have created here, you make a call to your auth0 endpoint once, it saves it as an environment variable and uses that token for all subsequent calls.

# Some notes
You will need to set your client_id, client_secret, audience, grant_type for each enviornment file you create. You can get this information from your Auth0 account.

# How does it work?
There's a call to Auth0 url that includes the following body:
{
    "client_id": "{{CLIENT_ID}}",
    "client_secret":"{{CLIENT_SECRET}}",
    "audience": "{{AUDIENCE}}",
    "grant_type": "{{GRANT_TYPE}}"
};
These values are replaced by the environment variables you set per environment. The response body from the request should include your access_token.

Under the Test tab of that request, the following code extracts the access_token and saves it as an environment variable called JWT_TOKEN:
pm.environment.set("JWT_TOKEN", response.access_token);

If you click on the top level folder (in this template it's called API (Rename me to your API) and select the Authorization tab, you will see that the token is {{JWT_TOKEN}} with a type of bearer token. Each new request to your actual API needs to include "Inherit auth from parent".
