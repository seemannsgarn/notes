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
minikube addons list
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

# pods
получить информацию о нодах
```
kubectl get pods
```
создать под из образа и открыть порт 80
```
kubectl run hello --image=mustafaevsl/k8s-php-test:latest --port=80
```
удалить под
```
kubectl delete pods hello
```
получить полную информацию о поде
```
kubectl describe pods hello
```
запустить команду на поде
```
kubectl exec hello date
```
запустить шелл пода
```
kubectl exec -it hell sh
```
получить лог
```
kubectl logs hello
```
перенаправить порт пода на порт сервера
```
kubectl port-forward hello 1234:80
```
создать под из манифеста
```
kubectl apply -f filename
```
# deployments
```
kubectl get deploy
kubectl create deployment deployName --image nginx:latest
kubectl describe deployments deployName
kubectl scale deployment deployName --replicas 4
kubectl get rs 
```
дополнительно используется технология hpa(horizontal pod autoscaler)
триггер скейлинга по значению 80% нагрузки проца, со всех pods, т.е. параметр TARGETS ставновится 80, добавляется еще под
```
kubectl autoscale deployment deployName --min=4 --max=8 --cpu-percent=80
kuberctl get hpa
```
история деплоя
```
kubectl rollout status deployment/deployName
kubectl rollout history deployment/deployName
```
изменить image в деплое
```
kubectl set image deployment/deployName containerName=newContainerName:version --record
```
вернутся к прошлой версии
```
kubectl rollout undo deployment/deployName
kubectl rollout undo deployment/deployName --to-revision=4
```
обновили image, версия latest изменилась, как обновить
```
kubectl rollout restart deployment/deployName
```

# services
services types:
- ClusterIP - IP только внутри k8s cluster(default)
- NodePort - определенный порт доступен на всех k8s worker nodes
- ExternalName - DNS CNAME Record
- LoadBalancer - только в cloud clusters(aws,GCP,azure)

выставляем деплой на 80 порт
```
kubectl expose deployment deployName --type=ClusterIP --port 80
kubectl expose deployment deployName --type=NodePort --port 80
kubectl expose deployment deployName --type=LoadBalancer --port 80
kubectl get services
kubectl get svc
kubectl delete service deployName
```

# ingress
по-умолчанию выключен, позволяет балансировать трафик на поды
может работать на несколько хостов
```
minikube addons enable ingress
kubectl get ing --all-namespaces
```

# 