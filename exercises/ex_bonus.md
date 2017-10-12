# Bonus Exercise
## Develop Java Microservices using Microservice Builder

### Prerequisites

[Install Docker](https://www.docker.com/community-edition)

[Install Git](https://git-scm.com/downloads)

### Install the Bluemix CLI Developer Plugin

You should have already installed the Bluemix CLI and Dev plugin as explained in the [main README](../README.md).

#### Make sure you're logged in

```
bx login
bx target --cf
```

### Create a microservice

You're now ready to start creating microservices. Run the following command to scaffold a new application:

```
bx dev create
```

Choose `1. Web App`, `1. Basic Web`, `1. Java`, and give it a unique name - I like to put my initials at the end of the name. Something like `webapp-skv`. Use the same name for the hostname. Skip the option to add services.

This will generate your application project. `cd` into it - in my case, `cd webapp-skv`.

Build the dependencies and a Docker image for your application:

```
bx dev build
```

Run your application:

```
bx dev run
```

Access the health endpoint for application at `localhost:9080/<app_name>/health`. 

### Developing your application

It's straight-forward to setup a iterative development work flow. Find the source code in the `src` directory. After making changes (or making additional REST endpoints for example), run `bx dev build` and `bx dev run`.

Happy Hacking!