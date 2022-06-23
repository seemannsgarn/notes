##### check versions
```
minikube --version
kubectl version --client
```

## minicube
> ограничения миникуба: 1 кластер, только с 1 нодом, он же мастер на котором запускаются контейнеры
```
minikube start --vm-driver=virtualbox
minikube start --cpus=4 --memory=8gb --disk-size=25gb --vm-driver=virtualbox
minikube status
minikube stop
minikube ssh
```
**shell users**
```
root
docker/tsuser
```

**clear local state**
```
minikube delete
```

## kubectl
**get information about a cluster**
```
kubectl get componentstatuses
kubectl cluster-info
kubectl get nodes
```
