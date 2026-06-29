---
title: 30 Python OOP Problems
tags:
 - python
 - oop
description: 30 coding problems about Object-Oriented Programming in Python from all levels.
---

# 30 Python OOP Problems

This page contains 30 Python Object-Oriented Programming (OOP) problems ranging from basic to advanced levels, along with their solutions.

## Basic Level

### 1. Create a basic class
**Question:** Define a class named `Car` with two attributes: `make` and `model`.

**Answer:**
```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model
```

### 2. Instantiate an object
**Question:** Create an instance of the `Car` class with make "Toyota" and model "Camry".

**Answer:**
```python
my_car = Car("Toyota", "Camry")
```

### 3. Add a method
**Question:** Add a method `start_engine` to the `Car` class that prints "Engine started".

**Answer:**
```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model

    def start_engine(self):
        print("Engine started")
```

### 4. Student Class
**Question:** Create a `Student` class with `name` and `age` attributes.

**Answer:**
```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

### 5. String Representation
**Question:** Implement the `__str__` method in the `Student` class to return "Name: [name], Age: [age]".

**Answer:**
```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"Name: {self.name}, Age: {self.age}"
```

### 6. Basic Inheritance
**Question:** Create a class `ElectricCar` that inherits from `Car` and adds a `battery_size` attribute.

**Answer:**
```python
class ElectricCar(Car):
    def __init__(self, make, model, battery_size):
        super().__init__(make, model)
        self.battery_size = battery_size
```

### 7. Method Overriding
**Question:** Override the `start_engine` method in `ElectricCar` to print "Silent start".

**Answer:**
```python
class ElectricCar(Car):
    def start_engine(self):
        print("Silent start")
```

### 8. Area of a Circle
**Question:** Create a `Circle` class with a `radius` attribute and a method `get_area` that returns the area.

**Answer:**
```python
import math

class Circle:
    def __init__(self, radius):
        self.radius = radius

    def get_area(self):
        return math.pi * (self.radius ** 2)
```

### 9. Encapsulation
**Question:** Create a `Book` class with a private attribute `__price`.

**Answer:**
```python
class Book:
    def __init__(self, title, price):
        self.title = title
        self.__price = price
```

### 10. Getters and Setters
**Question:** Add a getter and a setter for the `__price` attribute in the `Book` class.

**Answer:**
```python
class Book:
    def __init__(self, title, price):
        self.title = title
        self.__price = price

    def get_price(self):
        return self.__price

    def set_price(self, new_price):
        if new_price > 0:
            self.__price = new_price
```

---

## Intermediate Level

### 11. Multiple Inheritance
**Question:** Create a `Smartphone` class that inherits from both `Phone` and `Camera`.

**Answer:**
```python
class Phone:
    def make_call(self):
        print("Calling...")

class Camera:
    def take_photo(self):
        print("Click!")

class Smartphone(Phone, Camera):
    pass
```

### 12. Using `super()`
**Question:** In a subclass, how do you call the constructor of the parent class?

**Answer:**
Using `super().__init__(arguments)`.

### 13. Class vs Instance Variables
**Question:** Create a `Robot` class with a class variable `population` that increments every time a new robot is created.

**Answer:**
```python
class Robot:
    population = 0

    def __init__(self, name):
        self.name = name
        Robot.population += 1
```

### 14. Class Methods
**Question:** Use a `@classmethod` to create a factory method that creates a `Person` object from a birth year.

**Answer:**
```python
from datetime import date

class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod
    def from_birth_year(cls, name, year):
        return cls(name, date.today().year - year)
```

### 15. Static Methods
**Question:** Create a `MathUtils` class with a `@staticmethod` named `is_even` that checks if a number is even.

**Answer:**
```python
class MathUtils:
    @staticmethod
    def is_even(n):
        return n % 2 == 0
```

### 16. Abstract Base Classes
**Question:** Define an abstract class `Shape` with an abstract method `area()`.

**Answer:**
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass
```

