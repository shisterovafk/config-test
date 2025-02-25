# Docker compose

[Yandex.Wiki.Docker Compose](https://wiki.yandex.ru/homepage/work/technologies/docker/docker-compose/)

Те позвоняет запускать несколько контейнеров (docker file) в одном.

### Запуск 

Перед запуском почистить папку с Kafka_data если запускаешь с новой конфигкрацией.

`docker-compose up`

### Задача:
1) Поднять кластер кафки
   - kafka
     [kafka doc](https://kafka.apache.org/quickstart)
     [image](https://hub.docker.com/r/apache/kafka)
     [docker doc](https://docs.confluent.io/platform/current/get-started/platform-quickstart.html#ce-docker-quickstart)
   - akhq для удобного просмотра топиков
     https://akhq.io/docs/configuration/docker.html
2) Поднять стек ELK

    [Yandex.Wiki.ELK](https://wiki.yandex.ru/homepage/work/technologies/elk/)
4) Поднять прометеус для визуализации метрик





