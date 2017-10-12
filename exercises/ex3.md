# Exercise 3
## Use Helm to deploy fabric prerequisites

Before we "Dockerize" the microservices we compiled and packaged in [Exercise 2](ex2.md), let's deploy some prerequisites to our Kubernetes cluster. It's a good idea to do this ahead of time as it may take up to 20 minutes for it to install.

## Prerequisites

Ensure that your cluster has finished deploying. Navigate to your [dashboard on Bluemix](https://console.bluemix.net/containers-kubernetes/home/clusters) and double check that there is a green "Ready" icon.

If it's still not ready, you'll need to wait before the following steps. Things you can do while you wait:

* Check out the [Bonus exercise](ex_bonus.md) to learn how to create new microservices using the [Microservice Builder](https://developer.ibm.com/microservice-builder/)
* Navigate the microservices in this repo to familiarize yourself with the application architecture. For a more guided experience, check out the resources on [microprofile.io](https://microprofile.io/project/eclipse/microprofile-conference).

If the cluster is not working or has not spwaned in time for you to continue with the lab, please see the [instructions here](backup.md).

### Configure CLI to connect to your Kubernetes Cluster

You should have already installed the Bluemix CLI as explained in the [main README](../README.md). If you haven't already, make sure you're logged in: `bx login`. If prompted, use API endpoint `api.ng.bluemix.net`

Run `bx cs init` to initialize your container-service plugin.

Run `bx cs clusters` to see all your clusters in Bluemix - there should only be one.

Run `bx cs cluster-config <cluster_name>` to download the configuration file that allows you to access the cluster. It tells you to run a `export` command. Copy-paste to execute that command.

Run `kubectl cluster-info` to ensure that you're connected to the running Kubernetes Cluster. You should see something like this:

```
$ kubectl cluster-info
Kubernetes master is running at https://184.173.44.62:27192
Heapster is running at https://184.173.44.62:27192/api/v1/proxy/namespaces/kube-system/services/heapster
KubeDNS is running at https://184.173.44.62:27192/api/v1/proxy/namespaces/kube-system/services/kube-dns
kubernetes-dashboard is running at https://184.173.44.62:27192/api/v1/proxy/namespaces/kube-system/services/kubernetes-dashboard

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

## Helm - Streamline Kubernetes installations

Helm is a tool that allows you to manage Kubernetes "charts". Charts are pre-configured Kubernetes resources.

For our microservices to work, we need to deploy a fabric layer provided to us by Microservice Builder, an IBM tool to streamline development. This fabric allows us to connect up Liberty Microprofile instances with other services. In addition, we'll also deploy a sample ELK stack which allows us to retrieve metrics for our application in a Kibana dashboard.

### Installing prerequisites to our cluster

Initialize the helm installation

```
helm init
```

Install the fabric

```
helm repo add mb http://public.dhe.ibm.com/ibmdl/export/pub/software/websphere/wasdev/microservicebuilder/helm/
helm install --name fabric mb/fabric
```

Install the ELK stack

```
helm repo add mb-sample https://wasdev.github.io/sample.microservicebuilder.helm.elk/charts
helm install --name sample-elk mb-sample/sample-elk
```

### Verify installation

Run `kubectl get pods --show-all`

You should see the following pods getting installed:
```
⌞~/MicroprofileHOL⌟ ➤ kubectl get pods --show-all
NAME                                     READY     STATUS              RESTARTS   AGE
fabric-zipkin-992988055-88jls            1/1       Running             0          27s
key-retrieval-deploy-fn832               0/1       ContainerCreating   0          16s
kibana-dashboard-deploy-hbn7x            0/1       ContainerCreating   0          16s
sample-elk-sample-elk-2521815307-mscw4   0/3       ContainerCreating   0          16s
secret-generator-deploy-znv3c            0/1       ContainerCreating   0          27s
```

### Next steps

Now that we've kicked off the prereq installation on our cluster, let's start dockerizing the microservices we compiled in the previous step. Continue on to [Exercise 4](ex4.md).