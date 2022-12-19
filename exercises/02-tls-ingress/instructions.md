# Exercise 2

You are tasked to create an Ingress with TLS termination. Create the relevant objects using the imperative or declarative approach.

> **_NOTE:_** Kubernetes requires running an Ingress Controller to evaluate Ingress rules. Make sure your cluster employs an [Ingress Controller](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/). You can find installation guidance in the file [ingress-controller-setup.md](./ingress-controller-setup.md).

Created the ingress using additional docs
1. Create the objects defined by the YAML manifest [`setup.yaml`](./setup.yaml). You will end up with a Deployment, multiple Pods, and a Service in the namespace `t75`.
  Done
  The cluster and the nodes have ips. But they are not kubernetes objects. We have an ingress as a kubernetes object to manage the configuration of entry to the cluster. In particular, we use to direct http traffic to cluster services
  We need an ingress controller as well as an ingress
2. Generate a TLS certificate and key using OpenSSL with the command `openssl req -nodes -new -x509 -keyout accounting.key -out accounting.crt -subj "/CN=accounting.tls"`.
  Clarify certificates
3. Create a Secret named `accounting-secret` of type `kubernetes.io/tls` in the namespace `t75`. Use the TLS certificate and key from the previous step.
  Fumbled through this
4. Create an Ingress named `accounting-ingress` in the namespace `t75`. Assign the Secret from the previous step to the host `accounting.internal.acme.com`. The Ingress is supposed to the route traffic to the Sevice named `accounting-service` on port 80 for the path `/accounting` of type `Prefix`.
  I was better able to parse and understand the kubectl command reference documents this time
  I didn't get the correct path, so had to add that in having checked the answer. Seems broadly okay though


There are several reasons why you might want to use an ingress in Kubernetes:

Load balancing: An ingress can distribute incoming traffic across multiple replicas of a service, providing load balancing and improving the availability of the service.

SSL/TLS termination: An ingress can terminate SSL/TLS connections, allowing the service to receive traffic over a secure connection without having to implement SSL/TLS termination itself.

Host and path-based routing: An ingress can route traffic based on the hostname or path of the request, allowing you to expose multiple services on the same IP address and DNS name.

Name-based virtual hosting: An ingress can route traffic based on the hostname of the request, allowing you to expose multiple services on the same IP address and DNS name using name-based virtual hosting.

While you could potentially use a cluster IP to expose a service to the outside world, an ingress provides additional features and flexibility that may not be available with a cluster IP alone.