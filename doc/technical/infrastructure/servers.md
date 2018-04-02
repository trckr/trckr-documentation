# Servers

Our servers are described in this part of the documentation.

## Application Server

The application runs our server at nine.ch and can be found [here](https://trckr.trvlr.ch). Direct access to the server for deployments or configurations is accomplished through ssh with key based authentication. The TLS certificate is provided by Let's Encrypt and automated with the certbot.

## CI Server

The CI process is implemented with [CircleCi](https://circleci.com), which provides continues integration as a service. The link to our project can be found [here](https://circleci.com/gh/trckr) (access limited to contributers of the trckr application).
