---
layout: default
nav-title: Info
title: Info API
toplevel: true
---
# Info API
Info API используется для получения информации о работе системы.

***
## Версия сервера
> **GET** `/info/version`

Версия ПО сервера

>> Ответ `string` 

***
## Сводка
> **GET** `/info/summary`

Получить сводку по сервисах

>> Ответ `json`
```js
{
  version: string, // версия сервера
  uptimeSeconds: number, // время наработки в сек
  platform: { 
    version: string, // версия платформы,
    bootTime: DateTimeOffset, // Впемя загрузки ISO8601,
    uptime: number, // время наработки платформы в сек
    services:[
      {
        type:string, // тип сервиса,
        instance:string, // экземпляр
        version:версия, // версия сервиса
        processIndex:number // индекс запуска
      }    
    ]
  }
}
```