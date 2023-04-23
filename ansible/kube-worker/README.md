kube-worker
=========

The kube-worker role is in charge of the following task:

- Join the worker nodes to the k8s cluster 



Requirements
------------

This role heavily relies on the following roles:

- kube-common for system wide common configs across the nodes that will be part of the k8s cluster.
- kube-master since kubernetes needs n number of master nodes to create a cluster, and the ansible server will copy /tmp/token.sh script to the worker nodes so they can join the cluster.

Role Variables
--------------

This role doesnt use any external variable since most components are hundled behind the courtins by previous roles

Dependencies
------------

This role uses ansible standard modules

Example Playbook
----------------

The playbook used to test this role looks something like this:

```yaml
    - hosts: workers
      roles:
         - kube-worker
```
License
-------

BSD

Author Information
------------------

This Role was created by FKouhai aka a DevOps in Space

In case there is any doubt, or problem feel free to open a GH issue or contact me at Bulginess5273@protonmail.com
