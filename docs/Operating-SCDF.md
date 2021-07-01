# Operating Spring Cloud Data Flow

The following operations may be useful over the course of working with
SCDF.

### Kubectl interaction
Basic interaction via `kubectl`:
```
kubectl get all -l app=scdf-server
kubectl get svc scdf-server
```

### Deleting SCDF
Per the [SCDF kubernetes documentation], you can use the following 
command to remove SCDF.
```
kubectl delete all,cm -l app=scdf-server
```

### Re-deploying SCDF after a delete
If you've deleted SCDF, you can re-deploy it:
```
kubectl create -f src/kubernetes/server/server-config.yaml
sleep 10
kubectl create -f src/kubernetes/server/server-svc.yaml
sleep 10
kubectl create -f src/kubernetes/server/server-deployment.yaml
sleep 10
```

[SCDF kubernetes documentation]: https://dataflow.spring.io/docs/installation/kubernetes/kubectl/#deploy-data-flow-server