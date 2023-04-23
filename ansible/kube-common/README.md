kube-common
=========

kube-common performs the common tasks to deploy a kubernetes cluster on all nodes, master and workers

- Refreshes the current system wide repos
- Disables the hosts swap
- Performs a dist-upgrade
- Imports the docker repos
- Install containerd
- Makes the containerd config.toml be kubernetes ready
- Imports the kubernetes repos
- Installs the kubernetes base binaries(kubelet,kubeadm and kubectl)
- Enables the needed kernel modules
- Enables IPv4 forwarding

Requirements
------------

In order to run this role it is needed to perform a basic system config, such as:
- Network configuration
- Hostname setting
- DNS or /etc/hosts  setting so the nodes can reach each other via Hostname


Role Variables
--------------

This role doesnt use any sort of variables since it is thought to use containerd and install very basic packages, this could change in a future to provide support for other CRI.

Dependencies
------------

This role relies on ansible standard modules

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```yaml
    - hosts: all
      roles:
         - kube-common
```
License
-------

BSD

Author Information
------------------

This Role was created by FKouhai aka a DevOps in Space
In case there is any doubt, or problem feel free to open a GH issue or contact me at Bulginess5273@protonmail.com
