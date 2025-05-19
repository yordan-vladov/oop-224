# Strategy Pattern

**Strategy Pattern** (шаблон „Стратегия“) е поведенчески шаблон за дизайн, който позволява дефиниране на семейство от взаимозаменяеми алгоритми (стратегии), които могат да се сменят по време на изпълнение.

## Кога се използва?

- Когато имате различни начини за изпълнение на дадена операция
- Когато искате да избегнете използването на множество условни конструкции (`if`, `elif`)
- Когато искате да направите поведението лесно разширяемо и подменяемо

## Пример в Python

```python
from abc import ABC, abstractmethod

# Абстрактна стратегия
class DiscountStrategy(ABC):
    @abstractmethod
    def apply_discount(self, price):
        pass

# Конкретни стратегии
class NoDiscount(DiscountStrategy):
    def apply_discount(self, price):
        return price

class PercentageDiscount(DiscountStrategy):
    def __init__(self, percent):
        self.percent = percent

    def apply_discount(self, price):
        return price * (1 - self.percent / 100)

class FixedDiscount(DiscountStrategy):
    def __init__(self, amount):
        self.amount = amount

    def apply_discount(self, price):
        return max(0, price - self.amount)

# Контекст, използващ стратегията
class PriceCalculator:
    def __init__(self, discount_strategy: DiscountStrategy):
        self.discount_strategy = discount_strategy

    def set_discount_strategy(self, strategy: DiscountStrategy):
        self.discount_strategy = strategy

    def calculate_price(self, price):
        return self.discount_strategy.apply_discount(price)

# Използване
if __name__ == "__main__":
    calculator = PriceCalculator(NoDiscount())
    print("Без отстъпка:", calculator.calculate_price(100))  # 100

    calculator.set_discount_strategy(PercentageDiscount(20))
    print("20% отстъпка:", calculator.calculate_price(100))  # 80

    calculator.set_discount_strategy(FixedDiscount(15))
    print("Фиксирана отстъпка 15лв:", calculator.calculate_price(100))  # 85
```

## Обяснение на примера

1. **DiscountStrategy (абстрактен клас)** – определя интерфейс за стратегията на отстъпките.
2. **NoDiscount, PercentageDiscount, FixedDiscount** – конкретни реализации на стратегии.
3. **PriceCalculator** – контекст, който използва избраната стратегия за изчисление.
4. **Използване на стратегии** – може да сменяме стратегията в движение чрез `set_discount_strategy()`.

## Предимства

- Позволява лесно добавяне на нови стратегии
- Намалява броя на условните конструкции
- Стратегиите могат да се тестват и използват независимо
- Следва принципа за отвореност/затвореност (Open/Closed Principle)

## Задачи за самостоятелна работа

### 1. Buy-One-Get-One-Free стратегия

Създайте стратегия `BuyOneGetOneFree`, която връща половината от цената (например 2 артикула на цената на 1):

```python
class BuyOneGetOneFree(DiscountStrategy):
    pass # Имплементирайте метода
```

### 2. Black Friday отстъпка

Създайте стратегия `BlackFridayDiscount`, която прилага 50% отстъпка, но само ако цената е над 200 лв.

```python
class BlackFridayDiscount(DiscountStrategy):
    pass # Имплементирайте метода
```

### 3. Калкулатор за списък с продукти

Разширете `PriceCalculator`, така че да може да изчислява обща стойност на списък от продукти с избраната стратегия.

```python
def calculate_total(self, prices: list):
    pass # Имплементирайте метода
```

### 4. Графичен интерфейс с Tkinter (по избор)

Създайте GUI приложение, което:
- Позволява избор на стратегия от падащо меню
- Позволява въвеждане на цена/и
- Показва крайната сума
