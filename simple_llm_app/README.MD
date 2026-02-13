# Run Simple LLM Server on K8s Cluster (No GPU Required)

In this simple tutorial, I present a K8s App to run a Simple LLM Server on Kubernetes.
There is no GPU required for this application and you can get it to running within 5 minutes.


## Pre-requisite

* A kubernetes cluster running v1.32 or above
* A machine that can run the k8s commands against this cluster
* Preferrably a browser installed in the same machine as above 
  (If not, then a machine with a browser and that can talk to the machine that has access to the k8s cluster).


So, let's get right at it...!!!


## Step 1: Deploy the LLM Server App

```bash
kubectl -n ysb-llm-app port-forward --address=0.0.0.0 service/ysb-llm-server 8080:80
```


## Step 2: Expose the LLM Server App via a Load Balancer Service

```bash
kubectl -n ysb-llm-app port-forward --address=0.0.0.0 service/ysb-llm-server 8080:80
```


## Step 3: Enable k8s port-forwarding (For Testing Only)


```bash
kubectl -n ysb-llm-app port-forward --address=0.0.0.0 service/ysb-llm-server 8080:80
```

Next, we run more.
