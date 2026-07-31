# Kubernetes Ingress

## What is Ingress?

Ingress provides HTTP/HTTPS routing from outside the cluster to Services.

Typical flow:

```text
Internet
   |
   v
Ingress / Ingress Controller
   |
   +----> Service A ---> Pods
   |
   +----> Service B ---> Pods
```

## Important

Creating an Ingress resource normally requires an Ingress Controller to actually process the rules.

## Example

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: app-ingress
spec:
  rules:
    - host: app.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: nginx-service
                port:
                  number: 80
```

## Interview Questions

- Ingress vs Service?
- What is an Ingress Controller?
- How does host-based routing work?
- How would you configure TLS?
