# Exercise 1
## View, edit and build your Microprofile Java repositories

Clone or download this repository and cd to it.

Here you should see a number of directories. Primarily, the following folders contain all the microservices that make up our application:

```
sample.microservicebuilder.schedule
sample.microservicebuilder.session
sample.microservicebuilder.speaker
sample.microservicebuilder.vote
sample.microservicebuilder.web-app
```

Each of these repos represents a MicroProfile Java microservice. Notably, you'll see that each of these repos has a server.xml file - this is a config file that tells the Liberty runtime which features to enable for the corresponding microservice. You'll note that each has the following `server.xml` entry:

```
<feature>microProfile-1.0</feature>
```

This feature contains a set of capabilities (and other _features_) that has been decided by the Microprofile community to serve the common requirements for microservice development.

### Developing Java Microservices

This lab is focused on the deployment portion of these microservices. However, it's fairly straightforward to make changes to the individual microservices. Within each directory is a Maven based project structure which can be imported into Eclipse or your favorite IDE. To make updates to the microservice, simply make the code changes and run `mvn package` to rebuild the application. This creates a newly compiled and packaged `.war` file in the `target` directory.

You may want to run your cluster locally when in development mode. To do so, you would use a tool called [Minikube](https://kubernetes.io/docs/getting-started-guides/minikube/). However, in this set of exercises we'll be deploying to the dedicated Kubernetes cluster on IBM's Cloud - you should have created this as part of the [prerequisites](../README.md).

### Build your microservices
The microservices have already been cloned. However, you should run through all the folders to build the dependencies and ensure they passing tests. You'll be running build commands with Maven - a software project management tool used to manage the dependencies and project structure of your microservices. Run the following commands:

```
cd sample.microservicebuilder.schedule
mvn clean package

cd ../sample.microservicebuilder.session
mvn clean package

cd ../sample.microservicebuilder.speaker
mvn clean package

cd ../sample.microservicebuilder.vote
mvn clean package

cd ../sample.microservicebuilder.web-app
mvn clean package
```

At each step of the way, you should have seen a message indicating `BUILD SUCCESS`. Each build creates its own `.war` file in the `target` folder.

### Next Steps

We're now ready to create Docker images for each of our Microprofile-based Java microservices. Continue on to the [next exercise](ex2.md).