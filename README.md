K8s_Autodeploy
--------------

This repository is based on the following structure


 - Vagrantfile -> The file used to automatically spin up 3 VMs using the vbox driver<br/>
|<br/>
|<br/>
- ansible/* -> This directory contains all the roles and playbooks used to provision the cluster

Vagrantfile
-----------

This file consists in a multivm file with a static IP address provisioned for each VM to be able towork properly

Please note that the following steps can be done manually:

- Unlink /etc/resolv.conf file so the systemd unit doesnt refreshes it every now and then
- Set the hostname of each node
- Set the /etc/hosts (optional) so it includes the hostname:ipaddress binding for each node within the cluster 

Ansible
-------

This directory contains the roles and playbooks used to set up the cluster, a brief summary of it would be:

- ansible/*.yaml those are all the playbooks used to test the deployment
- kube-common -> role to set up the basic needs of the 3 nodes
- kube-master -> role in charge to init the cluster
- kube-worker -> role in charge to make the worker nodes join the cluster 
- kube-postconf -> role in charge to perform postconfig operations cluster wide

How-To
------
First of all virtualbox, vagrant and ansible should be installed in your system.

In order to bring up the vagrant machines you need to run: 

```bash
vagrant init#Remember to save the Vagrantfile before doing that cause running the init will override the file
vagrant up 
```

Then after the VMs are up and ready, perform the manual stuff or automate it(there is a playbook that is a WIP to do so)

Feel free to change stuff in the Vagrantfile so it suits your network requierements.

Then you need to create an ansible inventory with the proper format for vagrant
Then you can run the playbook deploy-all.yaml to perform the cluster tasks, to do so:

```bash
cd ansible 
ansible-playbook -i /path/to/inventory deploy-all.yaml
```
If you would prefer a more step by step procedure you can do the following:
```bash
cd ansible

ansible-playbook -i /path/to/inventory playbook.yaml
ansible-playbook -i /path/to/inventory master.yaml
ansible-playbook -i /path/to/inventory worker.yaml
ansible-playbook -i /path/to/inventory postconf.yaml

```

Also note that each role directory contains its own readme which explains the meaning of the role and its usage.

It is also worth to mention that these playbooks arent enterprise ready, what I mean by that is, that the proxy nor its envars has been set up anywhere in this deployment that part is also a WIP to make the roles enterprise ready.

License
-------
BSD 

Author
------
This Repo was created by FKouhai aka a DevOps in Space
In case there is any doubt, or problem feel free to open a GH issue or contact me at Bulginess5273@protonmail.com
