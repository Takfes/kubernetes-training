### minikube

Minikube is a tool that enables you to run a single-node Kubernetes cluster locally on your machine. A Minikube cluster provides a lightweight and convenient way to develop, test, and experiment with Kubernetes applications without the need for a full-scale production cluster.

Local Kubernetes Cluster: Minikube creates a single-node Kubernetes cluster that runs within a virtual machine on your local system. It simulates the functionality and behavior of a larger Kubernetes cluster.

**setup minikube on MacOS M1:**

- `brew install --cask docker`
- `brew install minikube`
- `minikube start --driver=docker`
- `minikube status`
- `brew install kubectl`
- `minikube stop`
- `minikube start`
