### The STARTERs

- `kubectl cluster-info`
- `kubectl api-resources`
- `kubectl explain node.spec`
- `minikube service myapp-service --url`

### The GETs & DESCRIBEs

- `kubectl get --help`
- `kubectl get pods,svc` to get POD and its service in one go
- `kubectl get pods -o wide`
- `kubectl get pod <pod-name> -o json`
- `kubectl get nodes -o=jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.status.nodeInfo.osImage}{"\n"}{end}'`
- `kubectl get pods --all-namespaces --no-headers | wc -l`
- `kubectl get pod webapp -o json | jq '.status.containerStatuses[] | select(.name == "agentx") .state'`
  <br><br>
- `kubectl describe <ResourceType>`
- `kubectl describe <ResourceType>/<ResourceName>`
- `kubectl describe <ResourceType> <ResourceName>`

### The IMPERATIVEs

- `kubectl run nginx --image=nginx:apline nginx-pod --dry-run=client -o yaml > nginx-pod.yaml`
- `kubectl run custom-nginx --image=nginx --port=8080`
- `kubectl run httpd --image=httpd:alpine --port=80 --expose`
  <br><br>
- `kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml`
- `kubectl expose pod nginx --port=80 --name nginx-service --type=NodePort --dry-run=client -o yaml`
- `kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml`
- `kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml`
  <br><br>
- `kubectl create deployment --image=nginx nginx`
- `kubectl create deployment nginx --image=nginx --replicas=4`
- `kubectl scale deployment nginx --replicas=4`
- `kubectl create deployment nginx --image=nginx--dry-run=client -o yaml > nginx-deployment.yaml`
- `kubectl create deployment pingpong --image alpine -- ping 1.1.1.1`
- `kubectl create deployment redis-deploy --image=redis --replicas=2 --namespace=dev-ns`
  <br><br>
- `kubectl create namespace dev-n`
- `kubectl create configmap app-config --from-literal=APP_COLOR=blue`
- `kubectl create configmap app-config --from-file=<path-to-file>`

### The SECRETS

- `kubectl create secret generic <secret-name> --from-literal=DB_HOST=my_sql`
- `echo -n 'takmers' | base64`
- `echo -n 'dGFrbWVycw==' | base64 --decode`

### The ROLLOUT/DEPLOYMENTS

- To **apply changes to a deployment** : `kubectl apply -f deployment-definition.yaml`
- `kubectl set image deployment/myapp-deployment nginx-container=nginx:1.9.1`
- `kubectl edit deployment myapp-deployment --record`
- To **rollback** a deployment : `kubectl rollout undo deployment/myapp-deployment`
- To record the change|cause of the deployment: `kubectl create -f deployment-definition.yaml --record`
- `kubectl rollout status deployment/myapp-deployment` to check deployment status
- `kubectl rollout history deployment/myapp-deployment` to check history and revisions
- `kubectl rollout undo deployment/<deployment name>`

### The MISC

**Creates**:

- Using a YAML : `kubectl create -f pod-definition.yaml` or `kubectl apply -f pod-definition.yaml`
- In general `kubectl create -f <yaml file>`
- Directly from CLI : `kubectl run nginx-pod --image=nginx`

**Edits**:

- `kubectl get po --dry-run=client -o yaml`
- `kubectl scale deployment nginx --replicas=4`
- `kubectl scale replicaset.apps/new-replica-set --replicas=5`
- `kubectl edit replicaset.apps/new-replica-set`
- `kubectl edit pod <pod name>`

**Taints**:

- `kubectl taint nodes <node-name> key1=value1:NoSchedule` alternative actions : NoSchedule | PreferNoSchedule | NoExecute

**Namespace**:

- `kubectl create namespace <name>`
- `kubectl config current-context`
- `kubectl config view --minify | grep namespace`
- `kubectl config set-context --current --namespace=default`

**Replicas**:

- There is ReplicationController (outdated) and ReplicaSet.
- Replicaset : `apiVersion: apps/v1`
- Replicaset enables selectors through lables for more refiden control over PODS (pods may have been already deployed)

**Access Logs**:

- `kubectl logs deploy/<deploymentname>`
- `kubectl logs deploy/<deploymentname> --tail 1 --follow`

**Scaling**:

- `kubectl scale --replicas=6 -f rs-definition.yaml` which won't update the `rs-definition.yaml`
- `kubectl scale --replicas=6 replicaset myapp-replicaset` which won't update the `rs-definition.yaml`
- `kubectl scale replicaset myapp-replicaset --replicas=2`
- `kubectl replace -f rs-definition.yaml`
- `kubectl edit replicaset myapp-replicaset` which will create a temporary file in memory. Any changes to this file will take immediate effect upon saving the file.
