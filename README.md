# Домашнее задание к занятию 12.3 "Реляционные базы данных: SQL. Часть 1" - Кувайсков Дмитрий

**Домашнее задание выполните в Google Docs или в md-файле в вашем репозитории GitHub.** 

Для оформления вашего решения в GitHub можете воспользоваться [шаблоном](https://github.com/netology-code/sys-pattern-homework).

Название файла Google Docs должно содержать номер лекции и фамилию студента. Пример названия: "12.2 Работа с данными (DDL/DML) - Александр Александров"

Перед тем как выслать ссылку убедитесь, что ее содержимое не является приватным (открыто на просмотр всем, у кого есть ссылка). Если необходимо прикрепить дополнительные ссылки, просто добавьте их в свой Google Docs.

Любые вопросы по решению задач задавайте в чате учебной группы.

Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1.

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a”, и не содержат пробелов.

![alt text](https://github.com/Fameq/12.3-hw/blob/master/img/task1.png)

```sql
SELECT (district)
FROM address
WHERE district  LIKE 'K%' and district LIKE '%a' and district NOT LIKE '% %'; 
```

### Задание 2.

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года **включительно**, 
и стоимость которых превышает 10.00.

![alt text](https://github.com/Fameq/12.3-hw/blob/master/img/task2.png)

```sql
SELECT *
FROM payment  
WHERE DATE_FORMAT(payment_date, '%Y-%c-%e')  BETWEEN '2005-6-15' AND '2005-6-18' AND amount > 10;
```

### Задание 3.

Получите последние 5 аренд фильмов.

![alt text](https://github.com/Fameq/12.3-hw/blob/master/img/task3.png)

```sql
SELECT *
FROM rental 
ORDER BY (rental_date) DESC
LIMIT 5 ;
```

### Задание 4.

Одним запросом получите активных покупателей, имена которых Kelly или Willie. 

Сформируйте вывод в результат таким образом:
- все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
- замените буквы 'll' в именах на 'pp'

![alt text](https://github.com/Fameq/12.3-hw/blob/master/img/task4.png)

```sql
SELECT 
	CONCAT_WS (' ', first_name, last_name),
	CONCAT_WS (' ', LOWER(first_name), LOWER(last_name)),
	CONCAT_WS (' ', LOWER(REPLACE(first_name, 'LL', 'PP')), LOWER(last_name)) 
FROM customer
WHERE first_name LIKE 'Willie' OR first_name LIKE 'Kelly' ;
```
 
## Дополнительные задания (со звездочкой*)
Эти задания дополнительные (не обязательные к выполнению) и никак не повлияют на получение вами зачета по этому домашнему заданию. Вы можете их выполнить, если хотите глубже и/или шире разобраться в материале.

### Задание 5*.

Выведите Email каждого покупателя, разделив значение Email на 2 отдельных колонки: в первой колонке должно быть значение, указанное до @, во второй значение, указанное после @.

### Задание 6.*

Доработайте запрос из предыдущего задания, скорректируйте значения в новых колонках: первая буква должна быть заглавной, остальные строчными.

