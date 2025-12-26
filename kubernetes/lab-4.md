The Nautilus DevOps team wants to deploy a temporary debug application in the cluster.

Requirements:

Create a Pod named debug-pod

Use image busybox:latest

Pod should run the command sleep 3600

Add labels:

env=dev

team=devops

The pod should NOT restart if the container exits


Approach-1: Using yaml manifest
```
# pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: debug-pod
  labels:
    env: dev
    team=devops
spec:
  restartPolicy: Never
  containers:
  - name: debug-container
    image: busybox:latest
    command: ["sleep", "3600"]
```
```
kubectl apply -f pod.yaml
```

Approach-2: Using kubetl run cmd
```
kubectl run debug-pod \
  --image=busybox:latest \
  --restart=Never \
  --labels=env=dev,team=devops \
  --command -- sleep 3600
```


