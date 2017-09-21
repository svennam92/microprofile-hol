# View, edit and build your Microprofile Java repositories

Navigate to your Java Microprofile directory. Here, you should see a number of directories. Primarily, the following folders contain all the microservices that make up our application:

```
sample.microservicebuilder.schedule
sample.microservicebuilder.session
sample.microservicebuilder.speaker
sample.microservicebuilder.vote
sample.microservicebuilder.web-app
```

Each of these repos represents a MicroProfile Java microservice. Notably, you'll see that each of these repos has a server.xml file - this is a descriptor that tells the Liberty runtime which features to enable for the corresponding microservice. You'll note that each has the following server.xml entry:

```
<feature>microProfile-1.0</feature>
```

This feature contains a set of capabilities that has been decided by the Microprofile community to serve the common requirements for creating microservices.

Within each directory is a Maven based project structure which can be imported into Eclipse or your favorite IDE. To make updates to the microservice, simply make the code changes and run `mvn package` to rebuild the application. This creates a newly compiled and packaged `.war` file in the `target` directory. Keep this in mind because we'll use this in the next exercise.

## Build your microservices
As the microservices have already been generated, run through all the directories to ensure that the microservices are up-to-date and passing tests. Run the following commands:

```
cd ~/JavaMicroprofile/sample.microservicebuilder.schedule
mvn clean package

cd ~/JavaMicroprofile/sample.microservicebuilder.session
mvn clean package

cd ~/JavaMicroprofile/sample.microservicebuilder.speaker
mvn clean package

cd ~/JavaMicroprofile/sample.microservicebuilder.vote
mvn clean package

cd ~/JavaMicroprofile/sample.microservicebuilder.web-app
mvn clean package
```

At each step of the way, you should have seen a message indicating `BUILD SUCCESS`. We're now ready to create Docker images for each our Microprofile-based Java microservices.

