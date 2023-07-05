### The STARTERS

`kubectl cluster-info`

`kubectl run hello-minikube`

### The GET

`kubectl get nodes`

`kubectl get pods -o wide`

`kubectl get pod <pod-name> -o json`

`kubectl get nodes -o=jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.status.nodeInfo.osImage}{"\n"}{end}'`

`kubectl get pods --all-namespaces --no-headers | wc -l`

`kubectl get pod webapp -o json | jq '.status.containerStatuses[] | select(.name == "agentx") .state'`

### The DESCRIBE

`kubectl describe pods`

`kubectl describe nodes`

`kubectl describe pod <pod-name>`

`kubectl describe replicaset <replicaset-name>`

### The CREATE

```{yaml}
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
    - name: nginx-container
      image: nginx
```

Using a YAML : `kubectl apply -f pod-definition.yaml`

Directly from CLI : `kubectl run nginx-pod --image=nginx`

### The REPLICATIONS

There is ReplicationController (outdated) and ReplicaSet.
Some major differences:

- Replicaset : `apiVersion: apps/v1`
- Replicaset enables selectors through lables for more refiden control over PODS (pods may have been already deployed)

```{yaml}
...
selector:
    matchLabels:
      type: frontend
```

`kubectl create -f rc-definition.yaml`

`kubectl create -f rs-definition.yaml`

`kubectl get replicationcontroller`

`kubectl get replicaset`

### How to SCALE

`kubectl replace -f rs-definition.yaml`

`kubectl scale --replicas=6 -f rs-definition.yaml` which won't update the `rs-definition.yaml`

`kubectl scale --replicas=6 replicaset myapp-replicaset` which won't update the `rs-definition.yaml`

`kubectl scale replicaset myapp-replicaset --replicas=2`

`kubectl edit replicaset myapp-replicaset` which will create a temporary file in memory. Any changes to this file will take immediate effect upon saving the file.

### The DELETE

`kubectl delete pod <pod_name>`

`kubectl delete replicaset myapp-replicaset` which will also delete underlying PODs
