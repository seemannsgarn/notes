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

