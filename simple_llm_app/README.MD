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

### Create the server as K8s Deployment

First, let's deploy our LLM Server App as a K8s deployment object.

```bash
kubectl apply -f https://github.com/yogeshbendre/k8s_apps/blob/main/simple_llm_app/ysb-llm-server.yaml
```

This deployment uses tinyllama LLM model which doesn't require any GPU for performing inferences.
Please note, the download of container image may take a while due to its size for the first time.

### Verify the server pods are running

```bash
kubectl get pods
```

You should see the pod with name of the format "ysb-llm-sever-XXXX" in the running status.

### (OPTIONAL) Verify the server is running inside the pod

Check the logs of the running pod with the following command.
You should see that server is listening.
(Replace ysb-llm-server-XXX with the actual name of the pod you saw in the earlier command.)

```bash
kubectl logs ysb-llm-server-XXX
```





## Step 2: Expose the LLM Server App via a Load Balancer Service

```bash
kubectl apply -f https://github.com/yogeshbendre/k8s_apps/blob/main/simple_llm_app/ysb-llm-service.yaml
```


## Step 3: Enable k8s port-forwarding (For Testing Only)


```bash
kubectl -n ysb-llm-app port-forward --address=0.0.0.0 service/ysb-llm-server 8080:80
```

Next, we run more.
