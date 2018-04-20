

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
kubectl apply -f k8-dev-deployment.yaml
kubectl describe deployment pm2-nginx-server
```

# Changing contexts
```bash
kubectl config get-contexts
kubectl config use-context minikube
```

# Deployment
```bash
gcloud container clusters get-credentials <CLUSTER_NAME> --zone <ZONE> --project <PROJECT_ID>
kubectl create configmap pm2-nginx-config-map --from-file=nginx.conf=nginx/nginx.conf
kubectl apply -f k8-prod-deployment.yaml
kubectl get ingress pm2-nginx-server-ingress
```


# Local PROD debugging
```bash
kubectl proxy
kubectl config view
```
Open localhost:8001 in the browser. User token from the config view command