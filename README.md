# GitOps Demo Applications

Public desired-state repository used by the managed Flux and Argo CD workshop.

- `apps/flux-demo` is reconciled by the Azure-managed Flux extension.
- `apps/argocd-demo` is reconciled by the Azure-managed Argo CD extension.

The applications are intentionally similar but use separate namespaces so the controllers never compete for ownership.

## Demo workflow

1. Create a feature branch.
2. Change the version text in one application's `configmap.yaml`.
3. Open a pull request and wait for manifest validation.
4. Merge and observe the corresponding controller reconcile AKS.
5. Revert the commit to demonstrate auditable rollback.

## Validate locally

```bash
kubectl kustomize apps/flux-demo >/dev/null
kubectl kustomize apps/argocd-demo >/dev/null
```

Never commit credentials or plaintext Kubernetes `Secret` resources.
