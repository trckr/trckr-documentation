# Trckr

This is the documentation of the trckr application. We develop the application for the PSIT4 module of the Zurich University of Applied Sciences (ZHAW).

## Our Vision

Trckr is a unique time tracking tool which stands out from the competition with an intuitive user interface and a focus on business features. In addition to the easy to use and project-oriented time tracking, Trckr offers features for teams to distribute tasks between users and respond proactively to time delays. We offer great value from the self-employed up to large teams for little effort.

## Main Features

* Register users
* Login
* Create projects
* Create tasks on projects
* Track time on tasks

* Logout


## Architecture Sketch

Trckr is a web based application. The web frontend is developed with Javascriüt and has access to a PostgreSQL database via the backend, which is written in Python. 

![Architecture](./img/architecture.png)

## Technlogies & Tools

### Backend

* Python ([Django](https://www.djangoproject.com/))
* [PostgreSQL](https://www.postgresql.org/)

### Frontend

* JavaScript ([Vue.js](https://vuejs.org/))

### Tools

* [Trello (Scrum Board)](https://trello.com/b/MvMOhuQv/trckr)
* [Google Docs (Documents)](https://docs.google.com/document/d/1TdwhZx0khze8sM7WRxGhiDrvJfaQ-fk7Ok_TBcYImM0/edit?usp=sharing)
* Google Slides (Presentations)
* Documentation (GitHub Pages)

### Data

* Data model:
* Archiving and Backup model:

## Roles

### Product Owner

* [Dimitri Balidis](mailto:baliddim@students.zhaw.ch)

### Scrum Master

* [David Pacassi Torrico](mailto:pacasdav@students.zhaw.ch)

### Team Members

#### Backend

* [Luca Christen](mailto:chrisluc@students.zhaw.ch)
* [Savino Jossi](mailto:jossisav@students.zhaw.ch)
* [Daniel Milenkovic](mailto:milendan@students.zhaw.ch)

#### Frontend

* [Gabriel Ankeshian](mailto:ankesgab@students.zhaw.ch)
* [Angelica Nominator](mailto:moreiane@students.zhaw.ch)
* [David Pacassi Torrico](mailto:pacasdav@students.zhaw.ch)

## Scrum

### SCRUM Infos
* Sprints:
** Sprint 0: Project Setup 09.03.2018 - 16.03.2018
** Sprint 1: 16.03.2018 - 30.03.2018
** Sprint 2: 30.03.2018 - 13.04.2018
** Sprint 3: 13.04.2018 - 27.04.2018
** Sprint 4: 27.04.2018 - 11.05.2018
** Sprint 5: 11.05.2018 - 25.05.2018

### Definition of Ready

* The user stories are defined.
* The acceptance criteria of the user stories are defined.
* The dependencies between the user stories were identified.
* The user stories were estimated by the development team.
* The documentation has been started and is subject to change.

### Definition of Done

* The unit tests are green and the test coverage is at least 85% or more.
* Acceptance tests coded and passed.
* The code were reviewed attending all coding-standards.
* The documentation has been adapted to the changes.
* The code has been approved by the product owner.

### Non-Functional Requirements

* Fast and reliable.
* Totally scalable from small businesses to big enterprises.
* Secure through self-hosting.

### Principles

* E.g. high cohesion & low coupling, SOLID etc.

### Constraints

* Time: Development only until week 20.
* Meetings: Daily standup meetings are not possible, due to working hours of the team members.
* Team size: limited amount of team members (three frontend- and three backend-developers).

## Deployment

* Description of the deployment.

## Decision Log

* We decided to use ... because of ...
