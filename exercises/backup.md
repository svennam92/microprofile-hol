# Backup - Use an existing cluster

If you're running into issues with spawning a Kubernetes cluster, you can use a cluster that I've already deployed.

Download the configuration file here: [https://ibm.box.com/s/76xvgcf8auokthgxmsse9bh4qvhfjokg](https://ibm.box.com/s/76xvgcf8auokthgxmsse9bh4qvhfjokg)

Download the PEM file here: [https://ibm.box.com/s/xqhc3w84kts2k614w3q8isow4j1384zp](https://ibm.box.com/s/xqhc3w84kts2k614w3q8isow4j1384zp)

Make sure both of these files are in the same directory. Then, set KUBECONFIG to that file to configure your CLI to work with my dedicated cluster. Run the following to configure your CLI:

```
export KUBECONFIG=<path_to_file>
```

It'll look something like this:

```
export KUBECONFIG=/home/javaone-hol/Downloads/kube-config-hou02-MicroprofileHOL.yml
```

Now that you're configured to work with the cluster, continue with [Exercise 3](ex3.md). However, please skip the `kubectl` commands.