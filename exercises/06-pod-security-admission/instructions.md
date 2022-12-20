# Exercise 6

You are tasked with defining a Pod Security Admission rule that should control the creation of Pods in the namespace `k29`.

1. Create the namespace `k29`. In the namespace, define a Pod Security Standard (PSS) with the level `restricted` that will cause a Pod to be rejected upon violation.
  This is just a namespace with the below label in metadata:
    labels:
    pod-security.kubernetes.io/enforce: restricted
2. Create objects from the YAML manifests [`pod-non-root.yaml`](./pod-non-root.yaml), [`pod-root.yaml`](./pod-root.yaml), and [`pod-privileged.yaml`](./pod-privileged.yaml). Which of the Pods will be created and why?
  Only pod-non-root is created. The others request root access or privilege escalation that the PSS disallows

There have been upgrades and deprecations that muddied the waters here
But this did have the effect of helping my udnerstanding versions and deprecations

I needed to find https://kubernetes.io/docs/concepts/security/pod-security-standards/#policy-instantiation
then click on the restricted namespace link to get to https://raw.githubusercontent.com/kubernetes/website/main/content/en/examples/security/podsecurity-restricted.yaml 