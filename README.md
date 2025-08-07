# Workshop de Argo
Este workshop está orientado a perfiles Jr1 y Jr2 que quieran introducirse en el uso de ArgoCD y los principios de GitOps aplicados al despliegue continuo en Kubernetes.

**Objetivo**

Aprender los conceptos básicos de ArgoCD, su arquitectura, y cómo automatizar despliegues utilizando repositorios Git como fuente de verdad.

## Limpieza de minikube
```shell
minikube delete --all --purge
minikube cache delete 
```

## Preparacion del enotorno local
```shell
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
```

## Levantamos minikube
```shell
minikube start
```

## Instalamos Argo
```shell
kubectl create ns argocd
helm install argocd argo/argo-cd -n argocd
```

## Obtengo pass de admin
```shell
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
```