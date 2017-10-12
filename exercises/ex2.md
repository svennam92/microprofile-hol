# Exercise 2
## Build and push each of your microservices to DockerHub

### Prerequisites

[Create an account on DockerHub](https://hub.docker.com/). This gives you a namespace on their registry to push your Docker images. This namespace usually matches your Docker ID.

### Build and Push your Docker images

In this step, we'll build and push the Docker images representing each of our microservices as well as an Nginx loadbalancer.

Be sure to login first using `docker login`.

#### Push Docker Images to Docker Hub
When running the following steps, make sure to replace `<docker_namespace>` with your own Docker ID. In my case, it's `svennam92`.

```
docker build -t <docker_namespace>/microservice-webapp sample.microservicebuilder.web-app
docker push <docker_namespace>/microservice-webapp

docker build -t <docker_namespace>/microservice-vote-cloudant sample.microservicebuilder.vote
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

Now the images are available in a public registry. We need them in an accessible location because when we deploy our microservices to our Kubernetes cluster, we don't upload them directly from our laptop. Instead, we simply upload a manifest file to the Kubernetes cluster. This manifest tells our cluster to fetch and download the registry images directly from the registry - this saves time and allows our cluster to automatically keep our microservices up-to-date.

### Next steps

Next we'll push deploy some prerequisites as well as our microservices to our Kubernetes cluster. Continue to the [next exercise](ex3.md).
