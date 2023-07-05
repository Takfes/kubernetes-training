### Why PODS?

In Kubernetes, a pod is the smallest and most basic unit of deployment. It represents a single instance of a running process in the cluster. A pod encapsulates one or more containers that are tightly coupled and share resources, such as network and storage namespaces, within the same host.

The primary purpose of a pod is to provide a cohesive and isolated environment for running one or more containers that work together. Containers within a pod are scheduled and deployed together on the same node, allowing them to communicate with each other using localhost. They also share the same lifecycle and are subject to the same resource management and scaling rules.

Here are a few key points about pods and their relationship with containers:

- **Pod as a wrapper**: A pod acts as a wrapper or a logical host for one or more containers. It provides a shared context for the containers running within it.

- **Colocated containers**: Containers within a pod share the same network namespace, allowing them to communicate over localhost. They can also share volumes for sharing data.

- **Shared resources**: Containers within a pod share CPU, memory, storage, and network resources. These resources are allocated collectively for the entire pod.

- **Atomic scheduling unit**: Pods are the atomic unit of scheduling in Kubernetes. The scheduler assigns pods to nodes, and all containers within the pod are deployed on the same node.

- **Tightly coupled**: Containers within a pod are intended to be tightly coupled and work together as a single cohesive unit. They often depend on each other and may need to communicate or share data.

- **Pod lifecycle**: Pods have their own lifecycle, and when a pod is created, containers within the pod are started simultaneously. They are also restarted together if the pod fails or is evicted.

By grouping containers within a pod, Kubernetes provides a way to manage and orchestrate closely related processes as a single unit, enabling efficient resource allocation and encapsulation.
