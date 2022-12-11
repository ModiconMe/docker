### Docker Registries

Представляет собой систему для хранения Docker Images. Бывают **public** и **private**.
В репозитории могут быть много images. Можно подтягивать по одному.

* `docker push [IMAGE_NAME]` - пушим image в репозиторий
* `docker push modiconme/user-api:latest` - пушим image в репозиторий
* `docker pull` - подтягиваем image из репозитория
* `docker pull amigoscode/kubernetes:frontend-v1` - подтягиваем image из репозитория пользователя
  amigoscode, репозитория kubernetes, image frontend-v1
* `docker login` - вход в docker hub, чтобы работать с приватными репозиториями