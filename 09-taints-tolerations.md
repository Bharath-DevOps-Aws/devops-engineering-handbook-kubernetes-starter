# Taints and Tolerations

## Taint

A taint is applied to a Node to restrict which Pods can be scheduled there.

Example:

```bash
kubectl taint nodes node1 dedicated=backend:NoSchedule
```

## Toleration

A Pod can declare a matching toleration.

```yaml
tolerations:
  - key: dedicated
    operator: Equal
    value: backend
    effect: NoSchedule
```

## Important

A toleration allows a Pod to be scheduled onto a tainted node; it does not force the Pod onto that node.

For placement requirements, combine tolerations with mechanisms such as node affinity.

## Interview Questions

- What is a taint?
- What is a toleration?
- Does a toleration force scheduling?
- Difference between taints/tolerations and node affinity?
