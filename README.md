﻿# Файлы проекта находятся в ветке master

# Задание 1

# Представь: тебе нужно проверить, отображается ли созданный заказ в базе данных. Для этого: выведи список логинов курьеров с количеством их заказов в статусе «В доставке» (поле inDelivery = true).

Запрос:

  SELECT c.login, 
         COUNT(o.id) AS "deliveryCount" 
  FROM "Couriers" AS c 
  LEFT JOIN "Orders" AS o ON c.id = o."courierId" 
  WHERE o."inDelivery" = true 
  GROUP BY c.login;

Скриншот результата запроса:

# Задание 2

# Ты тестируешь статусы заказов. Нужно убедиться, что в базе данных они записываются корректно. Для этого: выведи все трекеры заказов и их статусы. Статусы определяются по следующему правилу: 
Если поле finished == true, то вывести статус 2. 
Если поле canсelled == true, то вывести статус -1. 
Если поле inDelivery == true, то вывести статус 1. 
Для остальных случаев вывести 0.

Запрос:

   SELECT track, 
        CASE 
            WHEN finished = true THEN 2 
            WHEN cancelled = true THEN -1 
            WHEN "inDelivery" = true THEN 1 
            ELSE 0 
        END AS status 
   FROM "Orders";

Скриншот результата запроса:

# Задание 3

# Автоматизация тестов Яндекс Самокат, которые проверяют с помощью API Яндекс Самокат, что:
- Клиент создает заказ.
- Проверяется, что по треку заказа можно получить данные о заказе. 

# Важно:
- Для запуска тестов должны быть установлены пакеты pytest и библиотека requests
- Запуск всех автотестов выполняется командой pytest

# Шаги выполнения автотеста:
- Написать POST-запрос на создание заказа.
- Сохранить номер трекера заказа.
- Написать GET-запрос на получение заказа по трекеру заказа.
- Проверить, что код ответа равен 200.
- Запустить автотест.

# Стек для выполнения задания:
- VS Code
- GitHub
- requests
- pytest

# Файлы проекта находятся в ветке master

Скриншот результата автоматизации:
