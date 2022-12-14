## Контейнер

Контейнер это абстракция над приложением, которая упаковывает код(изолирует) и необходимые зависимости вместе. Для контейнеров не выделяются ресурсов, а они потребляют в зависимости от необходимости.

### Базовые команды для контейнера

#### Lifecycle
* `docker create` - создание контейнера
* `docker run` - создание и запуск контейнера
* `docker rm` - удаление контейнера по id или name
* `docker rename [OLD_NAME] [NEW_NAME]` - переименование контейнера
* `docker update` - обновление лимита ресурсов контейнера


* `docker run -d -p 8080:80 amigoscode/2048` - запуск контейнера из docker hub (port expose 8080 - порт на локальной машине, 80 - порт внутри контейнера, -d детач мод при котором мы не видим логов).
Можно определить несколько портов `docker run -p 8080:80 -p 5000:80 -p 3000:80 -d amigoscode/2048`, тогда на локальной машине приложение в контейнере будет доступно по этим портам.
* `docker run --name [CONTAINER_NAME]` - указываем имя контейнера при создании, потом можно будет управлять по имени
* `docker run --rm` - удалит контейнер после запуска
* `docker run -d -p 8080:80 --name dashboard-latest dashboard:latest` - запуск контейнера по версии

![alt text](https://github.com/ModiconMe/docker/blob/main/diagrams/docker-port-exposing.png "port-exposing")
***
#### Starting and Stopping

* `docker start` - запуск контейнера 
* `docker stop` - остановка контейнера
* `docker restart` - остановка и запуск контейнера
* `docker pause` - пауза контейнера
* `docker unpause` - снятие контейнера с паузы

Все команды могут выполнять по id или по имени (name) контейнера.
***
#### Info and util
* `docker ps` - информация о запущенных контейнерах
* `docker ps -a` - информация о всех контейнерах

* `docker exec -it [CONTAINER_ID] [CONTAINER_COMMAND]` - выполнение команд в контейнере (CTRL+D для выхода). На месте команды можно написать sh и откроется терминал контейнера.
* `winpty docker exec -it [CONTAINER_ID] sh` - выполнение команд в контейнере через windows bash

* `export FORMAT="ID\t{{.ID}}\nNAME\t{{.Names}}\nIMAGE\t{{.Image}}\nPORTS\t{{.Ports}}\nCOMMAND\t{{.Command}}\nCREATED\t{{.CreatedAt}}\nSTATUS\t{{.Status}}\n"` - красивый вывод для docker ps
* `docker ps --format=$FORMAT` - вывод согласно переменной FORMAT

* `docker inspect [CONTAINER_NAME]` - информация о контейнере
* `docker logs [CONTAINER_NAME]` - логи контейнера
* `docker logs [CONTAINER_NAME] -f` - логи контейнера в режиме просмотра

***
#### Docker network

Docker network позволяет контейнерам общаться друг с другом.

* `docker network create [NETWORK_NAME]` - создать network
* `docker network rm [NETWORK_NAME]` - удалить network
* `docker network ls` - показывает список всех network
* `docker inspect network [NETWORK_NAME]` - показывает данные о сети

Пример запуска контейнера с учетом network
```
docker run -d --network mongo --name mongo -p 27017:27017 \
-e MONGO_INITDB_ROOT_USERNAME=username \
-e MONGO_INITDB_ROOT_PASSWORD=password \
mongo:5.0.1
```

```
docker run -d --network mongo --name mongo-express -p 8081:8081 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=username \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongo \
mongo-express:latest
```

* `docker network create test` - создаем network
* `docker network connect test user-api` - подсоединяем первый контейнер к network
* `docker network connect test dashboard-v1` - подсоединяем второй контейнер к network
* `curl http://user-api:3000/api/v1/users` - вызываем один контейнер из второго

![docker-architecture](https://github.com/ModiconMe/docker/blob/main/diagrams/docker-network.png "docker-network")