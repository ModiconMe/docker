### Docker Compose

Специальный инструмент, который позволяем в одном файле описать конфигурацию 
наших контейнеров и запускать их из этого файла одной командой.

[Пример #1 Docker compose](https://github.com/ModiconMe/docker/tree/main/docker_compose/docker-compose.yml)

* `docker compose up -d` - запуск docker compose файла в фоновом режиме
* `docker compose down` - удаляет все docker compose контейнеры
* `docker compose start` - запускает все docker compose контейнеры
* `docker compose stop` - останавливает все docker compose контейнеры
* `docker compose rm` - удаляет все остановленные docker compose контейнеры
* `docker compose logs -f` - логи
