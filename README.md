# gitops-demo

Manifests that [Argo CD](https://argo-cd.readthedocs.io/) keeps applied to the
`alilearn-aks` cluster.

**Git is the desired state.** Nothing here is deployed by pushing from a laptop
or a pipeline. A controller inside the cluster watches this repo and makes the
cluster match it — so anything changed by hand shows up as *OutOfSync* and gets
reverted, rather than becoming undocumented drift nobody finds for months.

Public on purpose: Argo CD then needs no credential to read it.

## Try it

```bash
kubectl scale deploy/hello -n demo --replicas=5     # change it by hand
kubectl get deploy/hello -n demo -w                 # watch Argo CD put it back
```
