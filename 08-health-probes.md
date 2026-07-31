# Kubernetes Health Probes

Kubernetes supports three important container health checks.

## Liveness Probe

Determines whether a container should be restarted.

Use it when an application can become unhealthy and recover by restarting.

## Readiness Probe

Determines whether a Pod should receive traffic.

If readiness fails, the Pod is removed from the Service's ready endpoints.

## Startup Probe

Gives slow-starting applications time to initialize before liveness/readiness checks take over.

## Example

```yaml
livenessProbe:
  httpGet:
    path: /health
    port: 8080
  initialDelaySeconds: 10
  periodSeconds: 10

readinessProbe:
  httpGet:
    path: /ready
    port: 8080
  initialDelaySeconds: 5
  periodSeconds: 5

startupProbe:
  httpGet:
    path: /startup
    port: 8080
  failureThreshold: 30
  periodSeconds: 10
```

## Key Difference

```text
Startup  -> Has the application started?
Readiness -> Can it receive traffic?
Liveness  -> Is it still healthy enough to keep running?
```

## Interview Questions

- Liveness vs readiness?
- Why use startup probes?
- What happens when readiness fails?
- What happens when liveness repeatedly fails?
