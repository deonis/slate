---
title: Poster API

language_tabs:
  - php: PHP

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Авторизация 1-0

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Маркетинг (clients)

Все методы по работе с разделом маркетинга начинаются с clients.

## Список маркетинговых групп (clients.getGroups)

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.getGroups?' . 
  'format=json&token=745d516e1b9320ed85b84d5bfda14148';

$groups = sendRequest($url);
```

> После отправки запроса, получим примерно следующий ответ:

```json
{
  "response":[
    {
      "client_groups_id":"1",
      "client_groups_name":"Постоянный посетитель",
      "loyalty_type":"1",
      "client_groups_discount":"10",
      "birthday_bonus":"50",
      "count_groups_clients":"125"
    },
    {
      "client_groups_id":"4",
      "client_groups_name":"Скидочная система 10%",
      "loyalty_type":"2",
      "client_groups_discount":"10",
      "birthday_bonus":"0",
      "count_groups_clients":"43"
    },
    {
      "client_groups_id":"5",
      "client_groups_name":"Скидочная система 20%",
      "loyalty_type":"2",
      "client_groups_discount":"20",
      "birthday_bonus":"0",
      "count_groups_clients":"42"
    }
  ]
}
```

Все клиенты в Poster группируются по маркетинговым группам. Данный запрос возвращает список маркетинговых групп.

### HTTP запрос

`GET https://{account}.joinposter.com/api/clients.getGroups`

### Параметры запроса clients.getGroups

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен

### Параметры ответа clients.getGroups

Параметр | Описание
--------- | -----------
client_groups_id | id маркетинговой группы
client_groups_name |  Название группы
loyalty_type |  Тип группы: 1 — бонусная, 2 — скидочная
client_groups_discount |  Процент группы. Если группа бонсная, то означает сколько начислять бонусов на оплаченную сумму заказа. Если группа скидочная, то сколько % скидки давать по заказу.
birthday_bonus |  Количество бонусов (в копейках), начисляемых на День Рождения клиентов. Используется только бонусными группами. 
count_groups_clients |  Количество клиентов, что находится в данной группе

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

