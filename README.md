# Vagrantfile and Scripts to Automate Kubernetes Setup using Kubeadm 

## Documentation
Original REPO and docs can be found here: 
    https://devopscube.com/kubernetes-cluster-vagrant/

If you are preparing for CKA, CKAD or CKS exam, save $57 using code **DCUBEOFFER** at https://kube.promo/latest


## Prerequisites

1. Working Vagrant setup
2. 8 Gig + RAM workstation as the Vms use 3 vCPUS and 4+ GB RAM
3. VMware Fusion
 
## Usage/Examples

To provision the cluster, execute the following commands.

```shell
git clone https://github.com/itlinux/vagrant-k8
cd vagrant-k8
vagrant up
```

## Set Kubeconfig file varaible.

```shell
cd vagrant-k8
cd configs
export KUBECONFIG=$(PWD)/config
```

or you can copy the config file to .kube directory.

```shell
cp config ~/.kube/
```

## Kubernetes Dashboard URL

```shell
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=kubernetes-dashboard
```

## Kubernetes login token

Vagrant up will create the admin user token and saves in the configs directory.

```shell
cd vagrant-k8
cd configs
cat token
```
## Helm
I have added HELM, so it's easy to install ingress or other services using the nice helm tool. 

## To shutdown the cluster, 

```shell
vagrant halt
```

## To restart the cluster,

```shell
vagrant up
```

## To destroy the cluster, 

```shell
vagrant destroy -f
```

## Centos & HA based Setup

If you want Centos based setup, please refer https://github.com/marthanda93/VAAS
  

## Credit 
The original repo comes from 
    https://github.com/scriptcamp/vagrant-kubeadm-kubernetes

I have applied some changes to what I see fit better on my use. 
