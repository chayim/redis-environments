# redis-environments

This repository contains the base docker files, and a docker-compose that helps create various redis environments. It relies on [docker profiles](https://docs.docker.com/compose/profiles/) to ensure that collections of dockers can be started, rather than starting everything, or just specific named items.  Below are some examples:

**To start everything**

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