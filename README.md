# Mini Spring Cloud Data Flow

> Deploy Spring Cloud Data Flow to local Kubernetes via minikube.

Spring Cloud Data Flow (or SCDF), can be deployed to Kubernetes, locally
using [minikube](https://minikube.sigs.k8s.io/docs/).  As such, you
should be able to use it on Linux and Windows.  Here, we'll focus
on a macOS deployment.


### Minikube
To begin, install minikube:
```
brew install minikube
```
Next, launch a VM and specify the CPU & memory required.
```
minikube start --cpus=4 --memory=8192 --driver=virtualbox
```
### Deployment via Kubernetes YAML
Deployment is performed using YAML configuration files provided
by the SCDF project.  You'll need to clone the SCDF git repository.

Follow the remaining deployment steps in [docs/Initial-Deployment.md](docs/Initial-Deployment.md)
