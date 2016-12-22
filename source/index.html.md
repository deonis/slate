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

# clients: Маркетинг

Все методы по работе с разделом маркетинга начинаются с clients.


## clients.getGroups: Список маркетинговых групп

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.getGroups?' .
  'format=json&token=745d516e1b9320ed85b84d5bfda14148';

$groups = sendRequest($url);
```

> Пример ответа:

```json
{
  "response":[
    {
      "client_groups_id":"1",
      "client_groups_name":"Постоянный посетитель",
      "loyalty_type":"1",
      "client_groups_discount":"10",
      "birthday_bonus":"5000",
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

### GET-параметры запроса clients.getGroups

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен

### Параметры ответа clients.getGroups

Параметр | Описание
--------- | -----------
client_groups_id | id маркетинговой группы
client_groups_name | Название группы
loyalty_type | Тип группы: 1 — бонусная, 2 — скидочная
client_groups_discount | Процент группы. Если группа бонсная, то означает сколько начислять бонусов на оплаченную сумму заказа. Если группа скидочная, то сколько % скидки давать по заказу.
birthday_bonus | Количество бонусов (в копейках), начисляемых на День рождения клиентов. Используется только бонусными группами.
count_groups_clients | Количество клиентов, что находится в данной группе


## clients.getGroup: Данные маркетинговой группы

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.getGroup?' .
  'format=json&token=745d516e1b9320ed85b84d5bfda14148&group_id=1';

$group = sendRequest($url);
```

> Пример ответа:

```json
{
  "response":{
    "client_groups_id":"1",
    "client_groups_name":"Постоянный посетитель",
    "loyalty_type":"1",
    "client_groups_discount":"10",
    "birthday_bonus":"5000",
    "count_groups_clients":"125"
  }
}
```

Все клиенты в Poster группируются по маркетинговым группам. Запрос возвращает данные конкретной маркетинговой группы.

### HTTP запрос

`GET https://{account}.joinposter.com/api/clients.getGroup`

### GET-параметры запроса clients.getGroup

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен
group_id | Id группы, для которой необходимо вернуть детальные данные

### Параметры ответа clients.getGroup

Параметр | Описание
--------- | -----------
client_groups_id | id маркетинговой группы
client_groups_name | Название группы
loyalty_type | Тип группы: 1 — бонусная, 2 — скидочная
client_groups_discount | Процент группы. Если группа бонсная, то означает сколько начислять бонусов на оплаченную сумму заказа. Если группа скидочная, то сколько % скидки давать по заказу.
birthday_bonus | Количество бонусов (в копейках), начисляемых на День рождения клиентов. Используется только бонусными группами.
count_groups_clients | Количество клиентов, что находится в данной группе


## clients.createGroup: Создание маркетинговой группы

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.createGroup?' .
  'format=json&token=745d516e1b9320ed85b84d5bfda14148';

$group = [
  'client_groups_name' => 'Постоянный посетитель',
  'loyalty_type' => 1,
  'client_groups_discount' => 10,
  'birthday_bonus' => 50.00
];

$group = sendRequest($url, 'post', $group);
```

> Пример ответа:

```json
{
  "response":6
}
```

Все клиенты в Poster группируются по маркетинговым группам. Запрос создает маркетинговую группу, в которую в последствии можно поместить клиентов.

### HTTP запрос

`POST https://{account}.joinposter.com/api/clients.createGroup`

### GET-параметры запроса clients.createGroup

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен

### POST-параметры запроса clients.createGroup

Параметр | Описание
--------- | -----------
client_groups_name | Название группы
loyalty_type | Тип группы: 1 — бонусная, 2 — скидочная
client_groups_discount | Процент группы. Если группа бонсная, то означает сколько начислять бонусов на оплаченную сумму заказа. Если группа скидочная, то сколько % скидки давать по заказу.
birthday_bonus | Количество бонусов (в гривнах/рублях), начисляемых на День рождения клиентов. Используется только бонусными группами.

### Параметры ответа clients.createGroup

Параметр | Описание
--------- | -----------
response | id новосозданной маркетинговой группы


## clients.updateGroup: Изменение данных маркетинговой группы

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.updateGroup?' .
  'format=json&token=745d516e1b9320ed85b84d5bfda14148';

$group = [
  'client_groups_id' => 6,
  'client_groups_name' => 'Постоянный посетитель',
  'loyalty_type' => 1,
  'client_groups_discount' => 10,
  'birthday_bonus' => 50.00
];

$group = sendRequest($url, 'post', $group);
```

> Пример ответа:

```json
{
  "response":6
}
```

Все клиенты в Poster группируются по маркетинговым группам. Запрос позволяет изменить данные конкретной маркетинговой группы.

### HTTP запрос

`POST https://{account}.joinposter.com/api/clients.updateGroup`

### GET-параметры запроса clients.updateGroup

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен

### POST-параметры запроса clients.updateGroup

Параметр | Описание
--------- | -----------
client_groups_id | id маркетинговой группы, что будет изменена
client_groups_name | Название группы
loyalty_type | Тип группы: 1 — бонусная, 2 — скидочная
client_groups_discount | Процент группы. Если группа бонсная, то означает сколько начислять бонусов на оплаченную сумму заказа. Если группа скидочная, то сколько % скидки давать по заказу.
birthday_bonus | Количество бонусов (в гривнах/рублях), начисляемых на День рождения клиентов. Используется только бонусными группами.

### Параметры ответа clients.updateGroup

Параметр | Описание
--------- | -----------
response | id измененной маркетинговой группы


## clients.removeGroup: Удаление маркетинговой группы

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.removeGroup?' .
  'format=json&token=745d516e1b9320ed85b84d5bfda14148';

$group = [
  'group_id' => 6,
];

$result = sendRequest($url, 'post', $group);
```

> Пример ответа:

```json
{
  "response":true
}
```

Все клиенты в Poster группируются по маркетинговым группам. Запрос позволяет удалить конкретную маркетинговую группу вместе со всеми клиентами, что в ней находятся.

<aside class="warning">Удаленные данные восстановлению не подлежат!</aside>

### HTTP запрос

`POST https://{account}.joinposter.com/api/clients.removeGroup`

### GET-параметры запроса clients.removeGroup

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен

### POST-параметры запроса clients.removeGroup

Параметр | Описание
--------- | -----------
group_id | id маркетинговой группы, что будет удалена

### Параметры ответа clients.removeGroup

Параметр | Описание
--------- | -----------
response | В случае успешного удаления Poster вернет true


## clients.getClients: Список клиентов

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.getClients?' .
  'format=json&token=745d516e1b9320ed85b84d5bfda14148&num=100&offset=0';

$clients = sendRequest($url);
```

> Пример ответа:

```json
{
  "response":[
    {
      "client_id":"21",
      "firstname":"Евгений",
      "lastname":"Атаманов",
      "patronymic":"",
      "discount_per":"0",
      "bonus":"0",
      "total_payed_sum":"501226",
      "date_activale":"2015-08-09 02:07:13",
      "phone":"",
      "phone_number":"0",
      "email":"",
      "birthday":"0000-00-00",
      "card_number":"0",
      "client_sex":"1",
      "country":"",
      "city":"",
      "comment":"",
      "address":"0",
      "client_groups_id":"2",
      "client_groups_name":"Скидка Выходной",
      "client_groups_discount":"15",
      "loyalty_type":"1",
      "birthday_bonus":"0"
    },
    {
      "client_id":"125",
      "firstname":"Антон",
      "lastname":"Попов",
      "patronymic":"",
      "discount_per":"0",
      "bonus":"0",
      "total_payed_sum":"0",
      "date_activale":"2016-10-03 17:37:56",
      "phone":"+380 50 111-22-33",
      "phone_number":"380501112233",
      "email":"contact@joinposter.com",
      "birthday":"0000-00-00",
      "card_number":"0",
      "client_sex":"0",
      "country":"0",
      "city":"0",
      "comment":"0",
      "address":"0",
      "client_groups_id":"1",
      "client_groups_name":"Постоянный посетитель",
      "client_groups_discount":"0",
      "loyalty_type":"1",
      "birthday_bonus":"0"
    },
    {
      "client_id":"318",
      "firstname":"Игорь",
      "lastname":"Кучма",
      "patronymic":"",
      "discount_per":"0",
      "bonus":"0",
      "total_payed_sum":"0",
      "date_activale":"2016-12-03 16:33:20",
      "phone":"+380 95 111 2222",
      "phone_number":"380951112222",
      "email":"",
      "birthday":"0000-00-00",
      "card_number":"",
      "client_sex":"1",
      "country":"Ukraine",
      "city":"",
      "comment":"",
      "address":"",
      "client_groups_id":"4",
      "client_groups_name":"Скидочная система 10%",
      "client_groups_discount":"10",
      "loyalty_type":"2",
      "birthday_bonus":"0"
    }
  ]
}
```

Запрос на получение списка клентов поддерживает «постраничную» выборку данных.

### HTTP запрос

`GET https://{account}.joinposter.com/api/clients.getClients`

### GET-параметры запроса clients.getClients

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен
num | Количество клиентов, которое необходимо получить
offset | Сколько записей необходимо пропустить от начала списка
group_id | Опциональный параметр, позволяет отобрать клиентов только указанной группы. В качестве значения необходимо указать client_groups_id группы.
client_id_only | Опциональный параметр, позволяет возвращать только client_id клиентов. В качестве значения необходимо указать true.
1c | Опциональный параметр, позволяет возвращать id_1c привязанный к клиенту. В качестве значения необходимо указать true.

<aside class="info">Если num и offset не указывать, то будут возвращены все клиенты без постраничной разбивки</aside>

### Параметры ответа clients.getClients

Параметр | Описание
--------- | -----------
client_id | id клиента
firstname | Имя клиента
lastname | Фамилия
patronymic | Отчество
discount_per | Персональный % скидки или бонсов. Будет использоваться если будет больше чем процент группы.
bonus | Текущий размер накопленных бонусов клиента (в копейках)
total_payed_sum | Общая сумма покупок (в копейках)
date_activale | Дата создания клиента
phone | Телефон
phone_number | Телефон в виде одних только чисел
email | Адрес электронной почты
birthday | Дата рождения
card_number | Номер карты
client_sex | Пол: 0 — не указан, 1 — мужской, 2 — женский
country | Страна клиента
city | Город
address | Адрес
comment | Комментарий к учетной записи клиента
id_1c | Код данного клиента в системе 1С. Этот параметр можно установить с помощью компанды clients.set1cClientId
client_groups_id | id маркетинговой группы
client_groups_name | Название группы
loyalty_type | Тип группы: 1 — бонусная, 2 — скидочная
client_groups_discount | Процент группы. Если группа бонсная, то означает сколько начислять бонусов на оплаченную сумму заказа. Если группа скидочная, то сколько % скидки давать по заказу.
birthday_bonus | Количество бонусов (в копейках), начисляемых на День рождения клиентов. Используется только бонусными группами.


## clients.getClient: Данные клиента

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.getClient?' .
  'format=json&token=745d516e1b9320ed85b84d5bfda14148&client_id=1';

$client = sendRequest($url);
```

> Пример ответа:

```json
{
  "response":[
    {
      "client_id":"38",
      "firstname":"Попова",
      "lastname":"000022",
      "patronymic":"Елена",
      "discount_per":"0",
      "bonus":"0",
      "total_payed_sum":"417000",
      "date_activale":"2016-04-23 05:14:26",
      "phone":"+380 50 11-11-111",
      "phone_number":"380501111111",
      "email":"contact@joinposter.com",
      "birthday":"1986-11-23",
      "card_number":"0000000000222",
      "client_sex":"0",
      "country":"",
      "city":"",
      "comment":"",
      "address":"",
      "client_groups_id":"7",
      "client_groups_name":"Постоянный клиент",
      "client_groups_discount":"0",
      "loyalty_type":"2",
      "birthday_bonus":"0",
      "accumulation_products":{
        "4":{
          "promotion_id":"4",
          "products":[
            {
              "count":"3",
              "sum":540,
              "product_id":"24",
              "modification_id":"0"
            }
          ]
        }
      },
      "prize_products":[
        {
          "prize_product_id":"301",
          "promotion_id":"4",
          "conditions":{
            "bonus_products":[
              {
                "type":"1",
                "id":"1"
              }
            ],
            "bonus_products_pcs":1,
            "bonus_products_g":0,
            "bonus_products_condition_type":"1",
            "bonus_products_condition_value":"100"
          },
          "date_accrual":"2016-05-11 11:40:10"
        }
      ]
    }
  ]
}
```

Запрос возвращает данные конкретного клиента, включая его накопления по акциям с накоплениями, а также отложенные бонусные товары по бонусным акциям.

### HTTP запрос

`GET https://{account}.joinposter.com/api/clients.getClient`

### GET-параметры запроса clients.getClient

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен
client_id | Id клиента, для которого необходимо вернуть детальные данные
1c | Опциональный параметр, позволяет возвращать id_1c привязанный к клиенту. В качестве значения необходимо указать true.

### Параметры ответа clients.getClient

Параметр | Описание
--------- | -----------
client_id | id клиента
firstname | Имя клиента
lastname | Фамилия
patronymic | Отчество
discount_per | Персональный % скидки или бонсов. Будет использоваться если будет больше чем процент группы.
bonus | Текущий размер накопленных бонусов клиента (в копейках)
total_payed_sum | Общая сумма покупок (в копейках)
date_activale | Дата создания клиента
phone | Телефон
phone_number | Телефон в виде одних только чисел
email | Адрес электронной почты
birthday | Дата рождения
card_number | Номер карты
client_sex | Пол: 0 — не указан, 1 — мужской, 2 — женский
country | Страна клиента
city | Город
address | Адрес
comment | Комментарий к учетной записи клиента
id_1c | Код данного клиента в системе 1С. Этот параметр можно установить с помощью компанды clients.set1cClientId
client_groups_id | id маркетинговой группы
client_groups_name | Название группы
loyalty_type | Тип группы: 1 — бонусная, 2 — скидочная
client_groups_discount | Процент группы. Если группа бонсная, то означает сколько начислять бонусов на оплаченную сумму заказа. Если группа скидочная, то сколько % скидки давать по заказу.
birthday_bonus | Количество бонусов (в копейках), начисляемых на День рождения клиентов. Используется только бонусными группами.
accumulation_products | Список продаж, что относятся к акциям с накоплением. Например, акция «5+1», где учитываются покупки в разных чеках.
prize_products | Список отложенных бонусов, что относятся к призовым акциям. Например, акция «Купи пиццу и получи завтра еще одну на 10% дешевле», то есть призы, которые выдаются не сразу, а откладываются на следующую покупку.

### Содержимое параметра accumulation_products

Параметр | Описание
--------- | -----------
promotion_id | id акции с накоплением, за которой закрепили данную продажу
products | Список товаров осуществленной продажи, что относится к акции с накоплением. Ниже описано содержимое данного массива товаров.
product_id | id товара
modification_id | id модификации, если товар с модификациями
count | Количество товара
sum | Стоимость товара (в гривнах/рублях)

### Содержимое параметра prize_products

Параметр | Описание
--------- | -----------
prize_product_id | Уникальный id отложенного приза
promotion_id | id призовой акции
conditions | Список условий, по которым определяется какой именно приз надо выдать. type обозначет: 0 — из всех товаров, 1 — из категории, что указана в id, 2 — конкретный товар с указанным id, 3 — модификация товара с указанным id (для удобства еще будет передан product_id товара, к которому относится модификация)
bonus_products_pcs | Сколь штук бонусного товара выдавать, если он штучный
bonus_products_g | Сколь грамм бонусного товара выдавать, если он весовой
bonus_products_condition_type | На каких условиях выдавать бонус: 1 — процент скидки (например, с 50 или 100% скидкой), 2 — фиксированная сумма скидки (например, дать 5 гривен/рублей скидки на товар), 3 — фиксированная стоимость товара (например, продавать по 1 гривне/рублю)
bonus_products_condition_value | Количество для параметра bonus_products_condition_type. Если денежное значение, то возвращается в гривнах/рублях.


## clients.createClient: Создание клиента

>  Пример запроса:

```php
$url = 'https://demo.joinposter.com/api/clients.createClient?' .
  'format=json&token=745d516e1b9320ed85b84d5bfda14148';

$client = [
  'client_name' => 'Попова Елена Андреевна',
  'client_sex' => 2,
  'client_groups_id_client' => 7,
  'card_number' => '0000000000222',
  'discount_per' => 0,
  'phone' => '+380 50 11-11-111',
  'email' => 'contact@joinposter.com',
  'birthday' => '1986-11-23',
  'city' => '',
  'country' => '',
  'address' => '',
  'comment' => '',
  'bonus' => 10,
  'total_payed_sum' => 417000,
];

$client = sendRequest($url, 'post', $client);
```

> Пример ответа:

```json
{
  "response":4082
}
```

Запрос создает клиента.

### HTTP запрос

`POST https://{account}.joinposter.com/api/clients.createClient`

### GET-параметры запроса clients.createClient

Параметр | Описание
--------- | -----------
format | Указываем формат выдачи ответа. Может быть xml или json. По умолчанию json.
token | Авторизационный токен

### POST-параметры запроса clients.createClient

Параметр | Описание
--------- | -----------
client_name | ФИО клиента
client_sex | Пол: 0 — не указан, 1 — мужской, 2 — женский
client_groups_id_client | id маркетинговой группы, к которой будет относиться клиент
card_number | Номер карты
discount_per | Персональный % скидки или бонсов. Будет использоваться если будет больше чем процент группы.
phone | Телефон
email | Адрес электронной почты
birthday | Дата рождения
city | Город
country | Страна клиента
address | Адрес
comment | Комментарий к учетной записи клиента
bonus | Текущий размер накопленных бонусов клиента (в гривнах/рублях)
total_payed_sum | Общая сумма покупок (в копейках)

### Параметры ответа clients.createClient

Параметр | Описание
--------- | -----------
response | id новосозданного клиента