# redis-environments

Note: This repository requires a version of docker-compose with support for profiles.

This repository contains the base docker files, and a docker-compose that helps create various redis environments. It relies on [docker profiles](https://docs.docker.com/compose/profiles/) to ensure that collections of dockers can be started, rather than starting everything, or just specific named items.  Environments in this repository, rely on the *.env* file, for setting exposed ports. If you want to change the ports for your needs - modify the .env file, or pass in an explicit dotnet to docker-compose by changing commands to ```docker-compose --env-file <your file>...```

Examples:

**To start all non RESP3 dockers**

```bash
docker-compose --profile all up
```

**To start dockers based on unstable**
```bash
docker-compose --profile unstable up
```

**Redis environments, modified to default to RESP3**
```bash
docker-compose --profile resp3 up
```

Note: Some of these environments build dockers, rather than pulling from dockerhub. As a result, you will maintain a docker cache locally, once built. To force a rebuild extend the *docker-compose --profile <name> up* command by passing in *--build*.

```bash
docker-compose --profile resp3 up --build
```
