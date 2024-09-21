# Setup Kubernetes on Docker using Kind

This guide helps you to set up a simple Kubernetes cluster using `kind` (Kubernetes IN Docker) on a Linux system.

## Step 1: Install Docker

Install docker to run kind on it

```bash
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

Ensure Docker is installed and running on your system.

```bash
docker --version
```

Make sure your user has permission to run Docker without sudo:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

---

## Step 2: Install kind

Install kind by downloading the binary and moving it to a directory in your PATH.

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

Verify that kind is installed successfully:

```bash
kind --version
```

---

## Step 3: Create a Kubernetes Cluster with kind

Create a Kubernetes cluster using kind. This command will create a single-node cluster inside Docker.

```bash
kind create cluster

## Step 4: Install kubectl

Download the latest kubectl binary and move it to bin directory:
``````bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
```

Verify kubectl installation:

``````bash
kubectl version --client
kubectl get nodes
```