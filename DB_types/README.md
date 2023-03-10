# Домашнее задание к занятию "`Базы данных, их типы`" - `Пахомов Владимир`


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

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему?

1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков. СУБД должна гарантировать целостность и чёткую структуру данных.
Ответ:
СУБД это распространенный вариант  хранения/управления информации в БД, используемой для финансовых отчетов, производственной и логистической информации, данных о персоонале. Реляционная модель это подход к управлению данными с испрользованием структуры и языка SQL, все данные представлены в виде таблиц, столбцов и строк с уникальным ключем, идентифицырующем каждую строку. Это позволяет создать четкую структуру данных, гарантирует целостность данных. На рынке присутсвует большое количество Реляционных систем, например таких как : PostgresSQL, MySQL, Oracle, Microsoft SQL server.

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? СУБД должны быть гибкими и быстрыми.
Ответ:
Лендинг - это всегда одностраничный сайт содержащий конкретную информацию (рекламу, маркетенговое предложение) призывающий к кокому либо одному действию. CRM - это БД основанная на клиентах, дает бизнесу поимание поведения клиента, помогая бизнесу принимать стратегии и тактики. Можно представить в виде хранилища коллекции таблиц содержащих информацию о клиете, продажах. продуктах и т.д. ПО CRM 
использует архитектуру реляционной БД. Соответвствено для таких БД подойдут СУБД, такие как : PostgresSQL, MySQL	 

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

Тут я бы приминил Документо-ориентированную СУБД, каждый документ это ключ -значение, позволяет хранить данные списки, словари , в особенности JSON, таких например как : MongoDB, Amazon DocumentBD
Либо  Столбцовую БД, в отличие от реляционной БД, столбцовая БД хранит данные по столбцам, т.е. один столбец - эта отдельная таблица, читывание происходит из стобца, что дает большую скорость работы. позволяет просто и быстро рестуктурировать таблицы с данными, легко работает с большим обьемом данных, дает хорошее сжатие данных, за счет чего позволяет экономить место на диске. Популярные Столбцовые СУБД : Vertica, ClickHouse, GogleBQ, Apachi Druid. 

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.
 
 
 Я применил бы Графовую СУБД, тк легче проектируется, управляется и модифицыруется. поиск сложных связей происходить с большей эффективностью, чем в реляционной СУБД,поскольку все связи прямые, легко воспринимаеся визуально. 
 
 Для формирования маршрутов доставки можно пробовать приминить СУПространственнымиБД - приминяются при создании ГИС решений, например PostgresSQL имеет дополнительный модуль в котрый возможно загружать карты и геоданные. 
 

### Задание 2

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.

Ответ:
1. ввод телефона 
2. формирование запроса
3. проверка наличия/отсутвия данных
4. формирование отведа
5. подтверждение действия
6. поступление денег на счет (запись измененных данных)


### Задание 3

3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL.
 Ответ:
1. четкое логическое требование к данным
2. универсальный язык запросов
3. надежная обработка транзакций
4. целостность данных
5. долговечность
6. 

### Задание 4

Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу выделено 1000 машин.

На основе какого критерия будете выбирать тип СУБД и какая модель распределённых вычислений здесь справится лучше всего и почему?

Ответ:
 Параллельные СУБД по критериям : горизонтальное распределение реляционныых таблиц и разделяемое выполнение SQL-запросов. Горизонтальное распределение состоит в том, что бы распределить строки реляционной таблицы по узлам кластера, чтобы их обрабатывать параллельно. в большинстве таких СУБД поддерживаются разные стратегии разделения, например: хеш-разделение, разделение по диапазонам значений ключа. цыклическое разделениею важное преимущество ПСУБД в том, что система автоматически упраляет различными альтернативными стратегиями разделения таблиц. такие СУБД как : Teradata, Netezza, Aster, Vertica
 Альтернативой ПСУБД выстапают системы MapReduce (MR)- модель распределенных вычислений, используемая для паралельных вычислений над очень большим количеством данных, например известная система Hadoop, главным ее достоинством является простота, программа состоит всего из двух функций Map и Reduce праграмируемых пользователем для обработки пар элементов данных ключ/значение.
Выбор между ПСУБД и MR больше падает на MR:
- простота настройки
- возможность сложной аналитики
- обработка полуструктурированных данных
- доступность программ (бесплатные)
- при записи больших данных устанавливаются контрольные точки, что повышает отказоустойчивость.
- позволяет адаптироваться к перекосам рабочей нагрузки	 

 

