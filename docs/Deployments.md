### Deployments

**Facts:**

- Kubernetes deployment will automatically create a replicaset and this in turn a series of PODs.
- There are different approaches to deployemnts.
- Recreate : take all the deployment down and then deploy the new version
- Rolling Update : is the default one; replace the old with the new component, one by one.

**Info:**

A Kubernetes Deployment is a higher-level resource in Kubernetes that provides declarative updates and management for a set of replica pods. It enables you to define and manage the desired state of your application by specifying how many replicas of a pod should be running and handles the process of creating, scaling, and updating the replicas.

Here are some key features and benefits of Kubernetes Deployments:

1. **Declarative Updates**: Deployments allow you to specify the desired state of your application, such as the number of replicas, container images, and configuration. Kubernetes will ensure that the current state matches the desired state and automatically perform any necessary updates.

2. **Rolling Updates and Rollbacks**: Deployments support rolling updates, which allow you to update your application without downtime by gradually replacing old replicas with new ones. If an update fails or causes issues, you can easily roll back to the previous version.

3. **Scaling and Self-Healing**: Deployments make it easy to scale your application by simply updating the replica count. Kubernetes will automatically adjust the number of replicas to match the desired state. If a replica fails, it will be automatically replaced, ensuring high availability.

4. **Versioning and History**: Deployments keep track of revision history, allowing you to view and manage different versions of your application. You can also roll back to previous revisions if needed.

5. **Service Discovery and Load Balancing**: Deployments work together with Kubernetes Services to provide service discovery and load balancing for the replicas. Services enable stable network access to the replicas, even as they scale up or down.

In summary, a Kubernetes Deployment provides a declarative and automated way to manage and update your application's replica pods. It simplifies the process of scaling, updating, and rolling back your application, while ensuring high availability and self-healing capabilities.
