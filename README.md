# Домашнее задание к занятию "«Работа с данными (DDL/DML)» - `Смирнов Максим`

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.




1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

`Ссылка на .cfg`

https://github.com/turboturtle-90/Homework_clustering_and_load_balancing/blob/593b469a59cef8dcb0deedeb24426b0453281f6e/haproxy.cfg-assignment1 

`Балансировка на 4 уровне по roubdrobin`
![1-level4.jpg](https://github.com/turboturtle-90/Homework_clustering_and_load_balancing/blob/7705286e7aea06eb754ecf0cc6f2510aa3f7173f/1-level4.jpg)

`Команды :`

```
sudo apt update                                                        
sudo apt install mysql-server

sudo systemctl start mysql
sudo systemctl status mysql

sudo mysql
```
должно появиться `mysql>`
Далее создание пользователя с указанием с какого хоста он может подключаться и пароля

```
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'password';
```
Проверка что пользователь создан, вызов списка пользователей:
```
SELECT user, host, plugin FROM mysql.user;
```
Далее выдача прав - в данном случае всех прав:

```
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

Далее выдача прав - в данном случае всех прав:


```



### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```

---
