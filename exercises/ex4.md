# Exercise 4: Use Helm to deploy fabric prerequisites

Before we "Dockerize" the microservices we compiled and packaged in Exercise 3, let's deploy some prerequisites to our Kubernetes cluster. It's a good idea to do this ahead of time as it may take up to 20 minutes for it to install.

## Helm - Streamline Kubernetes installations

Helm is a tool that allows you to manage Kubernetes "charts". Charts are pre-configured Kubernetes resources.

For our microservice to work, we need to deploy a fabric layer provided to us by Microservice Builder. This fabric allows us to connect up Liberty Microprofile instances with other services. In addition, we'll also deploy a sample ELK stack which allows us to retrieve metrics for our application in a Kibana dashboard.

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

TODO: Screenshot

### Next steps

Now that we've kicked off the prereq installation on our cluster, let's start dockerizing the microservices we compiled in the previous step.