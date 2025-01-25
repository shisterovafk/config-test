

### Компоненты:
## 1) Pod 

   - Можно запустить под командой:
     Он создаст под  добавив туда метаинфрмацию
   
     `kubectl run hello --image=tomcat:8.5.38 --port=80`




## 2)  Deployment 

   - Команда для создания:
     Он создаст под + деплоймент добавив туда метаинфрмацию
   
     `kubectl create deployment infinispan --image infinispan/server:13.0`

   - Заскейлить деплоймент: изменить количество реплик

     `kubectl scale deployments infinispan  --replicas 3`

     Эта команда создала объект replicaSet:
     
     `kubectl get rs`
   - Создаем авто изменение кол подов:autoscale
      Те при 80% использования cpu он поидет его расширять.

     `kubectl autoscale deployments infinispan --min=1 --max=4 --cpu-percent=80`

     Эта комнда создает новый объект:HorizontalPodAutoscaler
     `kubectl get hpa`
   
     Точно так же можно обновлять image на рабочие деплойменты, он создаст новые поды и удалит старые.
     k8s хранит историю изменений деплойменты, можно переключаться(откатываться) на старые версии.

## 3) Service- для доступа к подам.

    -Типы:
    
      * clusterIp- создается по умолчанию. Доступ внутри кластера.
      * NodePort - порт для всех воркеров
      * ExternalName- dns
      * LoadBalancer- только для облаков, поднимается LB и прикрепляется к подам

    -Создать:

     `kubectl expose deployments tomcat-name-dep --type=ClusterIP --port=80`

## 4) INGRESS

Запускать несколько LoadBalancer оч дорого(может в ресурсах? вроде в облаках ты за них платишь), 
так что запускают 1 LB и за ним ставят Ingress Controller.

* Ingress Controller работает как маршрутизатор, чтоб заработал нужно создать Ingress Rules, чтоб контроллер знал к какому сервису ходить(сервис для связи с твоим приложением).
Те получается такая связка: 

<b> LB-> ingress controller -> service -> app </b>

* ingress controller уже много написанных, ingress-nginx, haproxy-ingress, Ambassador ...

[Сравнение Ingress Controller](https://docs.google.com/spreadsheets/d/191WWNpjJ2za6-nbG4ZoUMXMpUK8KlCIosvQB0f-oq3k/edit?gid=907731238#gid=907731238)

## 5) NetworkPolicy

### Спецификация сетевой политики

Спецификация сетевой политики Kubernetes включает в себя четыре элемента:

podSelector: определяет pod'ы, затрагиваемые этой политикой (цели) — обязательный;
policyTypes: указывает, какие типы политик включены в данную: ingress и/или egress — необязательный, однако я рекомендую его явно прописывать во всех случаях;
ingress: определяет разрешенный входящий трафик в целевые pod'ы — необязательный;
egress: определяет разрешенный исходящий трафик из целевых pod'ов — необязательный.


---

Запускает что угодно из yaml:

`kubectl apply/delete -f /Users/fkshistero/Documents/stydy/k8s/manifest/pod-min.yaml`

Узнать историю разворачивания или статус:
`kubectl rollout history/status Deployment/infinispan`