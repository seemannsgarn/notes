check versions
```
minikube version
kubectl version --client
```

## minicube

*config path: ~/.minikube/*

> ограничения миникуба: 1 кластер, только с 1 нодом, он же мастер на котором запускаются контейнеры
```
minikube start --vm-driver=virtualbox
minikube start --cpus=4 --memory=8gb --disk-size=25gb --vm-driver=virtualbox
minikube status
minikube stop
minikube ssh
```

shell users
```
root
docker/tcuser
```
clear local state
```
minikube delete
```

## kubectl

*config path: ~/.kube/*

get information about a cluster
```
kubectl get componentstatuses
kubectl cluster-info
kubectl get nodes
```

## pods
`kubectl get pods`

*создать под из образа и открыть порт 80*
`kubectl run hello --image=mustafaevsl/k8s-php-test:latest --port=80`

*удалить под*
`kubectl delete pods hello`

kubectl describe pods hello

kubectl exec hello date

kubectl exec -it hell sh

kubectl logs hello

kubectl port-forward hello 1234:80