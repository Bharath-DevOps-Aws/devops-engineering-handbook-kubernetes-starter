# Kubernetes Architecture

## What is Kubernetes?

Kubernetes is an open-source platform for orchestrating containerized workloads.

It provides:
- Scheduling
- Service discovery
- Scaling
- Self-healing
- Rolling deployments
- Configuration management

## High-Level Architecture

A Kubernetes cluster contains:

### Control Plane
- API Server
- etcd
- Scheduler
- Controller Manager

### Worker Node
- kubelet
- Container runtime
- kube-proxy
- Pods

## Request Flow

```text
kubectl
   |
   v
API Server
   |
   +----> etcd
   |
   +----> Scheduler
   |
   +----> Controllers
             |
             v
        Worker Node
             |
           kubelet
             |
            Pod
```

## Interview Questions

1. What are the main Kubernetes control-plane components?
2. What is the role of etcd?
3. What does the scheduler do?
4. What is kubelet?
5. What happens when you run `kubectl apply -f deployment.yaml`?
