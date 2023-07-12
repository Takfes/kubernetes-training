### The STARTERs

- `kubectl cluster-info`
- `kubectl run hello-minikube`

### The GETs

- `kubectl get <component>`
- where **`<component>`** can be any of `nodes`,`pods`,`replicasets`, `replicationcontroller`,`deployments`,`services` or `svc`
- `kubectl get pods,svc` to get POD and its service in one go
- `kubectl get pods -o wide`
- `kubectl get pod <pod-name> -o json`
- `kubectl get nodes -o=jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.status.nodeInfo.osImage}{"\n"}{end}'`
- `kubectl get pods --all-namespaces --no-headers | wc -l`
- `kubectl get pod webapp -o json | jq '.status.containerStatuses[] | select(.name == "agentx") .state'`

### The DESCRIBEs

- `kubectl describe pods`
- `kubectl describe nodes`
- `kubectl describe pod <pod-name>`
- `kubectl describe replicaset <replicaset-name>`
- `kubectl describe deployment <replicaset-name>`

### The CREATE

To **create components**:

- Using a YAML : `kubectl create -f pod-definition.yaml` or `kubectl apply -f pod-definition.yaml`
- In general `kubectl create -f <yaml file>`
- Directly from CLI : `kubectl run nginx-pod --image=nginx`

### The REPLICAs

There is ReplicationController (outdated) and ReplicaSet.
Some major differences:

- Replicaset : `apiVersion: apps/v1`
- Replicaset enables selectors through lables for more refiden control over PODS (pods may have been already deployed)

### The SCALING

- `kubectl replace -f rs-definition.yaml`
- `kubectl scale --replicas=6 -f rs-definition.yaml` which won't update the `rs-definition.yaml`
- `kubectl scale --replicas=6 replicaset myapp-replicaset` which won't update the `rs-definition.yaml`
- `kubectl scale replicaset myapp-replicaset --replicas=2`
- `kubectl edit replicaset myapp-replicaset` which will create a temporary file in memory. Any changes to this file will take immediate effect upon saving the file.

### The ROLLOUT/DEPLOYMENTS

- To **apply changes to a deployment** : `kubectl apply -f deployment-definition.yaml`
- `kubectl set image deployment/myapp-deployment nginx-container=nginx:1.9.1`
- `kubectl edit deployment myapp-deployment --record`
- To **rollback** a deployment : `kubectl rollout undo deployment/myapp-deployment`
- To record the change|cause of the deployment: `kubectl create -f deployment-definition.yaml --record`
- `kubectl rollout status deployment/myapp-deployment` to check deployment status
- `kubectl rollout history deployment/myapp-deployment` to check history and revisions
- `kubectl rollout undo deployment/<deployment name>`

### The SERVICEs

- `minikube service myapp-service --url`

### The DELETEs

- `kubectl delete pod <pod_name>`
- `kubectl delete replicaset myapp-replicaset` which will also delete underlying PODs
- `kubectl delete deployment <deployment_name>` e.g. deployment_name = myapp-deployment
