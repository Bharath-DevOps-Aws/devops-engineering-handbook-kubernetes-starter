# ConfigMaps and Secrets

## ConfigMap

Used to store non-sensitive configuration separately from application images.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_ENV: production
```

## Secret

Used for sensitive values such as credentials, tokens, or certificates.

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
type: Opaque
stringData:
  username: admin
  password: change-me
```

## Important

Kubernetes Secrets are not automatically equivalent to a full secrets-management solution. In production, consider encryption at rest and integrations such as an external secrets manager.

## Interview Questions

- ConfigMap vs Secret?
- How can a Pod consume a ConfigMap?
- How can a Secret be mounted?
- Are Kubernetes Secrets encrypted by default in etcd?
