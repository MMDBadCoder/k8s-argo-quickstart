# Deploy app on kubernetes cluster with using Argo-CD

To deploy Argo CD on your Kubernetes cluster and then use it to deploy your app from your GitHub repository, follow
these step-by-step instructions:

## Step 1: Install Argo

You can install Argo CD by applying the official YAML file.

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Use kubectl port-forward to forward the Argo CD server service's port to your local machine.

```bash
kubectl port-forward --address 0.0.0.0 svc/argocd-server -n argocd 8080:443
```

---

## Step 2: Log in to Argo CD

Username: admin

Password: Retrieve it with:

```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
``` 

---

## Step 3: Create the argo-cd app

Apply this YAML to create the Argo CD Application:

```bash
kubectl apply -f application.yaml
``` 

## Step 4: Test it

Execute this command to access to the nginx service.
```bash
sudo kubectl port-forward --address 0.0.0.0 service/nginx-service 80:80
``` 
