## Объекты в k8s

> containers 
*не являются по факту объектом куба, но без них никак*

> pod
*состоит из контейнера или нескольких контейнеров*
*1 под всегда исполняется только на одной ноде*

> deployment
*состоит из pod или pods, объединяет поды на разных нодах*

> service
*дает доступ к deployment(через: ClusterIP, NodePort, LoadBalancer, ExternalName)*

> nodes
*наши машины на которых испольняется кубер*

> cluster
*логическое объединение нодов*

> deamonSets

> statefulSets

> replicaSets

> secrets

> PV

> SVC

> loadBalancers

> configMaps

> vertical pod autoscaler

> horizontal pod autoscaler

> ingress
тип предоставления доступа
типо внутренний кубовый балансировщик, чтобы не платить за балансировщики клаудовские

## CMD & ENTRYPOINT переопределение в кубе
ENTRYPOINT - определяет вызываемый файл при запуске контейнера
CMD - задает аргументы которые перадаются в этот самый ENTRYPOINT (хотя можно все запустить с помощью CMD, хорошей практикой является с помощью ENTRYPOINT)

Различия форм, в exec файл запускается напрямую, в shell создается шелл который потом запускает файл, если приложение умеет принимать сигналы типо SIGTERM SIGKILL, то эти сигналы будет принимать в шелл форме шелл и не передаст в файл, exec использовать лучше
```
exec форма
ENTRYPOINT ["python3,"-u","server.py"]

shell форма
ENTRYPOINT python3 -u server.py
```

кубер может переопределить и ENTRYPOINT и CMD

## Helm scarts
