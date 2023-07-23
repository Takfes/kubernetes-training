### K8s COMPONENTS

<img src="https://www.ais.com/wp-content/uploads/2021/10/Master-Node-in-the-Kubernetes.png" alt="alt text" width="750">

1. **API Server**: The API server is the central management point of the Kubernetes control plane. It exposes the Kubernetes API, which allows users and other components to interact with the cluster. All administrative operations are handled through the API server.

2. **etcd**: etcd is a distributed key-value store that serves as the cluster's primary datastore. It stores the configuration data and state of the cluster, including information about pods, services, nodes, and more. etcd ensures consistent and reliable storage for cluster data.

3. **kubelet**: The kubelet is an agent that runs on each node in the cluster. It is responsible for managing the state of the node and ensuring that containers are running as expected. The kubelet communicates with the API server to receive instructions about which containers to run and monitors their health.

4. **Container Runtime**: The container runtime is the software responsible for running containers. Kubernetes supports various container runtimes such as Docker, containerd, and others. It provides the necessary environment to run containerized applications and manages the lifecycle of containers.

5. **Controller**: Controllers are responsible for maintaining the desired state of resources in the cluster. They monitor the cluster and make changes to ensure that the current state matches the desired state. Examples of controllers include the ReplicaSet controller, Deployment controller, and StatefulSet controller.

6. **Scheduler**: The scheduler is responsible for placing pods onto nodes in the cluster. It examines the resource requirements of pods and the available resources on each node to make intelligent decisions about pod placement. The scheduler helps achieve optimal resource utilization and load balancing.
