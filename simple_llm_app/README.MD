# Run Simple LLM Server on K8s Cluster (No GPU Required)

This App is to run a Simple LLM Server on Kubernetes


kubectl -n ysb-llm-app port-forward --address=0.0.0.0 service/ysb-llm-server 8080:80
