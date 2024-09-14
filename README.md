# Kubernetes Ingress and Website Deployment

## Overview

This repository demonstrates the deployment of multiple websites on Kubernetes using Ingress controllers. It includes configurations for both path-based and host-based routing, and secures the websites using TLS certificates.

## Prerequisites

- Kubernetes cluster (Minikube or another Kubernetes provider)
- kubectl command-line tool
- Docker (for building images, if needed)
- Helm (optional, for managing Kubernetes applications)
- A domain for host-based routing (e.g., `website1.local`)

## Getting Started

### 1. **Setup Kubernetes Ingress Controller**
Deploy your websites by creating the necessary Kubernetes Deployment and Service manifests.

'''bash

kubectl apply -f website1-deployment.yaml
kubectl apply -f website1-service.yaml

# apply ingress.yml place in host-based/path-based-routing folder each
kubectl apply -f ingress.yml

kubectl apply -f ingress_path_tls.yml

### Ingress:
Ensure you have an Ingress controller installed in your Kubernetes cluster. For this repository, we use the Nginx Ingress controller.
Configure Path-Based and Host-Based Routing
    Path-Based Routing: Set up an Ingress resource to route traffic based on URL paths.
    Host-Based Routing: Configure an Ingress resource to route traffic based on hostnames.

Create a TLS Secret with your SSL certificate and private key.

### Notes:

- Customize the paths and hostnames according to your setup.
- Ensure your Ingress YAML files and certificate files are correctly named and located.
- Add any additional setup or deployment instructions specific to your project.

Feel free to modify and expand this template to fit your needs!
Feel free to fork this repository and submit pull requests with improvements or additional features.


