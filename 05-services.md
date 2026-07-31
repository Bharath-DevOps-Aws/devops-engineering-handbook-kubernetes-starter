# Kubernetes Services

## Why do we need a Service?

Pods are ephemeral. Their IP addresses can change when Pods are recreated.

A Service provides a stable virtual IP/DNS name and routes traffic to matching Pods.

## Traffic Flow

```text
Client
  |
  v
Service
  |
  +----> Pod
  +----> Pod
  +----> Pod
```

## Selector

```yaml
selector:
  app: nginx
```

The Service selects Pods whose labels match `app: nginx`.

## port vs targetPort vs nodePort

- `port`: Port exposed by the Service.
- `targetPort`: Port on the selected Pod/container.
- `nodePort`: Port exposed on each node for a NodePort Service.

Example:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30081
```

## Service Types

### ClusterIP
Default type. Accessible inside the cluster.

### NodePort
Exposes the Service through a port on each node.

### LoadBalancer
Requests an external load balancer from the cloud/provider integration.

## DNS

A Service can be reached using Kubernetes DNS, for example:

```text
nginx-service.default.svc.cluster.local
```

## Troubleshooting

```bash
kubectl get svc
kubectl describe svc nginx-service
kubectl get endpoints nginx-service
kubectl get pods --show-labels
```

A common problem is a selector that does not match Pod labels. In that case the Service can have no endpoints and traffic will not reach Pods.

## Interview Questions

- Why do we need a Service?
- ClusterIP vs NodePort vs LoadBalancer?
- What is a selector?
- What is the difference between port and targetPort?
- What happens to Service traffic when a Pod is recreated?
