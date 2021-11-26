
## Kustomize Usage ##

Reference: https://github.com/kubernetes-sigs/kustomize/
https://github.com/argoproj/argocd-example-apps/tree/master/kustomize-guestbook

### Generate Yaml files ###

The yaml files are adapted from https://github.com/weifang993/dpd-kustomize

# Create a Kustomize app (argcd app create --help)

`kubectl create ns dpd`

From local github/dpd-kustomize-k8s directory, run
`argocd app create dpd-kustomize-k8s --repo https://github.com/weifang993/dpd-kustomize-k8s.git --path .  --dest-namespace dpd --dest-server https://kubernetes.default.svc --kustomize-image weifang993/drug-search:latest`
