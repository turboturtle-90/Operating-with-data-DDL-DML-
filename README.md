# Домашнее задание к занятию «Работа с данными (DDL/DML)» - `Смирнов Максим`

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

`mysql is up and running`
![1-mysql-status.jpg](https://github.com/turboturtle-90/Operating-with-data-DDL-DML-/blob/ed75bdae6685fe179df4a27b57b5fa5bad726301/1-mysql-status.jpg)

1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

`Пользователи баз`

![1-user-list.jpg](https://github.com/turboturtle-90/Operating-with-data-DDL-DML-/blob/ed75bdae6685fe179df4a27b57b5fa5bad726301/1-user-list.jpg)


1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

`Права sys_temp`
![1-sys_temp-rights.jpg](https://github.com/turboturtle-90/Operating-with-data-DDL-DML-/blob/ed75bdae6685fe179df4a27b57b5fa5bad726301/1-sys_temp-rights.jpg)

1.6. Переподключитесь к базе данных от имени sys_temp.

1.7. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.8. Восстановите дамп в базу данных.

1.9. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

`Таблицы в базе sakila`
![1-damp-imported.jpg](https://github.com/turboturtle-90/Operating-with-data-DDL-DML-/blob/ed75bdae6685fe179df4a27b57b5fa5bad726301/1-damp-imported.jpg)


`Команды чтобы установить, запустить и зайти в mysql:`

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

Проверка назначенных прав пользователя sys_temp:

```
SHOW GRANTS FOR 'sys_temp'@'localhost';

```
Выход из под root и заход как пользователь sys_temp:

```
exit
mysql -u sys_temp -p
ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

Подгружаем damp. Выходим из sql и пишем в командной строке команды чтобы зачитать sql файлы

```
exit;
mysql -u sys_temp -p < ~/mysql/sakila-db/sakila-schema.sql
mysql -u sys_temp -p < ~/mysql/sakila-db/sakila-data.sql
```

Далее для проверки 
```
SHOW DATABASES;
USE sakila;
SHOW TABLES;
```
---


### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)

`Перечень таблиц и их первичных ключей`
![2-prim-keys.jpg](https://github.com/turboturtle-90/Operating-with-data-DDL-DML-/blob/ed75bdae6685fe179df4a27b57b5fa5bad726301/2-prim-keys.jpg)


---
