c# Панченко_VK

#### SQL
Есть 2 таблицы p1 и p2 с индексом по id, при этом name есть только в таблице p2, а status только в таблице p1.
Нужно получить id c name содержащий X и status равный active.
------------------------

#### Решение
```
SELECT p1.id
FROM p1
INNER JOIN p2 ON p1.id = p2.id
WHERE p2.name LIKE '%X%'
AND p1.status = 'active';
```
-----------------------

#### HTML
Есть форма, в которой пользователь заполняет данные say и to, правильно ли написан код и что произойдет?
```
<form action="http://foo.com" method="post">
  <div>
    <label for="say">What you say?</label>
    <input name="say" id="say" value="Hi">
  </div>
  <div>
    <label for="to">You say it to?</label>
    <input name="to" id="to" value="Mom">
  </div>
  <div>
    <button>Send my greetings</button>
  </div>
</form>
```
---------------------------------
#### Решение

После нажатия на кнопку ```<button>``` форма отправляется на URL [http://foo.com](http://foo.com) с использованием метода POST.

В теле запроса будут:
say: Hi;
to: Mom

##### Итог: все работает корректно, форма отправит данные на [http://foo.com](http://foo.com)
---------------------------------

#### JS
В каком порядке выполняются JS
1. ```<script async src="script-1.js"></script> // Время загрузки скрипта 1.5s```
2. ```<script src="script-2.js"></script> // Время загрузки скрипта 1s```
3. ```<script defer src="script-3.js"></script> // Время загрузки скрипта 3s```
4. ```<script defer src="script-4.js"></script> // Время загрузки скрипта 1.5s```
5. ```<script src="script-5.js"></script> // Время загрузки скрипта 2s```
6. ```<script async src="script-6.js"></script> // Время загрузки скрипта 1s```
7. ```<script defer src="script-7.js"></script> // Время загрузки скрипта 0.1s```
-------------------
#### Решение

Скрипты без атрибутов выполнятся в порядке написанном в HTML:
1. ```script-2```
2. ```script-5```

Скрипты сатрибутом ```async``` могут выполнится параллельно с ```script-2``` и ```script-5```
* ```script-1.js```
* ```script-6.js```

Скрипты с атрибутом defer загружаются параллельно с загрузкой страницы, но выполнятся после полной загрузки в порядке указанном в коде:
* ```script-3.js```
* ```script-4.js```
* ```script-7.js```
