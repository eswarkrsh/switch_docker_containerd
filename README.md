# switch_docker_containerd

### Cordon Node (M and W) to stop further pod assignment

```
kubectl cordon <node_name>
```

### Drain Node (M and W) to evict running pods wich has a replica-set configured

```
kubectl drain <node_name> --ignore-daemonsets
```

### Login to the Node (SSH to the M and W node)

```
shh user@node_name
```
### Stop kubelet

```
systemctl stop kubelet
systemctl stop docker
apt remove --purge docker-ce docker-cli
```
### Edit containerD config file

```
vi /etc/containerd/config.toml
>>> comment disabled_plugins = ["cri"]
systemctl restart containerd
```
### ContainerD Initiate

```
vi /var/lib/kubelet/kubeadm-flags.env and edit
systemctl restart kubelet
```
