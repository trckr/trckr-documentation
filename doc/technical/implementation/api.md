# API Endpoints

Trckr relies on a well defined API to communicate between the backend and the frontend applications. This sections describes the current available api endpoints.

## User Management and Authentication

### Session Authentication

https://trckr.trvlr.ch/api/auth/login/

### Token Authentication

When a user tries to login the frontend will send a json request with following attributes:
```
{
  "username": <username>,
  "password": <hashed pw>
}
```

The backend will reply with either a fail:
```
{
  "non_field_errors":["Unable to log in with provided credentials."]
}
```
or a success:
```
{
  "token":"eyJ0eXAiOiJKV1QiLCJhb[...]vJzuiWUvZxytJ9yscldA"
}
```
The token is then used to authenticate for every action the user wants to perform.

### User logout
https://trckr.trvlr.ch/api/token-auth/

### Token Revocation

tbd
