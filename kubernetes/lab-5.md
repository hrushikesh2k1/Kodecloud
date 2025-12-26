The Nautilus DevOps team is running a stateless web application and wants zero downtime deployments.

Requirements:

Create a Deployment named web-app

Use image nginx:1.25

Run 3 replicas

Ensure rolling updates with:

maxUnavailable = 1

maxSurge = 1

Add label app=web

Verify rollout status

Roll back if deployment fails


Approach:
```
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-app
spec:
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 1
      maxSurge: 1
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
        - name: nginx
          image: nginx:1.25
          ports:
            - containerPort: 80
```
maxUnavailable:
The Maximum number of Pods that can be unavailable (down) during the update.

maxSurge:
Maximum number of extra Pods Kubernetes can temporarily create above desired replicas.

To create the deployment
```
kubectl apply -f deployment.yaml
```
To check the rollout status
```
kubectl rollout status deployment web-app
```
To scale the deployment
```
kubectl scale deployment web-app --replicas=2
```
To update the image
```
kubectl set image deployment web-app nginx=nginx:1.26
```
To check the rollout history
```
kubectl rollout history deployment web-app
```
To rollback to particular revision
```
kubectl rollout undo deployment web-app --to-revision=<number>
```
To update the change-cause for rollout
```
kubectl annotate deployment/web-app kubernetes.io/change-cause="<reason>"
```
  
