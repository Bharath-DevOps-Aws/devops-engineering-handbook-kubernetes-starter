# Kubernetes Deployments

## What is a Deployment?

A Deployment manages application Pods through ReplicaSets and provides controlled application updates.

## Example

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.27
          ports:
            - containerPort: 80
```

## Update

```bash
kubectl set image deployment/nginx-deployment nginx=nginx:1.28
kubectl rollout status deployment/nginx-deployment
```

## Rollback

```bash
kubectl rollout undo deployment/nginx-deployment
```

## Interview Questions

- Deployment vs ReplicaSet?
- What happens during a rolling update?
- How do you rollback a Deployment?
- How do you check rollout status?
