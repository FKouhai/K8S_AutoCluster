kube-master
=========

This role deploys the necesary components that a kubernetes master node needs, take into account this is after having installed the k8s binaries, this role:
 - Downloads the necesary pods that kubernetes needs aka the deployment of kube-system namespace.
 - Inits the master node with a given pod cidr and api address that is going to be advertised to the other nodes.
 - Gets the join token command on to the ansible server and stores it on /tmp/token.sh

Requirements
------------

This role needs to be used with the role named kube-common also found in this repo

Role Variables
--------------

This role needs the following variables from the vars directory

- podCIDR -> This variable refers to the pod network cidr that is going to be used in the cluster, note that this is the CIDR address and not 1 IP address
- apiAddr -> This variable refers to the Kubernetes API address that is going to be advertised for nodes that would join the cluster, note that this is the IP address of the master server



Example Playbook
----------------

The playbook used with this role looks something like the following:

```yaml
- hosts: master
  tasks:
  - import_role:
    name: kube-master
```
License
-------

BSD

Author Information
------------------

This Role was created by FKouhai aka a DevOps in Space, in case there is any doubt, or problem feel free to open a GH issue or contact me at Bulginess5273@protonmail.com
