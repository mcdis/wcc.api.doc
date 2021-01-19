---
layout: default
nav-title: Backyard
title: Backyard
toplevel: true
---
# Backyard API

Backyard API обеспечиват выполнение запросов к внутренней информационной структуре, как к единому целому.


## Основные подсистемы
{% for item in site.apis %}{% if item.backyard %}- [{{item.short-title}}]({{site.baseurl}}{{item.url}}){% endif %}
{% endfor %}

***
## Запрос на информационную площадку
> **POST** `backyard/{:target}/{:request}?timeout:number?`

Запрос позволяет послать запрос к внутренней инфрмационной системе.

Параметры запроса:
 - `target:string` - цель запроса
 - `request:string` - операция запроса
 - `number?:number` - таймаут ожидания ответа от подсистемы, опционален
 
Тело запроса: `Blob` 

>> Ответ зависит от запроса