# Наследяване

Наследяването в обектно-ориентираното програмиране (ООП) е механизъм, който позволява на един клас (наречен **детелен клас** или **подклас**) да наследи свойства и методи от друг клас (наречен **родителски клас** или **суперклас**). Това позволява повторно използване на код и създаване на йерархия от класове, които споделят обща функционалност.
### Основни понятия:

1. **Parent клас (суперклас)**: Класът, който предоставя свойствата и методите.
2. **Child клас (подклас)**: Класът, който наследява от родителския клас и може да добавя или променя функционалност.

## Наследяване - Пример

```python
# Родителски клас
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        return f"{self.name} makes a sound."

# Child клас, който наследява от Animal
class Dog(Animal):
    def speak(self):
        return f"{self.name} barks."

# Друг child клас, който наследява от Animal
class Cat(Animal):
    def speak(self):
        return f"{self.name} meows."

# Създаване на инстанции
dog = Dog("Buddy")
cat = Cat("Whiskers")

# Извикване на методите
print(dog.speak())  # Изход: Buddy barks.
print(cat.speak())  # Изход: Whiskers meows.
```

1. **Родителският клас `Animal`**:
    - Има метод `__init__`, който инициализира свойството `name`.
    - Има метод `speak`, който връща общо съобщение за звука на животното.
2. **Child класове `Dog` и `Cat`**:
    - Наследяват от `Animal` и затова имат достъп до свойството `name` и метода `speak`.
    - Предефинират (override) метода `speak`, за да предоставят специфично поведение за съответното животно.

## Предимства

- **Повторно използване на код**: Не е необходимо да пишете същия код многократно.
- **Разширяемост**: Можете да добавяте нови класове, които наследяват от съществуващи, без да променяте оригиналния код.
- **Йерархия**: Създава логична структура на класовете, която отразява реалните взаимоотношения между обектите.

## Допълнителни възможности

### super()

`super()` функцията позволява на един child клас да извиква методите на неговият родител.

```python
class Bird(Animal):
    def speak(self):
        original_sound = super().speak()
        return f"{original_sound} But {self.name} also chirps."

bird = Bird("Tweety")
print(bird.speak())  # Изход: Tweety makes a sound. But Tweety also chirps.
```

### Множествено наследяване

Множественото наследяване в Python позволява на един клас да наследява от **няколко родителски класа**. Това означава, че детелият клас може да използва атрибути и методи от всичките си родителски класове. Това е мощна възможност, но трябва да се използва внимателно, за да се избегнат конфликти или неочаквано поведение.

```python
# Първи родителски клас
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        return f"{self.name} makes a sound."

# Втори родителски клас
class CanFly:
    def fly(self):
        return f"{self.name} is flying."

# Трети родителски клас
class CanSwim:
    def swim(self):
        return f"{self.name} is swimming."

# Детелен клас, който наследява от Animal, CanFly и CanSwim
class Duck(Animal, CanFly, CanSwim):
    def speak(self):
        return f"{self.name} quacks."

# Създаване на инстанция
duck = Duck("Donald")

# Извикване на методите
print(duck.speak())  # Изход: Donald quacks.
print(duck.fly())    # Изход: Donald is flying.
print(duck.swim())   # Изход: Donald is swimming.
```

1. **Родителските класове**:
    - `Animal`: Дефинира основното поведение на животното, включително метод `speak`.
    - `CanFly`: Добавя функционалност за летене чрез метод `fly`.
    - `CanSwim`: Добавя функционалност за плуване чрез метод `swim`.
2. **Child клас `Duck`**:
    - Наследява от три класа: `Animal`, `CanFly` и `CanSwim`.
    - Предефинира метода `speak`, за да предостави специфично поведение за патицата.
    - Има достъп до методите `fly` и `swim` от родителските класове.

## Задачи за самостоятелна работа

### **Задача 1: Животни**

Създай йерархия от класове за различни видове животни:
- Родителски клас `Animal` с метод `speak()`.
- Child класове `Dog`, `Cat`, `Bird`, които наследяват `Animal` и предефинират метода `speak()`.
- Добави метод `eat()`, който да е общ за всички животни.

**Примерен изход:**

```txt
Buddy barks.
Whiskers meows.
Tweety chirps.
Buddy is eating.
```

### **Задача 2: Геометрични фигури**

Създай класове за геометрични фигури:
- Родителски клас `Shape` с метод `area()`.
- Детелни класове `Circle`, `Rectangle`, `Triangle`, които наследяват `Shape` и имплементират метода `area()`.
- Добави метод `perimeter()` за всяка фигура.

**Примерен изход:**

```txt
Area of Circle: 78.54
Perimeter of Circle: 31.42
Area of Rectangle: 20
Perimeter of Rectangle: 18
```

### **Задача 3: Транспортни средства**

Създай йерархия за транспортни средства:
- Родителски клас `Vehicle` с атрибути `brand` и `year` и метод `start()`.
- Детелни класове `Car`, `Bicycle`, `Motorcycle`, които наследяват `Vehicle` и добавят специфични методи (напр. `drive()` за колата и `pedal()` за велосипеда).
- Добави метод `stop()`, който да е общ за всички транспортни средства.

**Примерен изход:**

```txt
Toyota (2020) is starting.
Toyota is driving.
Bicycle is pedaling.
Toyota is stopping.
```

### **Задача 4: Служители в компания**

Създай класове за служители в компания:
- Родителски клас `Employee` с атрибути `name`, `salary` и метод `work()`.
- Детелни класове `Manager`, `Developer`, `Intern`, които наследяват `Employee` и предефинират метода `work()`.
- Добави метод `take_break()`, който да е общ за всички служители.

**Примерен изход:**
```txt
John (Manager) is managing the team.
John is taking a break.
Alice (Developer) is writing code.
Bob (Intern) is learning.
```

### **Задача 5: Банкови сметки**

Създай класове за банкови сметки:

- Родителски клас `BankAccount` с атрибути `account_number` и `balance` и методи `deposit()` и `withdraw()`.
- Детелни класове `SavingsAccount` и `CheckingAccount`, които наследяват `BankAccount`.
    - `SavingsAccount` трябва да има метод `add_interest()`, който добавя лихва към баланса.
    - `CheckingAccount` трябва да има метод `deduct_fees()`, който удържа такси от баланса.

```txt
Savings Account (12345) balance: 1050.0
Checking Account (67890) balance: 900.0
```
### **Бонус задача: Множествено наследяване**

Създай класове, които използват множествено наследяване:
- Родителски класове `ElectricAppliance` и `SmartDevice`.
- Детелен клас `SmartTV`, който наследява и двата класа.
- Добави методи `turn_on()` и `connect_to_wifi()`.

**Примерен изход:**
```txt
SmartTV is turning on.
SmartTV is connecting to Wi-Fi.
```
