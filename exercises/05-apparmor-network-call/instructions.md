# Exercise 5

You are tasked to prevent a Pod from making any network calls with the help of [AppArmor](https://apparmor.net/). You will create a AppArmor profile, and enforce the profile on the node that runs a specific Pod.

> **_NOTE:_** AppArmor is a Linux-only tool. For that reason, this exercise requires a cluster running on Linux. If you do not have a Linux-based cluster available, you can start one up with Vagrant and VirtualBox. You can find guidance in the file [vagrant-setup.md](../common/vagrant-setup.md).

1. Execute the following command in the cluster: `kubectl run network-call --image=alpine/curl:3.14 -- /bin/sh -c 'while true; do ping -c 1 google.com; sleep 5; done'`. If you are using the Vagrant setup then this will happen automatically.
  This didn't work, network calls outside cluster not permitted, as not root?
2. Check the logs of the Pod named `network-call`. What do you think the process running in the container is doing?
  Calling google every 5s
3. Create an AppArmor profile file named `network-deny`. The profile should not allow any network traffic. Reference the [documentation](https://gitlab.com/apparmor/apparmor/-/wikis/QuickProfileLanguage) for more information.
  Didn't know how to prevent networking. Use

  ```
#include <tunables/global>

profile network-deny flags=(attach_disconnected) {
  #include <abstractions/base>

  network,
}
```

4. Add the profile to the set of rules in enforce mode.
  Not sure where to specify enforce or complain. Perhaps ''' profile network-deny flags=(complain) 
5. Apply the profile to the Pod named `network-call` running in the `default` namespace. 
  Fine, see k8s docs
6. Check the logs of the Pod to ensure that network calls cannot be made anymore.
  Ping, should be fine