# Architecure

In this part of the trckr documentation, the software architecture is explained.

## Architecture Sketch

Trckr is a web based application. The web frontend is developed with Javascript and has access to a PostgreSQL database via the backend, which is written in Python.

![Architecture](../../../img/architecture.png)

## Technologies & Tools

### Backend

* Python ([Django](https://www.djangoproject.com/))
* [PostgreSQL](https://www.postgresql.org/)

### Frontend

* JavaScript ([Vue.js](https://vuejs.org/))

Tho following graphic shows a draft of the components we plan to implement into the frontend. Changes may be needed.
![Frontend Architecture](https://github.com/trckr/trckr-frontend/blob/master/documentation/trckr-frontend-architecture.png)

## Interface communication
This paragraph explains the communication between the backend and the frontend through json objects.

### User registration

### User login
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
