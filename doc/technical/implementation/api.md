# API Endpoints

Trckr relies on a well defined API to communicate between the backend and the frontend applications. This sections describes the current available API endpoints.

## User Management and Authentication

### Session Authentication

[`https://trckr.trvlr.ch/api/auth/login/`](https://trckr.trvlr.ch/api/auth/login/)

### Token Authentication

[`https://trckr.trvlr.ch/api/token-auth/`](https://trckr.trvlr.ch/api/token-auth/)

When a user tries to login the frontend will send a JSON request with following attributes:
```
{
  "username": <username>,
  "password": <pw>
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

#### Usage

To use the token to authenticate other API calls, the token has to be put into the header: `Authorization: JWT <token>`. The current life time of a token is 365 days.

### User logout

tbd

### Token Revocation

tbd

## Projects

### List Projects

GET [`https://trckr-api.trvlr.ch/api/projects/`](https://trckr-api.trvlr.ch/api/projects/)

Response:
```
[
    {
        "id": 1,
        "name": "test 1",
        "description": "foobar",
        "modifiedDate": "2018-04-04T19:29:43.296915Z",
        "createdDate": "2018-04-04T19:29:43.296847Z"
    },
    {
        "id": 2,
        "name": "test project 2",
        "description": "hello",
        "modifiedDate": "2018-04-04T19:29:57.017325Z",
        "createdDate": "2018-04-04T19:29:57.017285Z"
    }
]
```

### Create Project

POST [`https://trckr-api.trvlr.ch/api/projects/`](https://trckr-api.trvlr.ch/api/projects/)

Request body:
```
{
    "name": "test",
    "description": "foo",
}
```

The name is a charfield with a max length of 255 and required. Description is a text field and optional.

### View Project

GET [`https://trckr-api.trvlr.ch/api/projects/<id>/`](https://trckr-api.trvlr.ch/api/projects/1/)
  
Response:
```
{
    "id": 1,
    "name": "test 1",
    "description": "foobar",
    "modifiedDate": "2018-04-04T19:29:43.296915Z",
    "createdDate": "2018-04-04T19:29:43.296847Z"
},
```

### Update Project

PUT [`https://trckr-api.trvlr.ch/api/projects/<id>/`](https://trckr-api.trvlr.ch/api/projects/1/)

Request body:
```
{
    "name": "test",
    "description": "foo",
}
```

### Delete Project

DELETE [`https://trckr-api.trvlr.ch/api/projects/<id>/`](https://trckr-api.trvlr.ch/api/projects/1/)

### View Project Tasks

GET [`https://trckr-api.trvlr.ch/api/projects/<id>/tasks/`](https://trckr-api.trvlr.ch/api/projects/1/tasks/)

```
[
    {
        "id": 2,
        "name": "second test task",
        "description": "foo",
        "project": 1
    },
    {
        "id": 1,
        "name": "test task",
        "description": "foo",
        "project": 1
    }
]
```

## Tasks

### Create Task

POST [`https://trckr-api.trvlr.ch/api/tasks/`](https://trckr-api.trvlr.ch/api/tasks/)

Request body:
```
{
    "name": "second test task",
    "description": "foo",
    "project": 1
}
```

Response:
```
HTTP 201 Created

{
    "id": 2,
    "name": "second test task",
    "description": "foo",
    "project": 1
}
```

### View Task

GET [`https://trckr-api.trvlr.ch/api/tasks/<id>`](https://trckr-api.trvlr.ch/api/tasks/1)

Response:
```
HTTP 200 OK

{
    "id": 2,
    "name": "second test task",
    "description": "foo",
    "project": 1
}
```

### Update Task

PUT [`https://trckr-api.trvlr.ch/api/tasks/<id>/`](https://trckr-api.trvlr.ch/api/tasks/)

Request body:
```
{
    "name": "second test task",
    "description": "bar",
    "project": 1
}
```


