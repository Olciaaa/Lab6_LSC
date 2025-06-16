# Lab6_LSC

## How to Run the Application

### Start Minikube

```bash
minikube start
```

### Install NFS Server Provisioner via Helm

```bash
helm repo add kvaps https://kvaps.github.io/charts
helm repo update

helm install my-nfs kvaps/nfs-server-provisioner \
  --namespace nfs-provisioner \
  --create-namespace
```

### Apply Kubernetes Manifests

```bash
kubectl apply -f manifests/pvc.yaml
kubectl apply -f manifests/nginx-deployment.yaml
kubectl apply -f manifests/nginx-service.yaml
kubectl apply -f manifests/copy-job.yaml
```

### Access the HTTP Server

```bash
minikube service nginx-service --url
```

Open the printed URL in your browser. You should see the web page content created by the Job
