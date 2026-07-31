# Kubernetes ReplicaSets

## What is a ReplicaSet?

A ReplicaSet ensures that a specified number of Pod replicas are running.

## Example

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-rs
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
          image: nginx:latest
```

## Important Relationship

```text
ReplicaSet
    |
    +-- Pod
    +-- Pod
    +-- Pod
```

If one Pod disappears, the ReplicaSet creates another Pod to maintain the desired replica count.

## Interview Question

What is the difference between a ReplicaSet and a Deployment?

**Answer:** A ReplicaSet maintains the desired number of Pods. A Deployment manages ReplicaSets and provides declarative updates and rollout/rollback capabilities.
