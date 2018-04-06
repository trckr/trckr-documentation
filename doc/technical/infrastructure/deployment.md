# Deployment

This part of the documentation describes everything one needs to know to deploy the trckr application.

## Backend

Deployments for the backend happen automatically. The process to initiate a new deployment is as follows:

* A new commit gets pushed into the master branch.
* The CI server starts building the application and runs the unit tests.
* If the CI process was successful, the server will connect with the production system and run the deployment.

Since database migrations are part of the build process, they are included in the automatic deployment.
