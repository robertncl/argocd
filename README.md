### argocd

install

kubectl create ns argocd

https://github.com/robertncl/argocd.git

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

Get admin password

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

login at localhost:80

add application

kubectl create ns apps
kubectl apply -f apps.yaml

