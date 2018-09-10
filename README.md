# Kubernetes testbed

This repo has been created as a simple vagrant based testbed to aid familiarizing yourself with Kubernetes

It uses `minikube` to deploy a Kubernetes in a single VM. After setting up Kubernetes it will deploy `helm` as well

## Prerequisites

- Vagrant >=1.8.6
- Ansible >=2.4
- Virtualbox >=5.0 or libvirt (for libvirt you need `VAGRANT_DEFAULT_PROVIDER=libvirt` in your env)

## Usage

Just do `vagrant up`

After `vagrant up` is done, you should be able to `vagrant ssh` and issue `kubectl get node` as vagrant user

Helm is also installed, you can test with `helm version`.

You will need to check with `kubectl get pods --namespace=kube-system` that all pods are in Running state, that's when Kubernetes is available.

```
14:31 $ vagrant ssh
Last login: Mon Sep 10 13:31:31 2018 from 192.168.121.1
[vagrant@m01 ~]$ kubectl get nodes
NAME       STATUS    ROLES     AGE       VERSION
minikube   Ready     master    29s       v1.10.0
[vagrant@m01 ~]$ kubectl get pods --namespace=kube-system
NAME                                    READY     STATUS    RESTARTS   AGE
etcd-minikube                           1/1       Running   0          22s
kube-addon-manager-minikube             1/1       Running   0          1m
kube-apiserver-minikube                 1/1       Running   0          54s
kube-controller-manager-minikube        1/1       Running   0          1m
kube-dns-86f4d74b45-jgrlp               3/3       Running   0          1m
kube-proxy-qc6l9                        1/1       Running   0          1m
kube-scheduler-minikube                 1/1       Running   0          47s
kubernetes-dashboard-5498ccf677-dwpk8   1/1       Running   0          1m
storage-provisioner                     1/1       Running   0          1m
tiller-deploy-67d8b477f7-vbwbm          1/1       Running   0          1m
[vagrant@m01 ~]$ helm version
Client: &version.Version{SemVer:"v2.10.0", GitCommit:"9ad53aac42165a5fadc6c87be0dea6b115f93090", GitTreeState:"clean"}
Server: &version.Version{SemVer:"v2.10.0", GitCommit:"9ad53aac42165a5fadc6c87be0dea6b115f93090", GitTreeState:"clean"}
```


