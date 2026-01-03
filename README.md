# Workers
Давай напишем программу, которая определит, чем заняться тому или иному человеку.
Для этого нужно:

Ввести [в цикле] с клавиатуры несколько строк (ключей).
Строки (ключи) могут быть такими: "user", "loser", "coder", "proger".
Ввод окончен, когда строка не совпадает ни с одной из выше указанных.
Для каждой введенной строки нужно:
Создать соответствующий объект [см. Person.java], например, для строки "user" нужно создать объект класса User.
Передать этот объект в метод doWork.
Написать реализацию метода doWork, который:
Вызывает метод live() у переданного объекта, если этот объект (person) имеет тип User.
Вызывает метод doNothing(), если person имеет тип Loser.
Вызывает метод writeCode(), если person имеет тип Coder.
Вызывает метод enjoy(), если person имеет тип Proger.

Псевдокод:

```
ИНТЕРФЕЙС Person
    КЛАСС User РЕАЛИЗУЕТ Person
        МЕТОД live()
            ВЫВЕСТИ "I usually just live."
    
    КЛАСС Loser РЕАЛИЗУЕТ Person
        МЕТОД doNothing()
            ВЫВЕСТИ "I usually do nothing."
    
    КЛАСС Coder РЕАЛИЗУЕТ Person
        МЕТОД writeCode()
            ВЫВЕСТИ "I usually write code."
    
    КЛАСС Proger РЕАЛИЗУЕТ Person
        МЕТОД enjoy()
            ВЫВЕСТИ "It's a wonderful life!"


ФУНКЦИЯ doWork(person)
    ЕСЛИ person ЭКЗЕМПЛЯР User
        user = (User) person
        user.live()
    ИНАЧЕ ЕСЛИ person ЭКЗЕМПЛЯР Loser
        loser = (Loser) person
        loser.doNothing()
    ИНАЧЕ ЕСЛИ person ЭКЗЕМПЛЯР Coder
        coder = (Coder) person
        coder.writeCode()
    ИНАЧЕ ЕСЛИ person ЭКЗЕМПЛЯР Proger
        proger = (Proger) person
        proger.enjoy()

ГЛАВНАЯ ПРОГРАММА
    СОЗДАТЬ reader для чтения ввода
    
    person = null
    
    БЕСКОНЕЧНЫЙ ЦИКЛ
        ПРОЧИТАТЬ key из reader
        
        ЕСЛИ key НЕ в ["user", "loser", "coder", "proger"]
            ПРЕРВАТЬ ЦИКЛ
        
        ВЫБРАТЬ key
            СЛУЧАЙ "user":
                person = НОВЫЙ User
            СЛУЧАЙ "loser":
                person = НОВЫЙ Loser
            СЛУЧАЙ "coder":
                person = НОВЫЙ Coder
            СЛУЧАЙ "proger":
                person = НОВЫЙ Proger
        
        ВЫЗВАТЬ doWork(person)
    
    ЗАКРЫТЬ reader
```

Краткое описание алгоритма:

1. Определение интерфейса и классов:
   · Создается интерфейс Person
   · Внутри определяются 4 класса-реализации, каждый со своим уникальным методом
2. Основной алгоритм:
   · Бесконечно читаем ввод пользователя
   · Проверяем, является ли ввод одним из допустимых ключей
   · Если нет - выходим из цикла
   · Если да - создаем соответствующий объект и вызываем doWork()
3. Метод doWork():
   · Определяет конкретный тип объекта
   · Приводит к нужному типу
   · Вызывает специфический метод этого типа

Логика работы:

```
пользователь вводит → создается объект → вызывается метод
"user"            → User           → live()
"loser"           → Loser          → doNothing()
"coder"           → Coder          → writeCode()
"proger"          → Proger         → enjoy()
любое другое слово → завершение программы
```
