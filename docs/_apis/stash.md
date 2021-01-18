---
layout: default
nav-title: Stash
title: Stash API
---
# Stash API
Stash API используется для передачи данных серверу, на котором они хранятся до 24ч, с целью передать их на обработку другим участниками информационной системы. 

***
## Создание сессии загрузки
> **POST** `/stash/begin?filesize:number`

Запрос создает сессию загрузки файла.

Параметры запроса:
  - `filesize:number`: размер загружаемого файла
  
Ответ: `json`

```js
{
  sessionId:String // идентификатор сессии
}
```

***
## Загрузка блока
> **POST** `/stash/post?session:string&offset:number`

Запрос загружает блок данных в сессию

Параметры запроса:
  - `session:string`: сессия
  - `offset:number`: смещение от начала файла
  
Ответ: `200 OK`

***
## Завершение сессии
> **POST** `/stash/end?session:string&hashAlgorithm:string?&hash:string?`

Запрос завершает загрузку данных
Параметры запроса:
  - `session:string`: сессия
  - `hashAlgorithm:string?`: хеш алгоритм, для валидации содержимого:
    * `sha256`
    * `sha1`
  - `hash:string?` - hex строка хеш значения  
  
Ответ: `json`
```js
{
  storedId:string // Идентификатор сохраненных данных
}
```

Ответ: `200 OK`