### 17. Operator Overloading
**Question:** Overload the `+` operator for a `Point` class with `x` and `y` coordinates.

**Answer:**
```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)
```

### 18. Property Decorator
**Question:** Use the `@property` decorator to make an attribute `email` read-only in a `User` class.

**Answer:**
```python
class User:
    def __init__(self, username, email):
        self.username = username
        self._email = email

    @property
    def email(self):
        return self._email
```

### 19. Composition
**Question:** Demonstrate composition by creating a `Library` class that holds a list of `Book` objects.

**Answer:**
```python
class Book:
    def __init__(self, title):
        self.title = title

class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)
```

### 20. Method Overloading (Simulation)
**Question:** How do you simulate method overloading in Python?

**Answer:**
By using default arguments or `*args` and `**kwargs`.
```python
class Calculator:
    def add(self, a, b, c=0):
        return a + b + c
```

---

## Advanced Level

### 21. Iterators in Classes
**Question:** Make a `MyRange` class that works like the built-in `range()` by implementing `__iter__` and `__next__`.

**Answer:**
```python
class MyRange:
    def __init__(self, start, end):
        self.current = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.current >= self.end:
            raise StopIteration
        val = self.current
        self.current += 1
        return val
```

### 22. Metaclasses
**Question:** Create a metaclass `Singleton` that ensures only one instance of a class can exist.

**Answer:**
```python
class Singleton(type):
    _instances = {}
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Database(metaclass=Singleton):
    pass
```

### 23. Mixins
**Question:** What is a Mixin? Provide a simple example.

**Answer:**
A Mixin is a class that provides methods to other classes but isn't intended to stand alone.
```python
import json

class JSONMixin:
    def to_json(self):
        return json.dumps(self.__dict__)

class Employee(JSONMixin):
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary
```

### 24. Context Managers
**Question:** Implement a class-based context manager for a file opener.

**Answer:**
```python
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.file.close()
```

### 25. Method Decorators
**Question:** Create a decorator `timer` that prints the time taken by a method.

**Answer:**
```python
import time

def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"Executed in {end - start}s")
        return result
    return wrapper

class MyClass:
    @timer
    def slow_method(self):
        time.sleep(1)
```

### 26. `__slots__`
**Question:** What is the purpose of `__slots__`?

**Answer:**
It restricts the creation of instance attributes to a fixed set, saving memory by preventing the creation of `__dict__`.
```python
class Point:
    __slots__ = ('x', 'y')
    def __init__(self, x, y):
        self.x = x
        self.y = y
```

### 27. Deep vs Shallow Copy
**Question:** How do you create a deep copy of an object?

**Answer:**
Using the `copy` module.
```python
import copy
new_obj = copy.deepcopy(old_obj)
```

### 28. Method Resolution Order (MRO)
**Question:** What is MRO and how can you view it for a class?

**Answer:**
MRO is the order in which Python looks for a method in a hierarchy. View it using `ClassName.mro()` or `ClassName.__mro__`.

### 29. Descriptor Protocol
**Question:** Create a descriptor `NonNegative` that ensures an attribute cannot be set to a negative value.

**Answer:**
```python
class NonNegative:
    def __init__(self, name):
        self.name = name
    def __set__(self, instance, value):
        if value < 0:
            raise ValueError("Must be non-negative")
        instance.__dict__[self.name] = value

class Inventory:
    price = NonNegative('price')
    def __init__(self, price):
        self.price = price
```

### 30. `__call__` method
**Question:** What does the `__call__` method do?

**Answer:**
It allows an instance of a class to be called as a function.
```python
class Greeter:
    def __init__(self, greeting):
        self.greeting = greeting
    def __call__(self, name):
        print(f"{self.greeting}, {name}!")

hi = Greeter("Hello")
hi("Alice") # Output: Hello, Alice!
```
