### Docker Image

Мы разрабатываем код (приложение), далее мы можем построить Docker Image. Из Docker Image мы уже можем запустить Docker Container.
Docker Image - шаблон для контейнеров, из одного шаблона можно создать много контейнеров.

**APP** --> _build_ --> **Image** --> _run_ --> **Container** (может быть много)

* `docker image ls` - список image
* `docker rm image [IMAGE_NAME]` - удаляет image по имени (не должно быть запущенных контейнеров)
* `docker rm image -f [IMAGE_NAME]` - удаляет image по имени
* `docker pull [IMAGE_NAME]:[IMAGE_VERSION]` - подтягивает image из репозитория (если не пишем :[IMAGE_VERSION], то подтянет latest)
* `docker inspect [IMAGE_NAME]` - информация о image

* `docker system prune -a` - удаляет все images и контейнеры

* `docker tag dashboard:latest dashboard:1` - добавляем новый tag(создаем новый image на основе latest)

* `docker scan` - сканирует docker image
***
У Docker image могут быть различные flavor.
Flavor - ОС на которой базируется image. Бывают различные flavor в зависимости от потребностей.

* **full offical image** - без flavor, использует последний стабильный Debian
* **stretch** - Debian 10.4
* **buster** - Debian 9
* **jessie** - Debian 8
* **slim** - урезанная версия full
* **alpine** - специальная Linux Alpine для контейнеров
* **windowsservicecore** - windows server OS
***
#### Docker scan

Помогает проверить Docker Images на безопасность.

* `docker scan [IMAGE_NAME]` - список image (default - snyk)
***
#### Distroless images

Специальные образы, которые включают в себя только необходимые для приложения зависмости,
и исключают стандартные (например shell). Эти образы имеют очень маленький размер.

* `docker scan [IMAGE_NAME]` - список image (default - snyk)
