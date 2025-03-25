# 🚀 Minikube and kubectl Lab Setup

## 📌 Introduction
Minikube and kubectl provide a simple way to run Kubernetes locally, enabling developers to test and manage Kubernetes clusters on their laptops. This guide walks you through setting up Minikube, deploying an application, and managing it using kubectl.

## ✅ Prerequisites
Before getting started, ensure you have the following installed:

1. **Minikube** 🏗️ - A tool that runs a local Kubernetes cluster inside a virtual machine.
2. **kubectl** 🖥️ - The command-line tool for interacting with Kubernetes clusters.

---

## 🔧 Installation Guide

### Step 1️⃣: Install Minikube and kubectl
#### 🏗️ Installing Minikube
- **Linux** 🐧:
  ```sh
  curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  sudo install minikube-linux-amd64 /usr/local/bin/minikube
  ```
- **macOS** 🍏:
  ```sh
  brew install minikube
  ```
- **Windows** 🖥️:
  ```sh
  choco install minikube
  ```

#### ⚙️ Installing kubectl
- **Linux/macOS**:
  ```sh
  curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
  chmod +x kubectl
  sudo mv kubectl /usr/local/bin/
  ```
- **Windows**:
  Download kubectl from the [official Kubernetes site](https://kubernetes.io/docs/tasks/tools/install-kubectl/) and add it to the system path.

---

## ⚙️ Setting Up Minikube and Kubernetes Cluster

### Step 2️⃣: Start Minikube
Initialize a local Kubernetes cluster:
```sh
minikube start
```
This starts a single-node Kubernetes cluster inside a virtual machine.

### Step 3️⃣: Verify Cluster
Check if Minikube is running correctly:
```sh
kubectl get nodes
```
✅ You should see a node with a `Ready` status.

---

## 🚀 Deploying and Managing Applications

### Step 4️⃣: Create a Deployment
Deploy an **nginx** web server:
```sh
kubectl create deployment nginx --image=nginx
```
This creates a deployment named `nginx` using the official nginx image.

### Step 5️⃣: Expose the Deployment
Expose the deployment through a service:
```sh
kubectl expose deployment nginx --type=NodePort --port=80
```
This creates a service that makes the application accessible on a random NodePort (range 30000-32767).

### Step 6️⃣: Get the URL for Access
Retrieve the service URL:
```sh
minikube service nginx --url
```
📌 Example output:
```
http://192.168.99.100:30001
```
Open this URL in your browser 🌐 to see the running **nginx** server.

### Step 7️⃣: Check Running Pods
View running pods:
```sh
kubectl get pods
```
✅ You should see the nginx pod with a `Running` status.

### Step 8️⃣: Scale the Deployment
Increase the number of replicas to 3️⃣:
```sh
kubectl scale deployment nginx --replicas=3
```
Verify the scaling:
```sh
kubectl get pods
```
✅ You should now see **three** running nginx pods.

### Step 9️⃣: Delete the Deployment
To clean up, delete the deployment and service:
```sh
kubectl delete service nginx
kubectl delete deployment nginx
```

---

## 📌 Summary of Commands
```sh
# 🚀 Start Minikube
minikube start

# ✅ Verify Minikube and Kubernetes cluster status
kubectl get nodes

# 🏗️ Create a deployment for nginx
kubectl create deployment nginx --image=nginx

# 🔓 Expose the nginx deployment
kubectl expose deployment nginx --type=NodePort --port=80

# 🔗 Get the URL of the exposed service
minikube service nginx --url

# 📊 Check the status of running pods
kubectl get pods

# 📈 Scale the nginx deployment to 3 replicas
kubectl scale deployment nginx --replicas=3

# 🗑️ Clean up (delete service and deployment)
kubectl delete service nginx
kubectl delete deployment nginx
```

---

## 🎯 Conclusion
Using **Minikube** and **kubectl**, you can quickly set up a local Kubernetes cluster, deploy applications, scale them, and manage their lifecycle. Minikube is an excellent tool for development and testing before moving workloads to a production environment.

📚 For further details, refer to:
- The [official Minikube documentation](https://minikube.sigs.k8s.io/docs/) 📘
- The [Kubernetes official documentation](https://kubernetes.io/docs/home/) 🔗

