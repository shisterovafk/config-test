# Docker compose

[Yandex.Wiki.Docker Compose](https://wiki.yandex.ru/homepage/work/technologies/docker/docker-compose/)

Те позвоняет запускать несколько контейнеров (docker file) в одном.

### Запуск

`docker-compose up`
`docker-compose down -v` -удалить все за собой

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
    [ELK-blog](https://www.elastic.co/blog/getting-started-with-the-elastic-stack-and-docker-compose)
4) Поднять прометеус для визуализации метрик

### ELK
Elasticsearch (хранение и поиск данных)

Logstash (конвеер для обработки, фильтрации и нормализации логов)

Kibana (интерфейс для удобного поиска и администрирования)





