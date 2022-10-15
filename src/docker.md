# Docker

Docker can be used for a quick local dev setup, or to run Zerologin in a production environment as a container.

## Build
The docker image can be built from source:

```shell
$ docker build -t [tag] .
```

## Configure
For development it is best to run the container with docker-compose, as the container will connect to the databse on startup to do migrations. 

1. Set the image to the tag given in the step above.
1. Set the environment variables to your needs.

```yml
...

    zerologin:
        image: [tag]
    environment:
        PORT: 3333
        HOST: 0.0.0.0
...
```

It is possible to run the Zerologin container seperately, but there has to be a postgres instance running and accesible to Zerologin.

## Run
```shell
$ docker-compose create
$ docker-compose up
```