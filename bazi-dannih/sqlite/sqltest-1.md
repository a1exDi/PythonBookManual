# SQLtest 1

## Монтаж

SQLite3 может быть интегрирован с Python, используя sqlite3 модуль, который был написан Герхард Харинг. Он предоставляет интерфейс SQL совместимого со спецификацией DB-API 2.0, описываемой PEP 249. Вам не нужно устанавливать этот модуль отдельно, поскольку его отправки по умолчанию вместе с Python версии 2.5.x и выше.

Чтобы использовать sqlite3 модуль, вы должны сначала создать объект подключения, который представляет базу данных, а затем при необходимости вы можете создать объект курсора, который поможет вам в выполнении всех операторов SQL.

## Python sqlite3 API, модуль

Ниже приведена важный модуль sqlite3 процедура, которые могут хватить ваше требование для работы с SQLite базой данных из вашей программы на Python. Если вы ищете более сложные приложения, то вы можете посмотреть в официальной документации Python sqlite3 модуля.

| SN | API и описание |
| :--- | :--- |
| 1 | **sqlite3.connect\(database \[,timeout ,other optional arguments\]\)**Этот API открывает соединение с базой данных файла базы данных SQLite. Вы можете использовать":memory:", чтобы открыть соединение с базой данных в базу данных , которая находится в оперативной памяти , а не на диске. Если база данных успешно открыт, он возвращает объект соединения.Когда база данных получает доступ нескольких соединений и один из процессов изменяет базу данных, то SQLite база данных заблокирована, пока эта транзакция не будет зафиксирована. Параметр времени определяет, как долго соединение должно ждать, пока блокировка не уходить до тех пор, вызывая исключение. По умолчанию для параметра тайм - аута составляет 5,0\(five seconds\).Если имя, данная база данных не существует, то этот вызов будет создать базу данных. Вы можете указать имя файла с требуемой траекторией, а если вы хотите создать базу данных где-нибудь еще, кроме текущей директории. |
| 2 | **connection.cursor\(\[cursorClass\]\)**Эта процедура создает**cursor , который будет использоваться в течение вашего программирования баз данных с Python.**Этот метод принимает один необязательный параметр cursorClass. При поставке, это должно быть пользовательским курсор класс, который расширяет sqlite3.Cursor. |
| 3 | **cursor.execute\(sql \[, optional parameters\]\)**Эта подпрограмма выполняет инструкцию SQL. SQL заявление может быть параметрироваться\(ie placeholders instead of SQL literals\). Модуль sqlite3 поддерживает два вида заполнителей: знаки вопроса и именованные заполнители\(named style\).Дляexample:cursor.execute\("insert into people values\(?, ?\)",\(who, age\)\) |
| 4 | **connection.execute\(sql \[, optional parameters\]\)**Эта процедура представляет собой ярлык вышеуказанного выполнения способа, предложенный объект курсора, и это создает промежуточный объект курсора с помощью вызова метода управления курсора, а затем вызывает метод курсора выполнить с заданными параметрами. |
| 5 | **cursor.executemany\(sql, seq\_of\_parameters\)**Эта подпрограмма выполняет команду SQL против всех последовательностей параметров или отображений, найденных в последовательности SQL. |
| 6 | **connection.executemany\(sql\[, parameters\]\)**Эта процедура представляет собой ярлык, который создает промежуточный объект курсора с помощью вызова метода управления курсором, а затем вызывает метод cursor.s executemany с заданными параметрами. |
| 7 | **cursor.executescript\(sql\_script\)**Эта подпрограмма выполняет несколько SQL заявления сразу, представленного в виде сценария. Он выдает COMMIT заявление, а затем выполняет сценарий SQL он получает в качестве параметра. Все операторы SQL должны быть разделены запятой\(;\). |
| 8 | **connection.executescript\(sql\_script\)**Эта процедура представляет собой ярлык, который создает промежуточный объект курсора с помощью вызова метода управления курсора, а затем вызывает метод executescript курсора с заданными параметрами. |
| 9 | **connection.total\_changes\(\)**Эта подпрограмма возвращает общее количество строк базы данных, которые были изменены, вставлены или удалены, так как соединение с базой данных было открыто. |
| 10 | **connection.commit\(\)**Этот метод фиксирует текущую транзакцию. Если вы don.t вызвать этот метод, все, что ты с момента последнего вызоваcommit\(\)не видно из других соединений с базой данных. |
| 11 | **connection.rollback\(\)**Этот метод выполняет откат всех изменений в базе данных с момента последнего вызоваcommit\(\). |
| 12 | **connection.close\(\)**Этот метод закрывает соединение с базой данных. Обратите внимание , что это не автоматический вызовcommit\(\). Если вы просто закрыть соединение с базой данных без вызоваcommit\(\)во- первых, ваши изменения будут утеряны! |
| 13 | **cursor.fetchone\(\)**Этот метод выбирает следующую строку из набора результатов запроса, возвращая единственную последовательность, или None, когда больше нет данных нет. |
| 14 | **cursor.fetchmany\(\[size=cursor.arraysize\]\)**Эта процедура выбирает следующий набор строк результата запроса, возвращая список. Пустой список возвращается, если нет больше строк доступны. Метод пытается извлечь столько строк, сколько указано параметром размера. |
| 15 | **cursor.fetchall\(\)**Эта процедура извлекает все\(remaining\)строки результата запроса, возвращая список. Пустой список возвращается, когда ни одна строка не доступны. |

