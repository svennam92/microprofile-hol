# Exercise 5: Build and push each of your microservices to DockerHub

### Prerequisites

[Create an account on DockerHub](https://hub.docker.com/). This gives you a namespace on their registry to push your Docker images.

### Build and Push your Docker images

In this step, we'll build and push the Docker images representing each of our microservices as well as an Nginx loadbalancer. Be sure to login first using `docker login`

```
cd ~/JavaMicroprofile

docker build -t <docker_namespace>/microservice-webapp sample.microservicebuilder.web-app
docker push <docker_namespace>/microservice-webapp

docker build -t <docker_namespace>/microservice-vote sample.microservicebuilder.vote
docker push <docker_namespace>/microservice-vote-cloudant

docker build -t <docker_namespace>/microservice-schedule sample.microservicebuilder.schedule
docker push <docker_namespace>/microservice-schedule

docker build -t <docker_namespace>/microservice-speaker sample.microservicebuilder.speaker
docker push <docker_namespace>/microservice-speaker

docker build -t <docker_namespace>/microservice-session sample.microservicebuilder.session
docker push <docker_namespace>/microservice-session

docker build -t <docker_namespace>/nginx-server nginx
docker push <docker_namespace>/nginx-server
```

Now the images are available in a public registry. When we deploy our application to our Kubernetes cluster in the cloud, it will fetch the images directly from Docker Hub.

### Next steps

Next we'll push our application to our Kubernetes cluster.