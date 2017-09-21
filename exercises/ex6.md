# Exercise 6: Deploy your microservices to your Kubernetes cluster

In this exercise, we'll demonstrate why Kubernetes deployments are so easy and powerful. So far we've created a cluster, converted all our applications into containers and deployed the prerequisite dependencies to the cluster using Helm charts. Now let's push our containers.

### Customize deploy manifests

Get the IP of the node

```
$ kubectl get nodes
NAME             STATUS    AGE
10.76.193.96     Ready     23h
```

Change the image name given in the respective deployment YAML files for all the projects in the manifests directory with the newly build image names. Then, set the value of SOURCE_IP env variable present in deploy-nginx.yaml file present in manifests folder with the IP of the node.

For example, in the `manifests/deploy-speaker.yaml` file, change the following:

```
image: journeycode/microservice-speaker
to
image: <your_namespace>/microservice-speaker
```

### Double check prerequisites

Before you start deploying your application, make sure the Microservice Builder Add-ons are installed and running.

$ kubectl get pods --show-all=true
NAME                                    READY     STATUS      RESTARTS   AGE
fabric-zipkin-4284087195-d6s1t          1/1       Running     0          11m
key-retrieval-deploy-gkr9n              0/1       Completed   0          11m  # Make sure this job is completed
kibana-dashboard-deploy-rd0q5           1/1       Running     0          11m 
sample-elk-sample-elk-461262821-rp1rl   3/3       Running     0          11m 
secret-generator-deploy-bj1jj           0/1       Completed   0          11m  # Make sure this job is completed

### Deploy microservices using manifests

Now, deploy the microservices with the command `kubectl create -f manifests`.

After you have created all the services and deployments, wait for 10 to 15 minutes. You can check the status of your deployment on Kubernetes UI. Run 'kubectl proxy' and go to URL 'http://127.0.0.1:8001/ui' to check when the application containers are ready.

### Access your Application

Use the public IP of your Kubernetes cluster to access the Web Services Conference Application.

TODO: help user find their public IP. Screenshots to navigate application.


### Next Steps

Now that we've deployed the microservice, let's switch hats to a typical Operations engineer who would manage these deployments.