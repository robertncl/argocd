### argocd

install

```
kubectl create ns argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
Get admin password

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

login at localhost:80

add application

```
kubectl create ns apps
kubectl apply -f apps.yaml
```

add github actions runner controller (ARC)

```
kubectl apply -f arc-controller.yml

kubectl create ns arc-runners
kubectl create secret generic arc-github-secret -n arc-runners --from-literal=github_token='<PAT>'
kubectl apply -f arc-runner-set.yml
```

use in a workflow with `runs-on: arc-runner-set`
