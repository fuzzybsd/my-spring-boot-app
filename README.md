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

## How to run the docker image
The port:8080 is for application server so that you can access it with http://localhost:8080
The port:9404 is for jmx_exporter so that you can scrape metrics with http://localhost:9404/metrics
```
$ docker run -p 8080:8080 -p 9404:9404 fuzzybsd/my-spring-boot-app:0.0.1
```