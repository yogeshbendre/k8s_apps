# Run simple RAG pipeline on K8s Cluster (No GPU Required)

In this simple tutorial, I present a K8s App to run a Simple RAG pipeline with two agents on Kubernetes.
This system can generate new images based on an input image for reference.

There is no GPU required for this application and you can get it to running within 10 minutes.
But inferencing may be a bit slow due to CPU only mode.

## Pre-requisite

* A kubernetes cluster running v1.32 or above
* A machine that can run the k8s commands against this cluster
* Preferrably a browser installed in the same machine as above 
  (If not, then a machine with a browser and that can talk to the machine that has access to the k8s cluster).


So, let's get right at it...!!!


## Step 1: Deploy the Two Agent System of Servers for RAG

### Create the server as K8s Deployment

First, let's deploy our Two Agent System as K8s deployment objects.
(There is one more app that gets deployed, but more about it later.)

```bash
git clone https://github.com/yogeshbendre/k8s_apps.git visual_rag_app
```

```bash
kubectl apply -f visual_rag_app/visual_rag_app/
```


This deployment uses tinyllama LLM model which doesn't require any GPU for performing inferences.
Please note, the download of container image may take a while due to its size for the first time.

### Verify the server pods are running

```bash
kubectl get pods
```



