---
layout: default
backyard: true
short-title: Campaigns Backyard API
---
# Campaigns Backyard API

Для отправки запрос используется [Backyard API]({{site.baseurl}}/apis/backyard.html) с целью __<u>campaigns</u>__.

***
## Список кампаний

```
list
```

Запрос позволяет получить перечень кампаний

Запрос: `json`
```js
{
  namespace:string // группа кампаний
}
```

> Ответ: `json`
```js
[{
  id:number, // идентфиикатор документа
  doc:{
    info:{
      title:string, // название кампании
      durationSec:number, // длительность кампании в секундах
      hourRate:number, // частота показов в час
      begin:{ // начало действия кампании
        year:number, 
        month:number,
        day:number
      },
      end:{ // конец действия кампании
        year:number, 
        month:number,
        day:number
      }
    }
  },
  lastModified:string, // время последнего изменения, ISO8601
  version:number, // версия документа
}]
```

***
# Информация о кампании

```
info
```

Запрос позволяет получить общую информацию о кампании

Запрос: `json`
```js
{
  document:number // идентифактор кампании
}
```

> Ответ: `json`
```js
[{
  id:number, // идентфиикатор документа
  doc:{
    info:{
      title:string, // название кампании
      durationSec:number, // длительность кампании в секундах
      hourRate:number, // частота показов в час
      begin:{ // начало действия кампании
        year:number, 
        month:number,
        day:number
      },
      end:{ // конец действия кампании
        year:number, 
        month:number,
        day:number
      }
    }
  },
  lastModified:string, // время последнего изменения, ISO8601
  version:number, // версия документа
}]
```

***
# Структура кампании

```
content
```

Запрос позволяет получить информацию о структуре кампании

Запрос: `json`
```js
{
  document:number // идентифактор кампании
}
```

> Ответ: `json`
```js
[{
  id:number, // идентфиикатор документа
  doc:{
    content:{
      resources:[{
        weight: number, // вес медиа ресурса,
        resourceId:string // идентифкатор ресурас в Media Storage
      }]
    }
  },
  lastModified:string, // время последнего изменения, ISO8601
  version:number, // версия документа
}]
```

***
# Цели кампании

```
target
```

Запрос позволяет получить информацию о целях кампании

Запрос: `json`
```js
{
  document:number // идентифактор кампании
}
```

> Ответ: `json`
```js
[{
  id:number, // идентфиикатор документа
  doc:{
    target:{
      endpoints:[{
        device: number, // идентифкатор устройства,
        area:string // идентифкатор области на устройстве
      }]
    }
  },
  lastModified:string, // время последнего изменения, ISO8601
  version:number, // версия документа
}]
```

***
# Изменение информации о кампании

```
set-info
```

Запрос позволяет изменить общую информацию о кампании

Запрос: `json`
```js
{
  document:number, // идентфиикатор документа
  version:number?, // версия документа, для валидации изменений
  info:{
    title:string?, // новое название кампании
    durationSec:number?, // новая длительность кампании в секундах
    hourRate:number?, // новая частота показов в час
    begin:{ // новое начало действия кампании
      year:number, 
      month:number,
      day:number
    }?,
    end:{ // новый конец действия кампании
      year:number, 
      month:number,
      day:number
    }?
  }
}
```

> Ответ: `OK 200`

***
# Изменение структуры кампании

```
set-content
```

Запрос позволяет изменить информацию о структуре кампании

Запрос: `json`
```js
{
  document:number, // идентфиикатор документа
  version:number?, // версия документа, для валидации изменений
  content:{ // новая структура камрании
    resources:[{
      weight: number, // вес медиа ресурса,
      resourceId:string // идентифкатор ресурас в Media Storage
    }]
  }
}
```

> Ответ: `OK 200`


***
# Изменение целей кампании

```
set-target
```

Запрос позволяет изменить информацию о целях кампании

Запрос: `json`
```js
{
  document:number, // идентфиикатор документа
  version:number?, // версия документа, для валидации изменений
  target:{
    endpoints:[{
      device: number, // идентифкатор устройства,
      area:string // идентифкатор области на устройстве
    }]
  }
}
```

> Ответ: `OK 200`