## Подключение к базе данных

После кода Python показывает, как подключиться к существующей базе данных. Если база данных не существует, то он будет создан, и, наконец, объект базы данных будет возвращен.

```text
#!/usr/bin/python

import sqlite3

conn = 
sqlite3.connect('test.db')


print "Opened database successfully";
```

Здесь вы также можете поставить имя базы данных в качестве специального имени**:memory: создать базу данных в оперативной памяти.**Теперь, давайте работать над программой , чтобы создать нашу базу данных**test.db в текущем каталоге.**Вы можете изменить свой путь, согласно вашему требованию. Держите выше код в sqlite.py файл и выполнить его, как показано ниже. Если база данных успешно создана, то это даст следующее сообщение:

```text
$chmod +x sqlite.py
$./sqlite.py
Open database successfully
```

## Создать таблицу

После программы Python будет использоваться для создания таблицы в ранее созданной базе данных:

```text
#!/usr/bin/python

import sqlite3

conn = 
sqlite3.connect('test.db')

print "Opened database successfully";

conn.execute('''CREATE TABLE COMPANY
       (ID INT PRIMARY KEY     NOT NULL,
       NAME           TEXT    NOT NULL,
       AGE            INT     NOT NULL,
       ADDRESS        
CHAR(50)
 ,
       SALARY         REAL);''')
print "Table created successfully";


conn.close()
```

Когда выше программы выполнена, она будет создавать таблицу COMPANY в вашем**test.db и он будет отображать следующие сообщения:**

```text
Opened database successfully
Table created successfully
```

## ВСТАВИТЬ Операция

После программы Python показывает, как мы можем создавать записи в нашей компании таблице, созданной в предыдущем примере:

```text
#!/usr/bin/python

import sqlite3

conn = 
sqlite3.connect('test.db')

print "Opened database successfully";


conn.execute("INSERT INTO COMPANY 
(ID,NAME,AGE,ADDRESS,SALARY)
 \
      VALUES 
(1, 'Paul', 32, 'California', 20000.00 )
 ");


conn.execute("INSERT INTO COMPANY 
(ID,NAME,AGE,ADDRESS,SALARY)
 \
      VALUES 
(2, 'Allen', 25, 'Texas', 15000.00 )
 ");


conn.execute("INSERT INTO COMPANY 
(ID,NAME,AGE,ADDRESS,SALARY)
 \
      VALUES 
(3, 'Teddy', 23, 'Norway', 20000.00 )
 ");


conn.execute("INSERT INTO COMPANY 
(ID,NAME,AGE,ADDRESS,SALARY)
 \
      VALUES 
(4, 'Mark', 25, 'Rich-Mond ', 65000.00 )
 ");


conn.commit()

print "Records created successfully";

conn.close()
```

