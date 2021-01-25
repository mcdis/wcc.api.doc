---
layout: default
nav-title: Stash
title: Stash API
toplevel: true
---
# Stash API
Stash API используется для передачи данных серверу, на котором они хранятся до 24ч, с целью передать их на обработку другим участниками информационной системы. 

***
## Создание сессии загрузки
```http
POST /stash/begin?filesize:number HTTP/1.1
```

Запрос создает сессию загрузки файла.

Параметры запроса:
  - `filesize:number`: размер загружаемого файла
  
>Ответ: `json`
```js
{
  sessionId:String // идентификатор сессии
}
```

***
## Загрузка блока
```http
POST /stash/post?session:string&offset:number HTTP/1.1
```

Запрос загружает блок данных в сессию

Параметры запроса:
  - `session:string`: сессия
  - `offset:number`: смещение от начала файла

Http заголовки:
- Content-length, размер содержимогою
 
В **body** кладутся сами двоичные данные, которые будут записаны в файл со смещением **offset**.
> Ответ: `200 OK`

Пример:
```http
POST /stash/post?session=93E47134D46_329B0197&offset=1048576 HTTP/1.1
Content-Length: 1048576
<ApiHey>: <ApiKeyValue>


бинарные данный на 1048576 байт
```

***
## Завершение сессии
```http
POST /stash/end?session:string&hashAlgorithm:string?&hash:string?  HTTP/1.1
```

Запрос завершает загрузку данных
Параметры запроса:
  - `session:string`: сессия
  - `hashAlgorithm:string?`: хеш алгоритм, для валидации содержимого:
    * `sha256`
    * `sha1`
  - `hash:string?` - hex строка хеш значения  
  
>Ответ: `json`
```js
{
  storedId:string // Идентификатор сохраненных данных
}
```
Ответ: `200 OK`