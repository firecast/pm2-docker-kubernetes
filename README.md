

# Create kubernetes configMap from file
```bash
kubectl create configmap pm2-nginx-config-map --from-file=nginx.conf=nginx/nginx.conf
```

# Check the configMap created
```bash
kubectl get configmaps pm2-nginx-config-map -o yaml
```

# Running it locally
```bash
minikube start --kubernetes-version v1.10.0
eval $(minikube docker-env)
docker build -t pm2-server server/
kubectl apply -f kube-development.yaml
kubectl describe deployment pm2-nginx-server
kubectl expose deployment pm2-nginx-server --port=80 --type=NodePort
```