Когда над программой выполняется, она будет создавать данный записи в таблице COMPANY и отобразит следующие две строки:

```text
Opened database successfully
Records created successfully
```

## ВЫБРАТЬ Операция

После программы Python показывает, как мы можем получать и отображать записи из нашей компании таблицы, созданной в предыдущем примере:

```python
#!/usr/bin/python

import sqlite3

conn = sqlite3.connect('test.db')

print "Opened database successfully";

cursor = conn.execute("SELECT id, name, address, salary  from COMPANY")

for row in cursor:
   print "ID = ", row[0]
   print "NAME = ", row[1]
   print "ADDRESS = ", row[2]
   print "SALARY = ", row[3], "\n"

print "Operation done successfully";

conn.close()
```

Когда над программой выполняется, он будет производить следующий результат:

```text
Opened database successfully
ID =  1
NAME =  Paul
ADDRESS =  California
SALARY =  20000.0

ID =  2
NAME =  Allen
ADDRESS =  Texas
SALARY =  15000.0

ID =  3
NAME =  Teddy
ADDRESS =  Norway
SALARY =  20000.0

ID =  4
NAME =  Mark
ADDRESS =  Rich-Mond
SALARY =  65000.0

Operation done successfully
```

## UPDATE Операция

После кода Python показывает, как мы можем использовать UPDATE заявление, чтобы обновить любую запись, а затем получать и отображать обновленные записи из нашей таблицы COMPANY:

```text
#!/usr/bin/python

import sqlite3

conn = 
sqlite3.connect('test.db')

print "Opened database successfully";


conn.execute("UPDATE COMPANY set SALARY = 25000.00 where ID=1")

conn.commit
print 
"Total number of rows updated :"
 , conn.total_changes

cursor = 
conn.execute("SELECT id, name, address, salary  from COMPANY")

for row in cursor:
   print 
"ID = "
 , row[0]
   print 
"NAME = "
 , row[1]
   print 
"ADDRESS = "
 , row[2]
   print 
"SALARY = "
 , row[3], 
"\n"


print "Operation done successfully";

conn.close()
```

Когда над программой выполняется, он будет производить следующий результат:

```text
Opened database successfully
Total number of rows updated : 1
ID =  1
NAME =  Paul
ADDRESS =  California
SALARY =  25000.0

ID =  2
NAME =  Allen
ADDRESS =  Texas
SALARY =  15000.0

ID =  3
NAME =  Teddy
ADDRESS =  Norway
SALARY =  20000.0

ID =  4
NAME =  Mark
ADDRESS =  Rich-Mond
SALARY =  65000.0

Operation done successfully
```

## Операция удаления

После кода Python показывает, как мы можем использовать ВЕИМ удалить любую запись, а затем получать и отображать остальные записи из нашей таблицы COMPANY:

```text
#!/usr/bin/python

import sqlite3

conn = 
sqlite3.connect('test.db')

print "Opened database successfully";


conn.execute("DELETE from COMPANY where ID=2;")

conn.commit
print 
"Total number of rows deleted :"
 , conn.total_changes

cursor = 
conn.execute("SELECT id, name, address, salary  from COMPANY")

for row in cursor:
   print 
"ID = "
 , row[0]
   print 
"NAME = "
 , row[1]
   print 
"ADDRESS = "
 , row[2]
   print 
"SALARY = "
 , row[3], 
"\n"


print "Operation done successfully";

conn.close()
```

Когда над программой выполняется, он будет производить следующий результат:

```text
Opened database successfully
Total number of rows deleted : 1
ID =  1
NAME =  Paul
ADDRESS =  California
SALARY =  20000.0

ID =  3
NAME =  Teddy
ADDRESS =  Norway
SALARY =  20000.0

ID =  4
NAME =  Mark
ADDRESS =  Rich-Mond
SALARY =  65000.0

Operation done successfully
```

