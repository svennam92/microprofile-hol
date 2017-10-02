# Exercise 4
## Deploy your microservices to your Kubernetes cluster

In this exercise, we'll demonstrate why Kubernetes deployments are so easy and powerful. So far we've created a cluster, converted all our applications into containers and deployed the prerequisite dependencies to the cluster using Helm charts. Now let's push our containers.

### Customize deploy manifests

Change the image name given in the respective deployment YAML files for all the projects in the manifests directory with the newly built/pushed image names. You'll have to do once for each of the following files:

```
deploy-schedule.yaml
deploy-session.yaml
deploy-speaker.yaml
deploy-vote.yaml
deploy-webapp.yaml
```

For example, in the `manifests/deploy-speaker.yaml` file, change the following except with your own Docker Hub namespace:

```
image: journeycode/microservice-speaker
to
image: svennam92/microservice-speaker
```

Then, set the value of SOURCE_IP env variable present in the `manifests/deploy-nginx.yaml` file with the IP of the node. 

Get the IP of the node

```
$ kubectl get nodes
NAME             STATUS    AGE
10.76.193.96     Ready     23h
```

In my case it looks like this:

```
        env:
          - name: SOURCE_IP
           #change the value of IP with Kubernetes EXTERNAL-IP
            value: xxx.xxx.xx.xxx
```
to
```
        env:
          - name: SOURCE_IP
           #change the value of IP with Kubernetes EXTERNAL-IP
            value: 10.76.193.96
```

### Double check prerequisites

Before you start deploying your application, make sure the Microservice Builder Add-ons are installed and running.

```
$ kubectl get pods --show-all
NAME                                    READY     STATUS      RESTARTS   AGE
fabric-zipkin-4284087195-d6s1t          1/1       Running     0          11m
key-retrieval-deploy-gkr9n              0/1       Completed   0          11m  # Make sure this job is completed
kibana-dashboard-deploy-rd0q5           1/1       Running     0          11m 
sample-elk-sample-elk-461262821-rp1rl   3/3       Running     0          11m 
secret-generator-deploy-bj1jj           0/1       Completed   0          11m  # Make sure this job is completed
```

### Deploy microservices using manifests

Now, cd back to the main directory with `cd ~/JavaMicroprofile` and deploy the microservices with the command `kubectl create -f manifests`. You should promptly see the following:

```
⌞~/MicroprofileHOL⌟ ➤ kubectl create -f manifests
job "cloudant-secret-generator-deploy" created
persistentvolume "cloudant-pv" created
persistentvolumeclaim "cloudant-pv-claim" created
service "cloudant-service" created
deployment "cloudant-db" created
replicationcontroller "nginx-rc" created
service "nginx-svc" created
deployment "microservice-schedule-sample" created
service "schedule-service" created
deployment "microservice-session-sample" created
service "session-service" created
deployment "microservice-speaker-sample" created
service "speaker-service" created
deployment "microservice-vote-sample" created
service "vote-service" created
deployment "microservice-webapp-sample" created
service "webapp-service" created
```

After you have created all the services and deployments, you'll have to wait for 5 to 10 minutes. However, you can check the status of your deployment on Kubernetes UI. Run `kubectl proxy` and go to URL 'http://127.0.0.1:8001/ui' to check when the application containers are ready. It'll look like this once it's ready:

<img src="../images/ready.png"  width="700">

### Access your Application

Use the public IP of your Kubernetes cluster to access the Web Services Conference Application. You can find the Public IP of your cluster on the [Bluemix Containers Dashboard](https://console.bluemix.net/containers-kubernetes/home/clusters). Click your cluster, then click "Worker Nodes" along the leftside. The Public IP is listed by the worker node.

<img src="../images/PublicIP.png"  width="700">

To access your application, navigate to `<PUBLIC_IP>:30056`. Spend a moment to click around and orient yourself with the application.

<img src="../images/Microprofile.png"  width="700">

### Next Steps

Now that we've deployed the microservice, let's switch hats to a typical Operations engineer who would manage these deployments. Continue to the [next exercise](ex5.md).
