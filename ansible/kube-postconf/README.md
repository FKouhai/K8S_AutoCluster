kube-postconf
=========

kube-postconf performs the following post config operations on the master node:

- It deploys Calico CNI 
- It deploys a Calico CRD so the specified pod CIDR could be used
- After having the CNI it reschedules the coredns pods that are living in kube-system namespace
- It also installs K9S a TUI to manage kubernetes resources


Requirements
------------

This role could be independent from previous roles, but it would be advisable to use it with:

- kube-common
- kube-master
- kube-worker

Role Variables
--------------

This role uses the podCIDR variable for the calico CRD config 

Dependencies
------------

This role relies on ansible standard modules

Example Playbook
----------------
The playbook used for this role looks something like this:

```yaml
    - hosts: master
      roles:
         - kube-postconf
```
License
-------

BSD

Notes
-----

Although this role execution may output a failed status, it performs all the steps correctly, since ansible doesnt seem to handle certain outputs really well it still is a WIP

Author Information
------------------

This Role was created by FKouhai aka a DevOps in Space
In case there is any doubt, or problem feel free to open a GH issue or contact me at Bulginess5273@protonmail.com
