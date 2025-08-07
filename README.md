# Workshop de Argo

## Limpieza de minikube
minikube delete --all --purge
minikube cache delete 

## Preparacion del enotorno local
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update

## Levantamos minikube
minikube start

## Instalamos Argo
kubectl create ns argocd
helm install argocd argo/argo-cd --version 3.35.4 -n argocd

## Obtengo pass de admin
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
