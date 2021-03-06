# API Endpoints

Trckr relies on a well defined API to communicate between the backend and the frontend applications. This sections describes the current available API endpoints.

## Overview

* [Authentication](#authentication)
   * [Session Authentication](#session-authentication)
   * [Token Authentication](#token-authentication)
   * [Token Invalidation](#token-invalidation)
* [User](#user)
   * [Create User](#create-user)
* [Projects](#projects)
   * [List Projects](#list-projects)
   * [Create Project](#create-project)
   * [View Project](#view-project)
   * [Update Project](#update-project)
   * [Delete Project](#delete-project)
   * [View Project Tasks](#view-project-tasks)
* [Tasks](#tasks)
   * [Create Task](#create-task)
   * [View Task](#view-task)
   * [Update Task](#update-task)
   * [View Task Time Entries](#view-task-time-entries)
* [Time Entries](#time-entries)
   * [Create Time Entry](#create-time-entry)
   * [View Time Entry](#view-time-entry)
   * [View Time Entries for Current User](#view-all-time-entries-for-current-user)
   * [Update Time Entry](#update-time-entry)
   
## Authentication

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

To use the token to authenticate other API calls, the token has to be put into the header: `Authorization: Token <token>`. The current life time of a token is 365 days.

### Token Invalidation

POST [`https://trckr-api.trvlr.ch/api/tokens/invalidate/`](https://trckr-api.trvlr.ch/api/tokens/invalidate/)

This action will delete the token used in the authorization header with this request. A post body is not required.

## User

### Create User

POST [`https://trckr-api.trvlr.ch/api/user/`](https://trckr-api.trvlr.ch/api/user/)

Request body:
```
{
    "username" : "testuser",
    "email" : "test@example.com",
    "password" : "testpassword",
    "first_name" : "Max",
    "last_name" : "Muster"
}
```

Response:
```
{
    "id": 8,
    "username": "testuser",
    "email": "test@example.com",
    "first_name": "Max",
    "last_name": "Muster",
    "token": "450c24407787bba7e14b9386029789c14fa200a0"
}
```

#### Fields

* __username__: string, max_length=255, required
* __email__: email, max_length=255, optional
* __password__: string, min_length=8, use digits and letters, required
* __first_name__: string, max_length=255, optional
* __last_name__: string, max_length=255, optional

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

#### Fields

* __name__: string, max_length=255, required
* __description__: string, max_length=1024, optional    

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

#### Fields

* __name__: string, max_length=255, required
* __description__: string, max_length=1024, optional    

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

#### Fields

* __name__: string, max_length=255, required
* __description__: string, max_length=1024, optional
* __project__: int, id of existing project, required

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

#### Fields

* __name__: string, max_length=255, required
* __description__: string, max_length=1024, optional
* __project__: int, id of existing project, required

### View Task Time Entries

GET [`https://trckr-api.trvlr.ch/api/tasks/<id>/time-entries`](https://trckr-api.trvlr.ch/api/tasks/1/time-entries)

Response:
```
HTTP 200 OK

[
    {
        "id": 2,
        "timeSpent" : 5.123
        "description": "foo",
        "task": 1
    },
    {
        "id": 3,
        "timeSpent" : 10
        "description": "bar",
        "task": 1
    }
]
```

## Time Entries

### Create Time Entry

POST [`https://trckr-api.trvlr.ch/api/time-entries/`](https://trckr-api.trvlr.ch/api/time-entries/)

Request body:
```
{
    "description": "foo",
    "startTime": "2018-05-10 12:00:00",
    "timeSpent" : 5.123,
    "task": 1
}
```

#### Fields

* __description__: string, max_length=1024, optional
* __startTime__: A date time string in the format YYYY-MM-DD hh:mm[:ss], required
* __timeSpent__: decimal, max_digits=10, decimal_places=5, min_value=0.01, required
* __task__: int, id of existing task, required

Response:
```
HTTP 201 Created

{
    "id": 2,
    "description": "foo",
    "startTime": "2018-05-10T12:00:00",
    "timeSpent" : 5.123,
    "task": 1
}
```

### View Time Entry

GET [`https://trckr-api.trvlr.ch/api/time-entries/<id>`](https://trckr-api.trvlr.ch/api/time-entries/1)

Response:
```
HTTP 200 OK

{
    "id": 2,
    "timeSpent" : 5.123
    "startTime": "2018-05-10T12:00:00",
    "description": "foo",
    "task": 1
}
```

### View All Time Entries For Current User

GET [`https://trckr-api.trvlr.ch/api/time-entries`](https://trckr-api.trvlr.ch/api/time-entries)

Response:
```
HTTP 200 OK

[
    {
        "id": 2,
        "timeSpent" : 5.123
        "startTime": "2018-05-10T12:00:00",
        "description": "foo",
        "task": 1
    },
    {
        "id": 3,
        "timeSpent" : 10
        "startTime": "2018-05-10T12:00:00",
        "description": "bar",
        "task": 1
    }
]
```

### Update Time Entry

PUT [`https://trckr-api.trvlr.ch/api/time-entries/<id>/`](https://trckr-api.trvlr.ch/api/time-entries/)

Request body:
```
{
    "description": "bar",
    "startTime": "2018-05-10 12:00:00",
    "timeSpent" : 10,
    "task": 1
}
```

#### Fields

* __description__: string, max_length=1024, optional
* __startTime__: A date time string in the format YYYY-MM-DD hh:mm[:ss], required
* __timeSpent__: decimal, max_digits=10, decimal_places=5, min_value=0.01, required
* __task__: int, id of existing task, required

