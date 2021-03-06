# Kuberbetes Cluster 
Currently Kubernetes does not support master services for HA in multi-node cluster. This is to support master services run to another node using fleetctl & etcd service when a master node failed.

### Kubernetes Cluster Setup
This Cluster has two nodes as kube-01, kube-02
```
On Mac
$ cd cluster/kube
$ vagrant up
..............
..............
..............
..............
$ vagrant ssh kube-01

On CoreOS (kube-01)
$ cd /continuse/kube/bin
$ openssl genrsa -out kube-serviceaccount.key 2048
..............
..............
..............
..............
$ wget https://github.com/ContinUSE/openstack-on-coreos/releases/download/v1.1.2/kube_1.1.2.tgz
$ tar tvfz kube_1.1.2.tgz
```

### Kubernetes Service Start
```
On CoreOS
$ cd /continuse/kube/service
$ fleetctl start kube-apiserver.service
$ fleetctl start kube-controller-manager.service
$ fleetctl start kube-scheduler.service
$ fleetctl start kube-kubelet.service
$ fleetctl start kube-proxy.service
```

### Kubernetes Service for GUI Interface
```
$ cd /continuse/exsamples/kube-ui
$ kubectl create -f kube-system.yaml
$ kubectl create -f kube-ui-rc.yaml --namespace=kube-system
$ kubectl create -f kube-ui-svc.yaml --namespace=kube-system
```

## Kubernetes UI -- Web-based
```
http://192.168.10.12:8080/ui/           IP address of Kubernetes API Server Running
```

#### cAdvisor -- Web-based monitoring
```
http://192.168.10.71:4194/containers/    Each Kube Cluster node
```

**KUBERNETES_VERSION** v1..0.1

### Usage

If you want to test something exsamples, start with [Kubernetes examples]
(https://github.com/GoogleCloudPlatform/kubernetes/blob/master/examples/).
And I am trying yo make examples. See with [My Examples] (https://github.com/ContinUSE/kubernetes-coreos-cluster/tree/master/examples).
