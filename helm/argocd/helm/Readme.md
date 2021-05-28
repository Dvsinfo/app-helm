# Creating a Helm chart
```
helm repo add argoproj https://argoproj.github.io/argo-helm
helm dep update .
```
# Installing the Argo CD Helm chart
```
kubectl create ns argocd

helm install argocd -n argocd . -f values.yaml \
      --set argo-cd.server.config.url=https://${BLOTOUT_LOGIN_URL} \
      --set argo-cd.dex.enabled=false \
      --set argo-cd.redis.enabled=false \
      --set argo-cd.server.ingress.enabled=true \
      --set argo-cd.server.ingress.hosts[0]=${BLOTOUT_LOGIN_URL}
```

# Uninstall Argo CD
```
helm del -n argocd argocd
```
