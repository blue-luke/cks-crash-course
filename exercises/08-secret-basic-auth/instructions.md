# Exercise 8

A Pod needs username and password credentials for communicating with a third-party web service. Define a Secret for basic authentication and inject the credentials into the container as environment variables.

1. Create a new namespace named `d31`.
  Fine
2. Define a Secret named `api-basic-auth` of type `kubernetes.io/basic-auth` in the namespace `d31`. Set the key value-pairs `username=api-creds` and `password=bhj123as`.
  Fine, created in wrong ns initially
3. Create a Pod named `server-app` in the namespace `d31` with the image `nginx:1.18.0`. Inject the Secret credentials as environment variables. The keys should follow typical naming conventions for environment variables (all capital letters, underscore to separate words).
  Fine, had to manually add in the env var notation
4. Verify that the environment variables are available inside of the container.
  Fine, exec onto it. Variables persist after secret is deleted