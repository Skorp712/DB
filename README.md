Задание 1. СУБД
Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для каждой предметной области.
Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему?

1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков. СУБД должна гарантировать целостность и чёткую структуру данных.

ОТВЕТ:
Реляционная СУБД обеспечит целостность и структурированность данных, также позволит формировать отчеты на основе собранных данных.

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы?

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? СУБД должны быть гибкими и быстрыми.

ОТВЕТ:
В обоих случаях Реляционная СУБД.

1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

ОТВЕТ:
СУБД типа ключ-значение. По запрошенному ключу можно получить необходимую информацию.

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это реализовать?

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.

ОТВЕТ:
Графовые СУБД - предназначены для работы с графами, их узлами, свойствами, и отношениями между узлами.

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД логистов?

1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

Приведите ответ в свободной форме.
________________________________________
Задание 2. Транзакции
2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.

ОТВЕТ:
1.	Открытие транзакции. Открытие соединения с БД Банка;
2.	Обращение к счету в банке и проверка наличия необходимых к переводу средств;
3.	Блокировка для списания со счета в банке необходимой суммы;
4.	Открытие соединения с БД Оператора сотовой связи;
5.	Зачисление на лицевой счет суммы, равной списанной суммы со счета в банке;
6.	Коммит изменений. Закрытие транзакции.

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?

ОТВЕТ:
Те же самые действия. Автоплатеж активирует выполнение транзакции в определенное время без участия пользователя.
Приведите ответ в свободной форме.
________________________________________
Задание 3. SQL vs NoSQL
3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL.

ОТВЕТ:
1.	В SQL-БД  данные в таблицах структурированы по строгим правилам и могут быть связаны с помощью внешних ключей поэтому, они подходят для хранения структурированных данных;

2.	В SQL используется транзакционная модель, которая позволяет сохранять целостность данных и обеспечивать ACID (Atomicity, Consistency, Isolation, Durability) свойства для отказоустойчивости и надёжности базы данных. Также SQL-базы данных могут использовать процессы резервного копирования и восстановления для обеспечения сохранности данных и минимизации потерь в случае сбоя.

3.	SQL-базы данных могут использовать процессы резервного копирования и восстановления для обеспечения сохранности данных и минимизации потерь в случае сбоя.

4.	SQL имеет язык запросов, который позволяет обрабатывать сложные запросы;

5.	Кэширование в SQL-базах данных позволяет улучшить производительность и более точно отслеживать изменения, что может помочь в оптимизации обработки запросов.

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.
Приведите ответ в свободной форме.

Задание 4. Кластеры

Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу выделено 1000 машин.
На основе какого критерия будете выбирать тип СУБД и какая модель распределённых вычислений здесь справится лучше всего и почему?
Приведите ответ в свободной форме.

ОТВЕТ:
Скорость обмена данными, надежность, высокая производительность.

Shardman — это распределенная СУБД, состоящая из отдельных серверов (шардов), каждый из которых содержит только часть данных, при этом обеспечивается отказоустойчивость каждого шарда с помощью репликации на резервные серверы.
Шарды связаны между собой через специальный транспорт — интерконнект — для быстрого обмена данными при выполнении распределенных запросов. Подключение к Shardman и выполнение всех видов запросов возможно через любой шард.
В Shardman существует несколько видов таблиц:
распределенные таблицы — таблицы которые разбиты на секции, секции таких таблиц размещены на разных шардах, часть секций таблицы хранится локально, часть ссылается на другие шарды через fdw, на каждом шарде можно обратиться к любым данным таблицы;
соразмещенные таблицы — вид распределенной таблицы, у которой размещение секций зависит от родительской таблицы, т.е. на том же шарде, где расположена соответствующая родительская секция, это позволяет увеличить производительность, т.к. объединения связанных данных производится локально на одном шарде ;
глобальные таблицы – таблицы, у которых данные идентичны на всех шардах и обновление данных происходит одновременно на всех шардах, рекомендуется использовать для таблиц с редко меняющимися данными.
В Shardman последовательности и роли также являются глобальными объектами.
