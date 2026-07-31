# Kubernetes Pods

## What is a Pod?

A Pod is the smallest deployable unit in Kubernetes. It can contain one or more containers that share networking and storage.

## Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```

## Useful Commands

```bash
kubectl get pods
kubectl describe pod nginx-pod
kubectl logs nginx-pod
kubectl delete pod nginx-pod
```

## Key Point

Pods are ephemeral. In production, applications are normally managed through controllers such as Deployments rather than creating standalone Pods.

## Interview Questions

- What is a Pod?
- Can a Pod have multiple containers?
- Do containers in the same Pod share an IP?
- Why are Pods considered ephemeral?
