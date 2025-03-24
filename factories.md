# Factory класове

В обектно-ориентираното програмиране (OOP), **Factory класовете** са шаблон за създаване на обекти (creational design pattern), който предоставя интерфейс за създаване на обекти в суперклас, но позволява на подкласовете да променят типа на създаваните обекти. Това е полезно, когато имате йерархия от класове и искате да създавате обекти от различни типове в зависимост от някакво условие.
### Основна идея:
- **Factory класът** е отговорен за създаването на обекти, вместо да използвате директно конструктора на класа.
- Той скрива логиката за създаване на обекти и позволява на клиентския код да работи с абстракции, вместо с конкретни класове.
### Пример:

Нека разгледаме пример, в който имаме йерархия от класове за различни видове транспортни средства (например, кола, камион, мотоциклет). Ще използваме Factory клас, за да създаваме обекти от тези типове.

```python
# Дефинираме базов клас за транспортното средство
class Vehicle:
    def drive(self):
        pass

# Дефинираме конкретни класове за различни видове транспортни средства
class Car(Vehicle):
    def drive(self):
        return "Driving a car"

class Truck(Vehicle):
    def drive(self):
        return "Driving a truck"

class Motorcycle(Vehicle):
    def drive(self):
        return "Riding a motorcycle"

# Дефинираме Factory клас, който създава обекти от различни типове транспортни средства
class VehicleFactory:
    @staticmethod
    def create_vehicle(vehicle_type):
        if vehicle_type == "car":
            return Car()
        elif vehicle_type == "truck":
            return Truck()
        elif vehicle_type == "motorcycle":
            return Motorcycle()
        else:
            raise ValueError("Unknown vehicle type")

# Клиентски код, който използва Factory класа
if __name__ == "__main__":
    # Създаваме обект от тип "кола" чрез Factory класа
    car = VehicleFactory.create_vehicle("car")
    print(car.drive())  # Изход: Driving a car

    # Създаваме обект от тип "камион" чрез Factory класа
    truck = VehicleFactory.create_vehicle("truck")
    print(truck.drive())  # Изход: Driving a truck

    # Създаваме обект от тип "мотоциклет" чрез Factory класа
    motorcycle = VehicleFactory.create_vehicle("motorcycle")
    print(motorcycle.drive())  # Изход: Riding a motorcycle
```
### Обяснение:
1. **Vehicle**: Това е базовият клас, който дефинира общия интерфейс за всички транспортни средства. Всички конкретни класове (Car, Truck, Motorcycle) наследяват този базов клас и имплементират метода `drive`.

2. **VehicleFactory**: Това е Factory класът, който съдържа статичен метод `create_vehicle`. Този метод приема параметър `vehicle_type` и връща съответния обект от тип `Vehicle`. Логиката за създаване на обектите е скрита в този метод.

3. **Клиентски код**: Клиентският код използва Factory класа, за да създава обекти, без да се налага да знае конкретните детайли за създаването на тези обекти. Той просто подава типа на транспортното средство и получава съответния обект.

### Предимства на Factory класовете:
- **Разделяне на отговорностите**: Логиката за създаване на обекти е отделена от основната логика на програмата.
- **Гъвкавост**: Лесно можете да добавяте нови типове обекти, без да променяте клиентския код.
- **Прозрачност**: Клиентският код работи с абстракции, което го прави по-лесен за разбиране и поддръжка.

Този шаблон е особено полезен, когато имате сложна логика за създаване на обекти или когато искате да централизирате тази логика на едно място.

Ето пет задачи, които използват **Factory класове** в Python. Всяка задача демонстрира различен аспект на шаблона за създаване на обекти и показва как той може да се приложи в различни контексти.

## Задачи за самостоятелна работа

### 1. **Система за управление на документи**
Създайте система за управление на документи, която създава различни типове документи (текстови, PDF, Excel) с помощта на Factory клас.

```python
from abc import ABC, abstractmethod

# Базов клас за документи
class Document(ABC):
    @abstractmethod
    def open(self):
        pass

# Конкретни класове за документи
class TextDocument(Document):
    pass # TODO: Реализирайте класа


class PDFDocument(Document):
    pass # TODO: Реализирайте класа

class ExcelDocument(Document):
    pass # TODO: Реализирайте класа

# Factory клас за създаване на документи
class DocumentFactory:
    @staticmethod
    def create_document(doc_type):
	    pass # TODO: Реализирайте метода

# Клиентски код
if __name__ == "__main__":
    doc1 = DocumentFactory.create_document("text")
    print(doc1.open())  # Изход: Opening a Text Document

    doc2 = DocumentFactory.create_document("pdf")
    print(doc2.open())  # Изход: Opening a PDF Document
```
### 2. **Система за управление на фигури**
Създайте система за управление на геометрични фигури (кръг, квадрат, триъгълник), която използва Factory клас за създаване на обекти.

