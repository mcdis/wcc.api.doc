---
layout: default
backyard: true
short-title: Customers Backyard API
---
# Customers Backyard API

Для отправки запрос используется Backyard API с целью __<u>customers</u>__.

***
## Список клиентов
> request:`list`

Запрос позволяет получить перечень клиентов

>> Ответ: `json`
```js
[{
  friendlyName:string?, // Имя клиента
  description:string? // Описание
}]
```

***
## Информация о клиенте
> request: `get`

> Запрос `json`

> Тело запроса:
```js
{
  documentId:number // Идентификатор клиента 
}
```

>>Ответ `json`:
```js
{
  lastModified:string, // Время изменения сведений ISO8601
  version:number, // Номер версии изменений
  doc:{
    info:{
      friendlyName:string?, // имя клиента
      description:string? // описание    
    }  
  }
}
```

***
## Создание клиента
> request: `create`

> Запрос `json`

> Тело запроса:
```js
{
  friendlyName:string // Имя клиента 
}
```

>>Ответ `json`:
```js
{
  documentId:number? // номер документа со сведениями о клиенте
}
```

***
## Изменение сведений о клиенте
> request: `update`

> Запрос `json`

> Тело запроса:
```js
{
  documentId:number, // Номер документа
  version?:number, // Предущая версия документа, для контроля изменений, оптионально
  info:{
    friendlyName:string?, // имя клиента
    description:string? // описание клтента
  } 
}
```

>>Ответ `OK 200`