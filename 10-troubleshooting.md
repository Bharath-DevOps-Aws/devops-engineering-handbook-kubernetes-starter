# Kubernetes Troubleshooting

## 1. Pod is Pending

Check:

```bash
kubectl describe pod <pod>
kubectl get nodes
kubectl get events --sort-by=.lastTimestamp
```

Common causes:
- Insufficient CPU/memory
- Node constraints
- Taints without matching tolerations
- Storage/PVC issues

## 2. CrashLoopBackOff

Check:

```bash
kubectl logs <pod>
kubectl logs <pod> --previous
kubectl describe pod <pod>
```

Common causes:
- Application exits
- Wrong command/arguments
- Missing configuration
- Dependency failure
- Failed health checks

## 3. Service Has No Traffic

Check:

```bash
kubectl get svc
kubectl describe svc <service>
kubectl get endpoints <service>
kubectl get pods --show-labels
```

A common issue is a selector mismatch.

Example:

```text
Service selector:
app: nginx

Pod label:
app: apache
```

The Service will not select that Pod.

## 4. Pod is Running but Not Ready

Check:

```bash
kubectl describe pod <pod>
kubectl logs <pod>
```

Focus on readiness probe failures and application dependencies.

## Production Troubleshooting Approach

```text
Observe
  ↓
Identify affected resource
  ↓
Check events
  ↓
Check logs
  ↓
Check configuration
  ↓
Check networking/dependencies
  ↓
Validate the fix
  ↓
Monitor
```

## Interview Scenarios

### Scenario: Service exists but traffic is not reaching Pods

Check:

1. Service selector
2. Pod labels
3. Service endpoints
4. Pod readiness
5. targetPort
6. Application listening port
7. Network policies, if present
8. Ingress/load balancer configuration, if traffic originates externally
