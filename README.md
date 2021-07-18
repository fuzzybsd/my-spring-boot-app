# Spring Boot Application with Docker

## How to build project and docker image
```
$ ./gradlew clean build docker
```

## How to push the docker image
```
$ docker login
$ ./gradlew dockerPush
```