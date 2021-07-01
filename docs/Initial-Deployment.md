# Deploying SCDF

To deploy, clone the SCDF git repo (***below***), then choose the
executive summary or detailed deployment:
* To deploy quickly, follow the [Executive Summary](#executive-summary)
* For detailed instructions, see [Detailed Deployment](#detailed-deployment) 

After deployment is complete, see [Using the Spring Cloud Data Flow Web UI] and 
[Using the Spring Cloud Data Flow shell]. 

### Clone SCDF git repo
First, clone the SCDF git repository, and checkout the appropriate branch
or tag for your needs
```
git clone https://github.com/spring-cloud/spring-cloud-dataflow
cd spring-cloud-dataflow
git checkout main

# Alternatively, checkout something specific
# i.e. a commit, branch, or tag corresponding
# to your needs.  For example:
#
# git checkout v2.7.2
```

### Executive Summary

Copy & paste the following to deploy all of SCDF to a 
fresh Kubernetes cluster (e.g. minikube):

```
kubectl create -f src/kubernetes/rabbitmq/
sleep 10
kubectl create -f src/kubernetes/mysql/
sleep 10
kubectl create -f src/kubernetes/server/server-roles.yaml
sleep 10
kubectl create -f src/kubernetes/server/server-rolebinding.yaml
sleep 10
kubectl create -f src/kubernetes/server/service-account.yaml
sleep 10
kubectl create -f src/kubernetes/skipper/skipper-config-rabbit.yaml
sleep 10
kubectl create -f src/kubernetes/skipper/skipper-deployment.yaml
sleep 10
kubectl create -f src/kubernetes/skipper/skipper-svc.yaml
sleep 10
kubectl create -f src/kubernetes/server/server-config.yaml
sleep 10
kubectl create -f src/kubernetes/server/server-svc.yaml
sleep 10
kubectl create -f src/kubernetes/server/server-deployment.yaml
sleep 10
```

### Detailed deployment

Start with RabbitMQ:
```
kubectl create -f src/kubernetes/rabbitmq/
```
Next, the database:
```
kubectl create -f src/kubernetes/mysql/
```
Roles:
```
kubectl create -f src/kubernetes/server/server-roles.yaml
# NB: This next command produces a warning.  Output is below:
#   
#   Warning: rbac.authorization.k8s.io/v1beta1 RoleBinding is deprecated in v1.17+, 
#   unavailable in v1.22+; use rbac.authorization.k8s.io/v1 RoleBinding
#    rolebinding.rbac.authorization.k8s.io/scdf-rb created
kubectl create -f src/kubernetes/server/server-rolebinding.yaml
kubectl create -f src/kubernetes/server/service-account.yaml
```
Skipper:
```
kubectl create -f src/kubernetes/skipper/skipper-config-rabbit.yaml
kubectl create -f src/kubernetes/skipper/skipper-deployment.yaml
kubectl create -f src/kubernetes/skipper/skipper-svc.yaml
```
Next, deploy the SCDF server:

```
# Additional information on this step is available on the web:
#  https://dataflow.spring.io/docs/installation/kubernetes/kubectl/#deploy-data-flow-server
kubectl create -f src/kubernetes/server/server-config.yaml
kubectl create -f src/kubernetes/server/server-svc.yaml
kubectl create -f src/kubernetes/server/server-deployment.yaml
```

### Additional resources

If you're stuck, refer to the official documenation, available here: 
https://dataflow.spring.io/docs/installation/kubernetes/kubectl/ . 


[Using the Spring Cloud Data Flow Web UI]: ./Using-SCDF-Web-UI.md
[Using the Spring Cloud Data Flow shell]: ./Using-SCDF-Shell.md
