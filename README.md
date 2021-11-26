
## ArgoCD Kustomize K8S Demo ##

This demo supports the following workflow:

- The developer makes a change to `github/drug-search`, which triggers github actions to run. The docker image in docker hub will be updated.
- ArgoCD will be triggered to sync registered application `drug-search-argocd` to k8s clusters.

Reference: 
- https://github.com/kubernetes-sigs/kustomize/
- https://github.com/argoproj/argocd-example-apps/tree/master/kustomize-guestbook
- HowToArgoCDMinikube.odt

### Generate Yaml files ###

The yaml files are adapted from https://github.com/weifang993/dpd-kustomize

### Create a Kustomize app for Minikube (argcd app create --help) ###

- `kubectl create ns dpd`

From local github/dpd-kustomize-k8s directory, run

- `argocd app create drug-search-argocd --repo https://github.com/weifang993/dpd-kustomize-k8s.git --path ./base  --dest-namespace dpd --dest-server https://kubernetes.default.svc --kustomize-image weifang993/drug-search:latest`

- `kubectl port-forward service/drug-search 8090:8080 -n dpd`
- `http://localhost:8090`
