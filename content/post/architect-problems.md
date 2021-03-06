---
title: "Рассказать я и сам могу, а вот сделать как?"
date: 2019-11-08T14:48:32+02:00
lastmod: 2019-11-08T14:48:32+02:00
tags: ["work"]
---

На всех проектах, в которых я участвую, или которые я делаю сам, я всегда вижу кучу проблем. Более того, я даже знаю как их все можно исправить! Вот один пример:

Один из проектов, который живет в активном продакшене уже более двух лет, в основе своей имеет некое API, которое принимает на вход данные от партнёров. Дальше мы эти данные вращаем и асинхронно отдаем результат. И вот, есть проблема, что иногда сервера могут быть недоступными. Два раза падала сеть у хостера, еще пару раз заказчик забывал проплатить хостинг, примерно раз в пару недель база подвисает от корявых запросов и получаем маленький даунтайм.

Я знаю как исправить все эти проблемы. Вместо прямого обращения к API можно сделать прокси на API Gateway + Lambda и пускать сообщения на бекенед через очередь. AWS падает, но гораздо реже местечковых провайдеров. База тупит потому что идут фулл-сканы на генерации репортов, или индексы с высоким cardinality используются не там, где положено. Надо всего лишь перевести поиск на ElasticSearch, настроить архивацию старых данных (а их там за два года накопилось прилично), а для отчетов сделать отдельное хранилище, в которое будут писаться денормализованные записи, по которым будут ходить ETL. Сами ETL надо писать не в коде запросами на хибере, а дать в руки заказчику BI тулзу (он достаточно грамотен чтобы смочь в SQL), которую натравить на базу данных куда будет складываться все что надо. Заодно избавиться вообще от задач "а добавьте пожалуйста колонку в отчёт" которые требуют правки кода. Избавиться от всех N+1 и повторных запросов. Перелопатить схему базы, убрать дублирующиеся данные, оптимизировать индексы и колонки. Логика приложения включает в себя довольно сложный пайплайн по которому проходят все сущности, сейчас это все складируется в логи, а надо сделать мониторинг для пользователей, чтобы они сами видели что происходит и не ходили ко мне на каждый чих за объяснениями почему это или то запроцессилось не так, как они ожидали.

Обновиться на 13ую JDK в конце-концов. И ещё овер 9000 других вещей.

Короче я все знаю как сделать и даже могу подробно объяснить, какие инструменты брать и как зачем и почему решать задачу (и даже какие есть альтернативы).

Все знаю. Но ничего не делаю. Потому что влом. Или потому что не продам. Или потому что не заплатят столько сколько хочу. Или потому что работа нудная. Или потому что есть более срочные и приоритетные задачи. И так тянется время, сервис ловит даунтайм, я думаю "пора фиксить", потом все возвращается назад и ничего уже не фиксится. Через месяц ситуация повторяется, круг замкнулся. Выхода не вижу.
