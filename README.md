# MicroProfile and Kubernetes Hands-on Lab
## Create and Deploy Java Microservices

In this hands-on lab, you will follow a set of exercises to deploy Java microservices based on [MicroProfile](http://microprofile.io) to a Kubernetes cluster. 

### Application architecture
<img src="images/Architecture.png"  width="1000">

### Prerequisites

#### Sign up for a Bluemix Account

Sign up for a new account on the [Bluemix Dashboard](https://console.ng.bluemix.net/).

#### Spin up a new Kubernetes Cluster

Access the Bluemix Containers dashboard at [https://console.bluemix.net/containers-kubernetes/home/clusters](https://console.bluemix.net/containers-kubernetes/home/clusters)

Click the Create Cluster button, choose the "Lite" cluster option and give it a name like "MicroprofileHOL". It should take 10-20 minutes for a new Kubernetes cluster to get spun-up. You can continue for now - we'll verify that the cluster is running in [Exercise 3](ex3.md).

<img src="images/newcluster.png"  width="800">

#### Bluemix CLI

Install by Bluemix CLI - Find the appropriate installer and follow the instructions [here](https://console.bluemix.net/docs/cli/index.html#downloads).

Login to the CLI with `bx login`. When prompted, use API endpoint `api.ng.bluemix.net`

You'll need to install a couple of plugins for the Bluemix CLI as well:

```
bx plugin install dev -r Bluemix
```

```
bx plugin install container-service -r Bluemix
# Initialize and verify plugin install
bx cs init
```

#### Install Other Dependencies

Install the following tools:
* [Docker CE](https://www.docker.com/community-edition)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
* [helm](https://github.com/kubernetes/helm)
* [Java 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Maven](https://maven.apache.org/install.html)

Verify you have the proper versions (newer should be fine):
```
$ docker -v
Docker version 17.09.0-ce, build afdb6d4

# Note this command will fail when checking the server version - it's expected as your CLI is not configured to connect to a server yet.
$ kubectl version
Client Version: version.Info{Major:"1", Minor:"5", GitVersion:"v1.5.6", GitCommit:"114f8911f9597be669a747ab72787e0bd74c9359", GitTreeState:"clean", BuildDate:"2017-03-28T13:54:20Z", GoVersion:"go1.7.4", Compiler:"gc", Platform:"linux/amd64"}
The connection to the server localhost:8080 was refused - did you specify the right host or port?

# Note this command will fail when trying to connect to Tiller, we'll configure this later
$ helm version
Client: &version.Version{SemVer:"v2.6.1", GitCommit:"bbc1f71dc03afc5f00c6ac84b9308f8ecb4f39ac", GitTreeState:"clean"}
Error: cannot connect to Tiller
```

### Exercises

You should run through the set of exercises sequentially. Each should take around 5-10 minutes to complete.

* Exercise 1: [View, edit and build your Microprofile Java repositories](exercises/ex1.md)
* Exercise 2: [Build and push each of your microservices to DockerHub](exercises/ex2.md)
* Exercise 3: [Use Helm to deploy fabric prerequisites](exercises/ex3.md)
* Exercise 4: [Deploy your microservices to your Kubernetes cluster](exercises/ex4.md)
* Exercise 5: [Managing your Kubernetes Cluster](exercises/ex5.md)
* Bonus Exercise: [Develop Java Microservices using Microservice Builder](exercises/ex_bonus.md)

### More Resources

To learn more about the microservices that we deployed and how they utilize the Java Microprofile technology, see the [GitHub project](https://github.com/eclipse/microprofile-conference). There are extensive instructions on how to actually develop these microservices.

On the IBM Developer Works website, see the [full journey](https://developer.ibm.com/code/journey/deploy-microprofile-java-microservices-on-kubernetes/) that explains the steps we followed, architecture diagrams, blogs, utilized technologies and more.

Get started with running a Kubernetes cluster on your local machine for development. [Minikube](https://kubernetes.io/docs/getting-started-guides/minikube/).

Manage your Kubernetes cluster on [IBM Cloud](https://console.bluemix.net/containers-kubernetes/home/clusters).

### Contact
You can contact me directly on Twitter at @sai_vennam.
