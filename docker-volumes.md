## Docker Volumes

Позволяет смаппить (bind) папку на сервере (host) с папкой в контейнере. Используется для local development.

* `docker run --name dashboard -v [local_path]:[container_path] -d -p 8080:80 [image name]` - маппим папку на сервере (host, локальная машина) с папкой в контейнере
* `docker run --name dashboard -v //c/Users/rebee/dashboard:/usr/share/nginx/html -d -p 8080:80 nginx` - пример указания пути на host=windows, container=unix
* `docker run --name dashboard -v %PWD:/usr/share/nginx/html -d -p 8080:80 nginx` - пример указания пути на host=unix, container=unix (где $PWD выдает путь к текущей папке)

![alt text](https://github.com/ModiconMe/docker/blob/main/diagrams/docker-volumes.png "docker-volumes")

![alt text](https://github.com/ModiconMe/docker/blob/main/diagrams/docker-volumes-types.png "docker-volumes-types")
