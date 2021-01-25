---
layout: default
index: true
---
# Blending Worlds Server Rest API
Обновлено: {{ site.time | date: '%Y.%m.%d %H:%M'}}

***
## Автоматизированные запросы
Для автоматизированных запросов, следует передавать **API Access Key** через HTTP заголовок: <u>WccApiKey</u>

Пример запроса:
```http
GET /devices/list HTTP/1.1
Host: localhost:27000
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36
Accept: application/json
Accept-Encoding: br | gzip
WccApiKey: F037FF6C11A24A58AC374B16AE8EF5A9
```

***
## Сжатие
Все запросы поддерживают ответ в сжатом виде.

Поддерживаемые алгоритмы сжатия:
 - Brotli
 - GZip

Пример запроса:
```http
GET /devices/list HTTP/1.1
Host: localhost:27000
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36
Accept: application/json
Accept-Encoding: br | gzip
WCC-API-KEY: F037FF6C11A24A58AC374B16AE8EF5A9
```