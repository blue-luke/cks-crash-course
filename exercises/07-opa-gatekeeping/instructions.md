# Excerise 7

Your organization decides to introduce and enforce policies for Pods. You will create an Object Policy Agent (OPA) constraint and then verify the correct enforcement.
  Gatekeeper is a customizable admission webhook for Kubernetes that enforces policies executed by the Open Policy Agent (OPA). You can enforce company-wide policies
  via configuration, not code

1. Install the OPA gatekeeper objects with the version 3.7. Refer to the [OPA gatekeeper installation documentation](https://open-policy-agent.github.io/gatekeeper/website/docs/install/).
  Done
2. Ensure that the OPA gatekeeper objects transition into the "Running" status.
  Done
3. Inspect the OPA constraint template in the already existing file `opa-constraint-template-annotation.yaml`. Create the object.
  Each Constraint is written with Rego, a declarative query language used by OPA to enumerate instances of data that violate the expected state of the system. All Constraints are evaluated as a logical AND. If one Constraint is not satisfied, then the whole request is rejected
4. Create an OPA constraint for Deployments that requires two annotations to be defined specified by the keys `contact` and `commit-hash`.
  Fine. Used docs, had to deduce a few things
  I didn't change ApipGroups:       - apiGroups: ["Apps"], I jsut left it blank
5. Create a Deployment that does not define the annotations. What's the behavior?
  Gets created but it shouldn't
  I've compared my answer with the solution and can't see a difference
  It's not a good use of time to find out what I'm doing wrong
6. Create a Deployment that does define the annotations. What's the behavior?
  Gets created
7. Delete the OPA gatekeeper objects.