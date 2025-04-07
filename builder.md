# Builder Pattern

Builder Pattern (шаблон "Строител") е шаблон за дизайн, който се използва за конструиране на сложни обекти стъпка по стъпка. Той позволява създаването на различни конфигурации на обект, без да се замърсява конструкторът с много параметри.

## Кога се използва?

- Когато обектът има много опционални параметри
- Когато искаме процесът на създаване да бъде отделен от самия обект
- Когато искаме да създаваме различни варианти на един обект

## Пример в Python

```python
class Pizza:
    def __init__(self):
        self.size = None
        self.cheese = False
        self.pepperoni = False
        self.mushrooms = False
        self.bacon = False

    def __str__(self):
        return f"Pizza: size={self.size}, cheese={self.cheese}, pepperoni={self.pepperoni}, mushrooms={self.mushrooms}, bacon={self.bacon}"

class PizzaBuilder:
    def __init__(self):
        self.pizza = Pizza()

    def set_size(self, size):
        self.pizza.size = size
        return self

    def add_cheese(self):
        self.pizza.cheese = True
        return self

    def add_pepperoni(self):
        self.pizza.pepperoni = True
        return self

    def add_mushrooms(self):
        self.pizza.mushrooms = True
        return self

    def add_bacon(self):
        self.pizza.bacon = True
        return self

    def build(self):
        return self.pizza

# Използване на Builder
builder = PizzaBuilder()
pizza = (builder.set_size("Large")
                .add_cheese()
                .add_pepperoni()
                .add_bacon()
                .build())

print(pizza)
```

## Обяснение на примера

1. **Pizza клас**: Това е сложният обект, който искаме да конструираме. Има много възможни атрибути.

2. **PizzaBuilder клас**: Този клас е отговорен за стъпковото изграждане на Pizza обекта:
   - Всеки метод задава определен атрибут
   - Методите връщат `self`, което позволява method chaining (верижно извикване на методи)
   - `build()` метода връща готовия обект

3. **Използване**:
   - Създаваме builder инстанция
   - Извикваме методите за конфигуриране стъпка по стъпка
   - Накрая извикваме `build()` за да получим готовия обект

## Предимства

- Избягваме конструктори с много параметри
- Кодът е по-четлив и по-лесен за поддръжка
- Позволява създаване на различни варианти на обекта
- Капсулира логиката за създаване

Този шаблон е особено полезен, когато обектите имат много конфигурационни опции или когато процесът на създаване включва няколко стъпки.

## Задачи за самостоятелна работа

### 1. Конструиране на автомобил

Създайте клас `CarBuilder`, който да позволява стъпково конструиране на автомобил с различни характеристики като модел, двигател, цвят, брой колела и наличие на люк.

```python
class Car:
    def __init__(self):
        self.model = None
        self.engine = None
        self.color = "White"
        self.wheels = 4
        self.sunroof = False

class CarBuilder:
    def __init__(self):
        self.car = Car()

    def set_model(self, model):
        pass # имплементирайте метода
    def set_engine(self, engine):
        pass # имплементирайте метода

    def set_color(self, color):
        pass # имплементирайте метода
    def set_wheels(self, wheels):
        pass # имплементирайте метода

    def add_sunroof(self):
        pass # имплементирайте метода

    def build(self):
        return self.car

# Използване:
car = (CarBuilder()
       .set_model("Tesla Model S")
       .set_engine("Electric")
       .set_color("Red")
       .add_sunroof()
       .build())
```

### 2. Генериране на SQL заявки

Реализирайте `SQLQueryBuilder`, който да конструира SQL заявки с възможност за избор на колони, задаване на таблица и добавяне на WHERE условия.

```python
class SQLQuery:
    def __init__(self):
        self.table = None
        self.fields = []
        self.where_conditions = []

    def __str__(self):
        fields = ", ".join(self.fields) if self.fields else "*"
        where = f" WHERE {' AND '.join(self.where_conditions)}" if self.where_conditions else ""
        return f"SELECT {fields} FROM {self.table}{where}"

class SQLQueryBuilder:
    def __init__(self):
        self.query = SQLQuery()

    def select(self, *fields):
        pass # Имплементирайте метода

    def from_table(self, table):
        pass # Имплементирайте метода

    def where(self, condition):
        pass # Имплементирайте метода

    def build(self):
        return self.query

# Използване:
query = (SQLQueryBuilder()
         .select("id", "name", "email")
         .from_table("users")
         .where("age > 18")
         .where("status = 'active'")
         .build())
print(query)
```

### 3. Създаване на герой за RPG игра

Направете клас `CharacterBuilder` за създаване на герои с име, класа, ниво, оръжие и броня, като позволява гъвкаво конфигуриране.

```python
class Character:
    def __init__(self):
        self.name = "Unknown"
        self.character_class = None
        self.level = 1
        self.weapon = None
        self.armor = None

class CharacterBuilder:
    pass # имплементирайте класа

# Използване:
hero = (CharacterBuilder()
        .set_name("Gandalf")
        .set_class("Wizard")
        .set_level(10)
        .set_weapon("Staff")
        .set_armor("Robe")
        .build())
```

### 4. Изграждане на компютърна конфигурация

Създайте клас `ComputerBuilder` за конфигуриране на компютърни системи с компоненти като процесор, RAM, памет и видео карта.

```python
class Computer:
    def __init__(self):
        self.cpu = None
        self.ram = None
        self.storage = None
        self.gpu = None

class ComputerBuilder:
    pass # имплементирайте класа


# Използване:
gaming_pc = (ComputerBuilder()
             .set_cpu("Intel i9")
             .set_ram("32GB DDR5")
             .set_storage("1TB NVMe SSD")
             .set_gpu("NVIDIA RTX 4090")
             .build())
```

### 5. Създаване на персонализирана бургер поръчка

Имплементирайте клас `BurgerBuilder` за съставяне на бургери с различни видове питки, месо, допълнителни съставки и сосове.

```python
class Burger:
    def __init__(self):
        self.bun = None
        self.patty = None
        self.cheese = False
        self.lettuce = False
        self.tomato = False
        self.sauce = None

class BurgerBuilder:
    pass # Имплементирайте класа

# Използване:
my_burger = (BurgerBuilder()
             .set_bun("Sesame")
             .set_patty("Beef")
             .add_cheese()
             .add_lettuce()
             .add_tomato()
             .set_sauce("BBQ")
             .build())
```
