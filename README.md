# kube-agents-evals-large-gitops

An eval fixture for the kube-agents bench case `upgrades-api-deprecation-large-repo`
(gke-labs/kube-agents#4705). Do not use it for anything else.

- `vendor/charts/` holds about 40 MiB of random bytes that are not manifests, so the
  repository's tree is over the credential broker's snapshot ceiling (32 MiB of tar by
  default).
- `clusters/prod/pdb.yaml` is a PodDisruptionBudget on `policy/v1beta1`, an apiVersion
  removed in Kubernetes 1.25. The case expects the API deprecation scan to find it.
- `clusters/*/deployment.yaml` are ordinary `apps/v1` Deployments.

Changing these files changes what the case grades.
