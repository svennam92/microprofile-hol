# MicroProfile and Kubernetes Hands-on Lab
## Create and Deploy Java Microservices

In this hands-on lab, you will follow a set of exercises to deploy Java microservices based on [MicroProfile](http://microprofile.io) to a Kubernetes cluster. 

### Application architecture
<img src="images/Architecture.png"  width="1000">

### Prerequisites

The VM you're using for the lab at Java One 2017 is already preconfigured with most of the dependencies. However, there are a few things you'll need to do manually.

_Note: Your VM password is `password`. You'll use this for `sudo` commands or if you get logged out_

#### Sign up for a Bluemix Account

Sign up for a new account on Bluemix. It is recommended that you create a new account from the [Bluemix Dashboard](https://console.ng.bluemix.net/) if the trial on your existing account has expired.

#### Spin up a new Kubernetes Cluster

Access the Bluemix Containers dashboard at [https://console.bluemix.net/containers-kubernetes/home/clusters](https://console.bluemix.net/containers-kubernetes/home/clusters)

Click the Create Cluster button, choose the "Lite" cluster option and give it a name like "MicroprofileHOL". It should take 10-20 minutes for a new Kubernetes cluster to get spun-up. You can continue for now - we'll verify that the cluster is running in [Exercise 3](ex3.md).

<img src="images/newcluster.png"  width="800">

#### Bluemix CLI (Java One Lab Attendees - Ignore, already installed)

Install by Bluemix CLI - Find the appropriate installer and follow the instructions [here](https://console.bluemix.net/docs/cli/index.html#downloads).

When logging in with `bx login`, use API endpoint `api.ng.bluemix.net`

#### Install Docker

Installing Docker allows you to create Docker images, publish them to the registry and run them natively as virtual machines.

```
# Download the script
curl -fsSL get.docker.com -o get-docker.sh

# Execute the script
sudo sh get-docker.sh

# Allow Docker usage as non-root user
sudo usermod -aG docker $(whoami)
```
Log out and log back in.

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