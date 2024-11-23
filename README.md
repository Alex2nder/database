# Домашнее задание к занятию "`Базы данных, их типы`" - `Чернецкий А.В.`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---
### Задание 1

1.1. Бюджетирование проектов и финансовые аналитические отчёты

Тип СУБД: Реляционная СУБД (PostgreSQL, Oracle, Microsoft SQL Server).

Необходимость гарантирования целостности данных и строгой структуры.
Для аналитики и прогнозирования рисков можно использовать возможности для OLAP-запросов, встроенные в современные реляционные СУБД.
Поддержка транзакций (ACID).

1.2. Лендинги и CRM

Тип СУБД для лендингов: Документоориентированная СУБД (MongoDB).
Гибкость структуры данных (JSON-документы) 
Быстрая обработка запросов, масштабируемость и возможность горизонтального масштабирования под высокие нагрузки.

Тип СУБД для CRM: Реляционная СУБД (PostgreSQL, MySQL).

CRM требует строгой структуры данных и высокой надежности для учета сделок, клиентов и взаимодействий.
Возможность интеграции с BI-системами для построения отчётов.
Высокая производительность для сложных аналитических запросов.

1.3. База по корпоративным нормам и обучающим материалам

Тип СУБД: Реляционная СУБД (SQLite, PostgreSQL).

Простая структура данных позволяет эффективно организовать корпоративные правила и обучающие материалы.
Реляционная модель обеспечивает удобство доступа к информации благодаря строгой иерархии и возможностям SQL-запросов.
SQLite подойдет для небольших объёмов данных и простых приложений, а PostgreSQL — для более масштабных решений.

1.4. Задачи логистики и маршрутизации

Тип СУБД: Графовая СУБД ( Neo4j).

Графовые базы данных оптимально подходят для задач, связанных с маршрутами и связями, так как данные представляются в виде узлов (объекты) и рёбер (связи между объектами).
Быстрая обработка запросов на построение маршрутов (например, кратчайший путь).
Возможность работы с динамическими связями.


### Задание 2

Шаги для успешного завершения транзакции по пополнению баланса телефона:

1. Проверка входных данных
Пользователь вводит номер телефона и сумму пополнения.
Система проверяет корректность данных:
Формат номера телефона.
Допустимую сумму (например, минимальное/максимальное ограничение).
Наличие пользователя с указанным номером в базе данных.

2. Авторизация платежа
Пользователь выбирает способ оплаты (карта, электронный кошелёк и т. д.).
Система отправляет запрос в платежный шлюз или банк для проверки:
Валидности платежных данных (номер карты, CVV, срок действия).
Наличия достаточных средств на счёте.

3. Блокировка средств
Если авторизация прошла успешно, на счёте пользователя временно блокируется указанная сумма.
Платёжный провайдер подтверждает возможность списания средств, но пока не выполняет транзакцию.

4. Запись транзакции в СУБД
В базу данных создаётся запись о транзакции с уникальным идентификатором и статусом «В обработке».
Фиксируются:
Номер телефона.
Сумма пополнения.
Дата и время.
Способ оплаты.
Статус транзакции.

5. Обновление баланса
Система инициирует обновление баланса в СУБД.
Баланс пользователя увеличивается на указанную сумму.
Статус транзакции обновляется на «Успешно».

6. Завершение транзакции
Платёжный провайдер подтверждает списание средств с платежного счёта.
Пользователь получает уведомление (SMS, email или push):
Подтверждение успешного пополнения.
Актуальный баланс счёта.
В случае сбоя на любом этапе:
Система отменяет блокировку средств.
Статус транзакции обновляется на «Ошибка», пользователь получает уведомление о проблеме.


### Задание 3

Преимущества SQL-систем по отношению к NoSQL:

1. Строгая структура данных
SQL-системы используют реляционную модель с заранее определённой схемой данных. Это обеспечивает:
Целостность данных (constraints, primary/foreign keys).
Удобство работы с данными, имеющими чёткую иерархию и связи.
Минимизацию ошибок благодаря валидации на уровне базы.

2. Поддержка транзакций (ACID-свойства)
SQL-системы обеспечивают атомарность, согласованность, изолированность и долговечность операций, что особенно важно для финансовых и критически важных систем.
Например, банковские транзакции или изменения данных гарантированно сохраняются и не нарушают целостность при сбоях.

3. Удобный язык запросов (SQL)
SQL является стандартом для работы с данными, что делает его:
Понятным и универсальным инструментом для большинства пользователей.
Подходящим для сложных аналитических запросов (включая агрегатные функции, подзапросы и джоины).
Широко поддерживаемым в BI-инструментах.

4. Богатый набор встроенных функций
SQL-системы предоставляют обширный функционал для работы с данными:
Индексы для ускорения поиска.
Механизмы репликации и восстановления данных.
Встроенные инструменты для аналитики (например, OLAP-операции).
Это делает их идеальными для обработки сложных аналитических запросов и отчётов.

5. Развитая экосистема и сообщество
SQL-системы существуют десятилетиями (PostgreSQL, MySQL, Oracle и др.), что обеспечило:
Надёжную документацию и большое количество ресурсов для обучения.
Поддержку огромного числа инструментов для интеграции, мониторинга и оптимизации.
Готовые решения для масштабирования и оптимизации производительности.

### Задание 4

Критерии выбора типа СУБД:

Объем и структура данных:
Если данные имеют строгую структуру (таблицы, связи), подойдут реляционные СУБД, поддерживающие горизонтальное масштабирование (например, Amazon Aurora, CockroachDB).
Если данные неструктурированные (логи, JSON, текстовые файлы), лучше использовать NoSQL СУБД (например, Cassandra, MongoDB).

Требования к консистентности:
Если требуется строгая консистентность, следует выбирать СУБД с поддержкой ACID.
Для задач с высокой доступностью, где допустима eventual consistency, подойдут NoSQL решения (например, DynamoDB).

Тип и сложность вычислений:
Для сложной аналитики и обработки больших объёмов данных оптимальны аналитические СУБД, такие как Snowflake, ClickHouse или Google BigQuery.
Если требуется обработка потоковых данных, следует выбирать СУБД с интеграцией с Apache Kafka или Apache Pulsar.
Масштабируемость:

Нужно учитывать способность СУБД эффективно работать на кластере из 1000 машин (распределённое хранение и вычисления).

Рекомендуемая модель распределённых вычислений Apache Spark

Почему:

Высокая производительность:
Spark использует распределённую обработку в оперативной памяти, что значительно ускоряет вычисления по сравнению с дисковой моделью Hadoop MapReduce.
Поддержка масштабируемости:

Spark масштабируется на тысячи узлов, обеспечивая обработку петабайт данных.
Гибкость:

Поддерживает различные типы данных (структурированные, полуструктурированные, неструктурированные).
Позволяет выполнять как пакетную обработку, так и потоковую (Streaming).
Интеграция с хранилищами данных:

Spark легко интегрируется с HDFS, Amazon S3, Cassandra, Hive, а также с реляционными базами данных (через JDBC).
Поддержка сложной аналитики:

Включает библиотеки для машинного обучения (MLlib), работы с графами (GraphX) и SQL-запросов (Spark SQL).