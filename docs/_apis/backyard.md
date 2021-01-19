---
layout: default
nav-title: Backyard
title: Backyard
toplevel: true
---
# Backyard API

Backyard API обеспечивает выполнение запросов к внутренней информационной структуре, как к единому целому.


## Основные подсистемы
{% for item in site.apis %}{% if item.backyard %}- [{{item.short-title}}]({{site.baseurl}}{{item.url}}){% endif %}
{% endfor %}

***
## Запрос на информационную площадку
```http
POST backyard/{:target}/{:request}?timeout:number? HTTP/1.1
```

Запрос позволяет послать запрос к внутренней информационной системе.

Параметры запроса:
 - `target:string` - цель запроса
 - `request:string` - операция запроса
 - `number?:number` - максимальное время ожидания ответа от подсистемы, опционально
 
Тело запроса: `Blob` 

> Ответ зависит от запроса