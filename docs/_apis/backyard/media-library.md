---
layout: default
backyard: true
short-title: Media library Backyard API
---
# Media-Library Backyard API

Для отправки запрос используется [Backyard API]({{site.baseurl}}/apis/backyard.html) с целью __<u>customers</u>__.

***
## Список группы папок
```
list-buckets
```
Запрос позволяет получить список папок

Тело запроса `json`:
```js
{
  namespace?:string // группа папок
}
```

Если группа папок не задана, но по умолчанию она считается как "`.`".


> Ответ: `json`
```js
[{
  docId:number, // номер документа описания
  doc:{
    info:{
      title:string // пользовательское название папки     
    }  
  },
  lastModified:string, // Время последней модификации документа, ISO8601
  version:number // Версия документа
}]
```


***
## Список всех папок
```
list-all-buckets
```
Запрос позволяет получить список всех папок во всех группах

> Ответ: `json`
```js
[{
  docId:number, // номер документа описания
  namespace:string, // группа папки
  doc:{
    info:{
      title:string // пользовательское название папки     
    }  
  },
  lastModified:string, // Время последней модификации документа, ISO8601
  version:number // Версия документа
}]
```


***
## Информация о папке

```
info-bucket
```
Запрос позволяет получить информацию о папке

Тело запроса `json`:
```js
{
  bucket:number // номер документа, описывающего папку 
}
```

> Ответ: `json`
```js
{
  docId:number, // номер документа описания
  namespace:string, // группа папки
  doc:{
    info:{
      title:string // пользовательское название папки
    },  
    history:{
      createdBy:string // пользователь, который создал папку,
      created:string // время создания папки ISO8601
    }  
  },
  lastModified:string, // Время последней модификации документа, ISO8601
  version:number // Версия документа
}
```


***
## Список файлов в папке

```
list-files
```
Запрос позволяет получить список файлов в папке

Тело запроса `json`:
```js
{
  bucket:number, // номер документа, описывающего папку
  includeMedia:bool? // включать медиа данные
}
```

> Ответ: `json`
```js
{
  id:number?, // номер документа описания, может не быть
  status: 'stored' | 'pending', // статус документа
  info:{
    storageId:string, // идентифкатор хранения файла,в Media Library Storage
    author:string, // автор
    enqueued:string, // время поставновки в очередь на загрузку ISO8601
    uploaded:string, // время загрузки на Media Library Storage ISO8601
    size:number, // размер содержимого файла в байтах
    filename:string, // имя оригинального файла
    filetype:string // mime тип содержимого
  },
  media:{
      width:number?, // ширина в пикселях 
      height:number?, // высота в пикселях
      codec:string?, // кодек
      frames:number?, // количество кадров
      duration:string?, // длительность в формате HH:MM:SS.zzz
      rotation:number?, // угол поворота в градусах
      fps:{ // частота смены кадров в формате num/den
        num:number, // числитель
        den:number // знаменатель
      },
      extra : {} // дополнительные, не регламентированные данные
  }  
  lastModified:string, // Время последней модификации документа, ISO8601
  version:number // Версия документа
}
```



***
## Создать папку

```
create-bucket
```
Запрос позволяет создать папку

Тело запроса `json`:
```js
{
  namespace:string?, // группа папок, null соответствует '.' 
  bucket:string? // пользовательское название папки 
}
```

Если группа папок не задана, но по умолчанию она считается как "`.`".
> Ответ: `json`
```js
{
  docId:number // номер созданного документа
}
```


***
## Состояние очереди загрузки

```
queue-list
```
Запрос позволяет получить список файлов ожидающих загрузку

> Ответ: `json`
```js
[{
  bucket:number, // идентфикатор папки
  doc:{
    author:string, // автор
    enqueued:string, // время поставновки в очередь на загрузку ISO8601
    size:number, // размер содержимого файла в байтах
    filename:string, // имя оригинального файла
    filetype:string // mime тип содержимого
  }
}]
```

***
## Постановка файла в очередь загрузки
```
enqueue
```
Запрос позволяет поставить файл из [Stash]({{site.baseurl}}/apis/stash.html) в очередь на загрузку в Media Library Storage.

Тело запроса `json`:
```js
{
  bucket:number?, // идентифкатор папки куда заливается файл 
  stashId:string? // идентифкатор файла помещенного в Stash, Stash Stored Id
  filename:string, // имя файла 
  filetype:string // mime тип файла
}
```

> Ответ: `OK 200`
