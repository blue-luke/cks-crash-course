# Exercise 3

You logged into a Kubernetes clusters and are planning to verifying the validity of the Kubernetes binaries `kubectl`, `kubeadm`, and `kubelet`. Use the SHA256 checksums for comparison.

> **_NOTE:_** Consult the OS-specific commands in the [Kubernetes documentation](https://kubernetes.io/docs/tasks/tools/#kubectl) for reference. You may have to install SHA checksum tool depending on your operating system. On MacOSX use the tool `shasum`, on Linux use the tool `sha256sum`. Use the tool `certutil` if you are working on Windows.

1. Create the directory named `kubernetes-bin`. Navigate to the directory.
  Skipped
2. Copy the script `setup.sh` into the new directory and run it. It will download the Kubernetes binaries for Linux AMD64.
  Did manually
3. Inspect the downloaded files.
  Did sah156sum FILENAME
4. Verify that the downloaded binaries are compatible with the Kubernetes version 1.23.5 by comparing them with the corresponding checksum files.
  The instructions use different syntax
  You could echo both checksums into a dox and then run cat FILE | uniq or cat FILE | uniq | wc -l