```python
from abc import ABC, abstractmethod
import math

# Базов клас за фигури
class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

# Конкретни класове за фигури
class Circle(Shape):
    pass # TODO: Реализирайте класа

class Square(Shape):
    pass # TODO: Реализирайте класа

class Triangle(Shape):
    pass # TODO: Реализирайте класа

# Factory клас за създаване на фигури
class ShapeFactory:
    @staticmethod
    def create_shape(shape_type, *args):
		pass # TODO: Реализирайте метода

# Клиентски код
if __name__ == "__main__":
    circle = ShapeFactory.create_shape("circle", 5)
    print(f"Area of Circle: {circle.area():.2f}")  # Изход: Area of Circle: 78.54

    square = ShapeFactory.create_shape("square", 4)
    print(f"Area of Square: {square.area()}")  # Изход: Area of Square: 16
```
### 3. **Система за управление на животни**
Създайте система за управление на животни (куче, котка, птица), която използва Factory клас за създаване на обекти.

```python
from abc import ABC, abstractmethod

# Базов клас за животни
class Animal(ABC):
    @abstractmethod
    def speak(self):
        pass

# Конкретни класове за животни
class Dog(Animal):
    pass # TODO: Реализирайте класа

class Cat(Animal):
    pass # TODO: Реализирайте класа

class Bird(Animal):
    pass # TODO: Реализирайте класа

# Factory клас за създаване на животни
class AnimalFactory:
    @staticmethod
    def create_animal(animal_type):
        pass # TODO: Реализирайте метода

# Клиентски код
if __name__ == "__main__":
    dog = AnimalFactory.create_animal("dog")
    print(dog.speak())  # Изход: Woof!

    cat = AnimalFactory.create_animal("cat")
    print(cat.speak())  # Изход: Meow!
```
### 4. **Система за управление на бази данни**
Създайте система за управление на връзки с бази данни (MySQL, PostgreSQL, SQLite), която използва Factory клас за създаване на обекти.

```python
from abc import ABC, abstractmethod

# Базов клас за връзки с бази данни
class DatabaseConnection(ABC):
    @abstractmethod
    def connect(self):
        pass

# Конкретни класове за връзки с бази данни
class MySQLConnection(DatabaseConnection):
    pass # TODO: Реализирайте класа

class PostgreSQLConnection(DatabaseConnection):
    pass # TODO: Реализирайте класа

class SQLiteConnection(DatabaseConnection):
    pass # TODO: Реализирайте класа

# Factory клас за създаване на връзки
class DatabaseFactory:
    @staticmethod
    def create_connection(db_type):
        pass # TODO: Реализирайте метода

# Клиентски код
if __name__ == "__main__":
    db1 = DatabaseFactory.create_connection("mysql")
    print(db1.connect())  # Изход: Connected to MySQL

    db2 = DatabaseFactory.create_connection("sqlite")
    print(db2.connect())  # Изход: Connected to SQLite
```
### 5. **Система за управление на игрални герои**
Създайте система за управление на игрални герои (воин, магьосник, ловец), която използва Factory клас за създаване на обекти.

```python
from abc import ABC, abstractmethod

# Базов клас за герои
class Character(ABC):
    @abstractmethod
    def attack(self):
        pass

# Конкретни класове за герои
class Warrior(Character):
	pass # TODO: Реализирайте класа

class Mage(Character):
    pass # TODO: Реализирайте класа

class Archer(Character):
    pass # TODO: Реализирайте класа

# Factory клас за създаване на герои
class CharacterFactory:
    @staticmethod
    def create_character(character_type):
        pass # TODO: Реализирайте метода

# Клиентски код
if __name__ == "__main__":
    warrior = CharacterFactory.create_character("warrior")
    print(warrior.attack())  # Изход: Warrior attacks with a sword!

    mage = CharacterFactory.create_character("mage")
    print(mage.attack())  # Изход: Mage casts a fireball!
```
### Обобщение:
Тези задачи демонстрират как **Factory класовете** могат да се използват за създаване на обекти в различни контексти. Основната идея е да се скрие логиката за създаване на обекти и да се предостави гъвкавост за добавяне на нови типове обекти в бъдеще.
