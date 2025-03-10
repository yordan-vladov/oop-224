# Абстрактни класове

Абстрактните класове в обектно-ориентираното програмиране (ООП) са класове, които не могат да бъдат инстанцирани (т.е. не може да се създават обекти от тях директно). Те служат като шаблон или базов клас за други класове, които ще ги наследяват. Абстрактните класове обикновено съдържат един или повече абстрактни методи, които са методи без имплементация (т.е. без тяло) и трябва да бъдат имплементирани от наследяващите класове.

## Характеристики

1. **Не могат да бъдат инстанцирани**: Не може да се създават обекти директно от абстрактен клас.
2. **Съдържат абстрактни методи**: Методи, които нямат имплементация и трябва да бъдат имплементирани от наследниците.
3. **Могат да съдържат и конкретни методи**: Абстрактните класове могат да имат и методи с имплементация, които могат да бъдат наследени и използвани от подкласовете.

## Абстрактни класове в Python

В Python, абстрактните класове се създават с помощта на модула `abc` (Abstract Base Classes). Този модул предоставя декоратори и класове за дефиниране на абстрактни методи и класове.

```python
from abc import ABC, abstractmethod

# Дефиниране на абстрактен клас
class Animal(ABC):

    @abstractmethod
    def sound(self):
        pass  # Абстрактният метод няма имплементация

    def sleep(self):
        print("This animal is sleeping.")  # Конкретен метод с имплементация

# Наследяване на абстрактния клас
class Dog(Animal):

    def sound(self):
        return "Woof!"

class Cat(Animal):

    def sound(self):
        return "Meow!"

# Опит за инстанциране на абстрактен клас ще доведе до грешка
# animal = Animal()  # Това ще предизвика TypeError

# Създаване на обекти от наследените класове
dog = Dog()
cat = Cat()

print(dog.sound())  # Изход: Woof!
print(cat.sound())  # Изход: Meow!

dog.sleep()  # Изход: This animal is sleeping.
cat.sleep()  # Изход: This animal is sleeping.
```

1. **Animal** е абстрактен клас, който наследява от `ABC` (Abstract Base Class). Той съдържа абстрактен метод `sound()` и конкретен метод `sleep()`.
2. **Dog** и **Cat** са класове, които наследяват `Animal` и имплементират абстрактния метод `sound()`.
3. Ако се опитаме да създадем обект от класа `Animal`, ще получим грешка, защото той е абстрактен и не може да бъде инстанциран.
4. Обектите от класовете `Dog` и `Cat` могат да извикват както абстрактния метод `sound()`, така и конкретния метод `sleep()`.

Абстрактните класове са полезни, когато искате да дефинирате общ интерфейс или поведение за група от класове, но не искате да позволявате инстанциране на самия базов клас. Те гарантират, че всички подкласове имплементират определени методи, което прави кода по-предсказуем и структуриран.

## Задачи за самостоятелна работа

### Задача 1: **Система за управление на служители**

Създайте абстрактен клас `Employee`, който дефинира абстрактни методи за изчисляване на заплата (`calculate_salary`) и показване на информация за служителя (`display_info`). След това създайте подкласове за различни типове служители (например `FullTimeEmployee`, `PartTimeEmployee`).

**Примерна употреба:**

```python
full_time = FullTimeEmployee("John Doe", "Developer", 3000)
part_time = PartTimeEmployee("Jane Smith", "Designer", 20, 80)

print(full_time.display_info())  # Изход: Full-Time Developer: John Doe, Salary: 3000
print(part_time.display_info())  # Изход: Part-Time Designer: Jane Smith, Salary: 1600
```

### Задача 2: **Система за управление на библиотека**

Създайте абстрактен клас `LibraryItem`, който дефинира абстрактни методи за заемане (`check_out`), връщане (`return_item`) и показване на информация (`display_info`). След това създайте подкласове за различни типове библиотечни артикули (например `Book`, `Magazine`).

**Примерна употреба:**

```python
book = Book("1984", "George Orwell")
magazine = Magazine("National Geographic", "Various Authors")

print(book.check_out())  # Изход: Book '1984' by George Orwell has been checked out.
print(magazine.check_out())  # Изход: Magazine 'National Geographic' by Various Authors has been checked out.

print(book.display_info())  # Изход: Book: 1984 by George Orwell, Status: Checked Out
print(magazine.display_info())  # Изход: Magazine: National Geographic by Various Authors, Status: Checked Out
```

### Задача 3: **Система за управление на герои в игра**

Създайте абстрактен клас `GameCharacter`, който дефинира абстрактни методи за движение (`move`), атака (`attack`) и показване на информация (`display_info`). След това създайте подкласове за различни типове герои (например `Warrior`, `Mage`).

**Примерна употреба:**

```python
warrior = Warrior("Conan", 100)
mage = Mage("Gandalf", 80)

print(warrior.move())  # Изход: Conan moves forward with a sword.
print(mage.attack())  # Изход: Gandalf casts a fireball!

print(warrior.display_info())  # Изход: Warrior: Conan, Health: 100
print(mage.display_info())  # Изход: Mage: Gandalf, Health: 80
```

### Задача 4: **Система за управление на задачи**

Създайте абстрактен клас `Task`, който дефинира абстрактни методи за стартиране (`start`), завършване (`complete`) и показване на информация (`display_info`). След това създайте подкласове за различни типове задачи (например `WorkTask`, `PersonalTask`).

**Примерна употреба:**

```python
work_task = WorkTask("Write Report", "Finish the quarterly report")
personal_task = PersonalTask("Buy Groceries", "Milk, Bread, Eggs")

print(work_task.start())  # Изход: Starting work task: Write Report
print(personal_task.complete())  # Изход: Completed personal task: Buy Groceries

print(work_task.display_info())  # Изход: Work Task: Write Report, Description: Finish the quarterly report, Status: Not Completed
print(personal_task.display_info())  # Изход: Personal Task: Buy Groceries, Description: Milk, Bread, Eggs, Status: Completed
```

### Задача 5: **Система за документи**

Създайте абстрактен клас `Document`, който дефинира абстрактни методи за отваряне (`open`), затваряне (`close`) и запазване (`save`). След това създайте подкласове за различни типове документи (например `TextDocument`, `SpreadsheetDocument`, `PDFDocument`).

**Примерна употреба:**

```python
# Примерна употреба
text_doc = TextDocument()
pdf_doc = PDFDocument()

print(text_doc.open())  # Изход: Text document opened
print(text_doc.save())  # Изход: Text document saved
print(text_doc.close())  # Изход: Text document closed

print(pdf_doc.open())  # Изход: PDF document opened
print(pdf_doc.save())  # Изход: PDF document saved
print(pdf_doc.close())  # Изход: PDF document closed
```
