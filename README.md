# Install kubernetes master-slave on ubuntu 16.04 or 18.04

## after install master, you must run 
```
$ kubectl -n kube-system edit service kubernetes-dashboard
```
Change type: 
```
type: ClusterIP to type: NodePort
```

### check dashboard port
```
$ kubectl -n kube-system get service kubernetes-dashboard
```
```
NAME                   TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)         AGE
kubernetes-dashboard   NodePort   10.152.183.101   <none>        443:32068/TCP   12m
```
### allow dashboard port
```
$ sudo iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 32068 -j ACCEPT
```
