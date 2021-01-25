---
layout: default
backyard: true
short-title: Customers Backyard API
---
# Customers Backyard API

Для отправки запрос используется [Backyard API]({{site.baseurl}}/apis/backyard.html) с целью __<u>customers</u>__.

***
## Создать клиента

```
create
```

Запрос позволяет создать нового клиента.
тело запросы: `json`:
```
{
   friendlyName
}
```

> Ответ: `json`
```js
{
  documentId:number // номер документа
}
```


***
## Список клиентов
```
list
```

Запрос позволяет получить перечень клиентов

> Ответ: `json`
```js
[{
  friendlyName:string?, // Имя клиента
  description:string? // Описание
}]
```

***
## Информация о клиенте
```
get
```

Запрос `json`
Тело запроса:
```js
{
  documentId:number // Идентификатор клиента 
}
```

>Ответ `json`:
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
```
create
```
Запрос `json`
Тело запроса:
```js
{
  friendlyName:string // Имя клиента 
}
```

>Ответ `json`:
```js
{
  documentId:number? // номер документа со сведениями о клиенте
}
```

***
## Изменение сведений о клиенте

```
update
```

Запрос `json`
Тело запроса:
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

>Ответ `OK 200`