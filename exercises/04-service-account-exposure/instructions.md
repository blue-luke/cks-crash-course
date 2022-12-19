# Exercise 4

The cluster defines a ClusterRole and ClusterRoleBinding that map a Service Account for listing, watching, and deleting the API resources Pods, ConfigMaps, and Secrets. Two Pods defined in the namespace `k97` use the service account. You are tasked with reducing the permissions to the minimal set of permissions needed for the Pods based on the command running in the container.

1. Create the objects from the file [`setup.yaml`](./setup.yaml).
  Pods took a long time to be live. It was an autopilot cluster, and node autoscaling took minutes rather than seconds. Deleted previous deployments and then pods were scheduled a few minutes later
2. Inspect the Pods and wait until they transition into the "Running" status.
  Done
3. Check the logs for both Pods. You should see a success message.
  Done
4. Identify the operation that is not required and remove it from the configuration. 
  Only need to list pods and configmaps - don't need secrets, don't need deletion - I was correct here
  The roles and bindings should be namespace, rather than cluster wide, if that is sufficient - I overlooked this
  The RoleBindings have the below and I don't understand why it is necessary:
  roleRef:
  kind: ClusterRole
  name: pod-operations-clusterrole
  apiGroup: rbac.authorization.k8s.io

5. Identify which Pods requires which operation. Split up the RBAC configuration so that each Pod has its own definition on the namespace-level.
  Fine - thought experiment
6. Check the logs for both Pods. You should still see a success message.
  Fine - thought experiment

