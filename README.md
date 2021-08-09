# Spring Boot Application with Docker

## How to build project and docker image
```
$ ./gradlew clean build docker
```

## How to push the docker image
### Dockerhub
```
docker login
./gradlew dockerPush
```

### Google Container Registory
```
gcloud auth configure-docker # configure it only once
gcloud auth login
docker tag [image ID] asia.gcr.io/[project ID]/[application]:[version]
```
You can get the project ID through the following command:
`$ gcloud config get-value project`

## How to run the docker image
The port:8080 is for application server so that you can access it with http://localhost:8080
The port:9404 is for jmx_exporter so that you can scrape metrics with http://localhost:9404/metrics
```
$ docker run -p 8080:8080 -p 9404:9404 fuzzybsd/my-spring-boot-app:0.0.1
```

## How to login to the k8s cluster
### For GKE
```
gcloud container clusters get-credentials [cluster name] --region=asia-northeast1
```
https://cloud.google.com/kubernetes-engine/docs/how-to/cluster-access-for-kubectl#using-gcloud-config


