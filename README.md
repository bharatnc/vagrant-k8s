### Create Vagrant Kubernetes Cluster

Provision Kubernetes cluster using Vagrant and Ansible. 

### Versions

This repo has been tested on:

```bash
$ vagrant --version
Vagrant 2.0.3

$ ansible --version
ansible 2.5.1
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/worker25-0/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.15+ (default, Nov 27 2018, 23:36:35) [GCC 7.3.0]

``` 

### Spinning up the cluster

```bash
# run this with the Vagrant file and other ansible files in the CWD
vagrant up
```


### Possible configurations

1. In the example `public IP addresses` are used. Alternatively private IPs can be used.
2. `WORKERS=?` - The number of worker nodes that needs to be provisioned can be changed as per the requirement.
3. `IMAGE_NAME=?` - The cluster uses `bento/ubuntu-16.04`. Alternative distros can be used. But the ansible tasks might need additional working.

