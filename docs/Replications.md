### Replicas

In Kubernetes, ReplicaController and ReplicaSet are both components used for managing and ensuring the desired number of replicas (copies) of a pod are running in the cluster. They serve similar purposes, but there are some differences between them.

**ReplicaController:**

- ReplicaController is an older version of the replication controller in Kubernetes.
- It is responsible for maintaining a specified number of replicas of a pod running at all times.
- ReplicaController uses the "label" selector to identify and manage the pods it controls.
- It supports only equality-based selectors.
- ReplicaController doesn't provide support for more advanced deployment strategies, such as rolling updates.
- It is recommended to use ReplicaSet or Deployment instead of ReplicaController in newer Kubernetes versions.

**ReplicaSet:**

- ReplicaSet is an improved version of ReplicaController.
- It performs the same role as ReplicaController, ensuring the desired number of pod replicas are running.
- ReplicaSet supports both equality-based and set-based selectors, providing more flexibility in pod selection.
- ReplicaSet allows more advanced deployment strategies, such as rolling updates and canary deployments, through its integration with Deployments.
- ReplicaSet is the recommended choice for managing pod replicas in newer Kubernetes versions.
- Deployments, which are higher-level resources, internally use ReplicaSet for managing the desired state of pods.

<br>

**More ReplicaSet:**

- ReplicaSet allows to select and manage already instantiated PODS
- In case the amount of selector-matched PODS is larger that the replicas argument, no new PODS will be created
- However, if a POD fails for any reason, ReplicaSet will spin-up a new POD based on the provided template; That's why we need to provide the POD-template even if the PODS are already deployed.
- Replicaset will always ensure the exact number of replicas running at any point in the cluster
- That is, if we delete a POD matching our replicaset selector, then the replicaset will create a new one so as to meet the replicas requirements
- Similarly, if we try to create a new POD matching the replicaset selector, this will be killed from the replicaset

---

**Summary:**

In summary, both ReplicaController and ReplicaSet are used for managing and maintaining the desired number of pod replicas in a Kubernetes cluster. However, ReplicaSet is the newer and more flexible version, offering advanced deployment strategies and supporting both equality-based and set-based selectors. It is recommended to use ReplicaSet or Deployment instead of ReplicaController for managing replicas in modern Kubernetes deployments.
