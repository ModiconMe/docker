### Dockerfile

Для создания своих Docker Image используются специальные файлы описания - Dockerfile.
С помощью Dockerfile можно заменить docker volumes.

[Пример #1 Dockerfile](https://github.com/ModiconMe/docker/tree/main/dashboard/Dockerfile)
[Пример #2 Dockerfile](https://github.com/ModiconMe/docker/tree/main/user-api/Dockerfile)

* `docker build [dockerfile package] -t [tag] [image name]` - создает image из Dockerfile
* `docker build -t dashboard:latest -t dashboard:1 .` - создает image из Dockerfile. Определяем 2 тэга (latest, 1)
