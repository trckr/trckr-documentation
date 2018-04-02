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


## Domain Model

The domain model is further described [here](domain_model.md).
