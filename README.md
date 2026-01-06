# 🎓 COMPLETE OOP (Object-Oriented Programming) GUIDE
## A-Z For Interviews | Easy Explanations | Real Examples | Master OOP Forever

---

# 📚 TABLE OF CONTENTS

## PART 1: FOUNDATIONS
1. [What is OOP?](#what-is-oop)
2. [Why Use OOP?](#why-use-oop)
3. [Core Concepts](#core-concepts)

## PART 2: FOUR PILLARS
4. [Pillar 1: Encapsulation](#pillar-1-encapsulation)
5. [Pillar 2: Abstraction](#pillar-2-abstraction)
6. [Pillar 3: Inheritance](#pillar-3-inheritance)
7. [Pillar 4: Polymorphism](#pillar-4-polymorphism)

## PART 3: SOLID PRINCIPLES
8. [S: Single Responsibility](#s-single-responsibility-principle)
9. [O: Open/Closed](#o-openclosed-principle)
10. [L: Liskov Substitution](#l-liskov-substitution-principle)
11. [I: Interface Segregation](#i-interface-segregation-principle)
12. [D: Dependency Inversion](#d-dependency-inversion-principle)

## PART 4: DESIGN PATTERNS
13. [Creational Patterns](#creational-patterns)
14. [Structural Patterns](#structural-patterns)
15. [Behavioral Patterns](#behavioral-patterns)

## PART 5: ADVANCED TOPICS
16. [Access Modifiers](#access-modifiers)
17. [Static vs Instance](#static-vs-instance)
18. [Composition vs Inheritance](#composition-vs-inheritance)

## PART 6: INTERVIEW PREP
19. [Common Interview Questions](#common-interview-questions)
20. [LeetCode OOP Problems](#leetcode-oop-problems)
21. [Real-World Design Examples](#real-world-design-examples)

---

# WHAT IS OOP?

## Simple Definition:

**OOP = Way to organize code using "Objects" that represent real things**

```
Real World:
  CAR: Has properties (color, speed) and actions (drive, stop)
  
OOP:
  class Car:
    properties: color, speed
    actions: drive(), stop()
```

## Without OOP (Procedural):

```python
# Old way: Just functions
def drive():
    global speed
    speed += 10

def stop():
    global speed
    speed = 0

# Problem: Hard to manage, global variables, chaos!
```

## With OOP (Object-Oriented):

```python
# New way: Objects
class Car:
    def __init__(self, color):
        self.color = color
        self.speed = 0
    
    def drive(self):
        self.speed += 10
    
    def stop(self):
        self.speed = 0

car1 = Car("red")
car2 = Car("blue")
# Each car has its own speed, color, etc.
```

---

## Why is OOP Better?

```
Procedural (Messy):
  ┌─────────────────┐
  │ Global Variables│
  │ Tangled Logic   │
  │ Hard to maintain│
  └─────────────────┘

OOP (Organized):
  ┌────────────┐  ┌────────────┐  ┌────────────┐
  │   Car      │  │  Person    │  │   House    │
  │ (properties)  │ (properties)  │ (properties)
  │ (methods)  │  │ (methods)  │  │ (methods)  │
  └────────────┘  └────────────┘  └────────────┘
  
  Everything organized!
```

---

# WHY USE OOP?

## 4 Main Reasons:

### 1. MODULARITY ✅
```
Problem: 1 big file with 10,000 lines
Solution: Divide into 10 small classes, 1000 lines each
```

### 2. REUSABILITY ✅
```
Write once, use everywhere
class Dog:
  def bark(self): ...

dog1 = Dog()  # Use 1
dog2 = Dog()  # Use 2
dog3 = Dog()  # Use 3
```

### 3. MAINTAINABILITY ✅
```
Easy to change one class without affecting others
```

### 4. SCALABILITY ✅
```
Easy to add new features
Old code doesn't break
```

---

# CORE CONCEPTS

## 1. CLASS (Blueprint)

```python
# CLASS = Blueprint for creating objects
class Car:
    def __init__(self, brand, color):
        self.brand = brand      # Property
        self.color = color      # Property
        self.speed = 0
    
    def drive(self):            # Method
        self.speed += 10

# OBJECT = Instance of a class
car1 = Car("Toyota", "red")     # Create object from class
car2 = Car("Honda", "blue")     # Another object
```

### Visual:

```
CLASS (Blueprint):
┌─────────────────────┐
│  Car                │
│  ─────────────────  │
│  Properties:        │
│  - brand            │
│  - color            │
│  - speed            │
│  ─────────────────  │
│  Methods:           │
│  - drive()          │
│  - stop()           │
└─────────────────────┘
        ↓
OBJECTS (Instances):
    ┌──────────┐  ┌──────────┐
    │ car1     │  │ car2     │
    │ Toyota   │  │ Honda    │
    │ red      │  │ blue     │
    │ speed=0  │  │ speed=0  │
    └──────────┘  └──────────┘
```

---

## 2. ATTRIBUTES (Properties/Data)

```python
class Person:
    def __init__(self, name, age):
        self.name = name        # Attribute
        self.age = age          # Attribute

person = Person("John", 25)
print(person.name)              # Access attribute
```

---

## 3. METHODS (Functions inside class)

```python
class Person:
    def __init__(self, name):
        self.name = name
    
    def greet(self):            # Method
        return f"Hello, I'm {self.name}"

person = Person("John")
print(person.greet())           # Call method
```

---

## 4. CONSTRUCTOR (__init__)

```python
class Car:
    def __init__(self, brand, color):
        # Constructor runs automatically when object is created
        self.brand = brand
        self.color = color

car = Car("Toyota", "red")  # __init__ runs here automatically
```

---

# PILLAR 1: ENCAPSULATION

## What is it?

**Encapsulation = Hiding internal details, showing only what's needed**

```
Real World:
  CAR: You see buttons (accelerate, brake)
       You don't see engine internals
  
OOP:
  class Car:
    public: drive(), stop()      # Show these
    private: __calculate_fuel()  # Hide these
```

## Problem Without Encapsulation:

```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance

account = BankAccount(1000)
account.balance = -500  # PROBLEM! Negative balance allowed!
```

## Solution With Encapsulation:

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance    # Private (hidden)
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
    
    def withdraw(self, amount):
        if amount > 0 and amount <= self.__balance:
            self.__balance -= amount
    
    def get_balance(self):
        return self.__balance

account = BankAccount(1000)
account.deposit(500)              # Allowed
account.withdraw(2000)            # Not allowed (insufficient)
# account.__balance = -500         # Can't do this! Protected!
```

## Access Modifiers:

```python
class Example:
    def __init__(self):
        self.public = 1              # PUBLIC (anyone can access)
        self._protected = 2          # PROTECTED (convention only)
        self.__private = 3           # PRIVATE (hidden)
    
    def public_method(self):
        pass
    
    def _protected_method(self):
        pass
    
    def __private_method(self):
        pass
```

### Access Levels:

```
┌────────────────────────────────────────┐
│  PUBLIC (self.var)                     │
│  ├─ Access anywhere                    │
│  ├─ No protection                      │
│  └─ Use for: public API               │
├────────────────────────────────────────┤
│  PROTECTED (self._var)                 │
│  ├─ Convention (not enforced)         │
│  ├─ Accessible from child classes     │
│  └─ Use for: internal use             │
├────────────────────────────────────────┤
│  PRIVATE (self.__var)                  │
│  ├─ Truly hidden                       │
│  ├─ Not accessible from outside       │
│  └─ Use for: internal secrets         │
└────────────────────────────────────────┘
```

---

# PILLAR 2: ABSTRACTION

## What is it?

**Abstraction = Showing only the interface, hiding complexity**

```
Real World:
  TV: You press POWER button
      You don't care about circuits inside
  
OOP:
  class TV:
    def turn_on(self):           # Simple interface
        # Complex logic hidden
        ...
```

## Problem Without Abstraction:

```python
# User has to handle all complexity
class PaymentProcessor:
    def process(self, card_num, cvv, amount, address, country, ...):
        # User has to pass 100 things!
        pass
```

## Solution With Abstraction:

```python
class PaymentProcessor:
    def process_payment(self, amount):
        # Simple interface!
        self._validate_card()
        self._check_fraud()
        self._process()
        self._record_transaction()

processor = PaymentProcessor()
processor.process_payment(100)  # User just calls 1 method
```

## Using Abstract Classes:

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def make_sound(self):
        pass
    
    @abstractmethod
    def move(self):
        pass

class Dog(Animal):
    def make_sound(self):
        return "Woof!"
    
    def move(self):
        return "Running on 4 legs"

# dog = Animal()  # Error! Can't create abstract object
dog = Dog()       # OK! Concrete implementation
```

---

# PILLAR 3: INHERITANCE

## What is it?

**Inheritance = Child class inherits properties and methods from parent class**

```
Real World:
  ANIMAL (Parent)
  ├─ Dog (Child)     → Inherits "move", "eat" from Animal
  ├─ Cat (Child)     → Inherits "move", "eat" from Animal
  └─ Bird (Child)    → Inherits "move", "eat" from Animal

OOP:
  class Animal:
    def move(self): ...
    def eat(self): ...
  
  class Dog(Animal):  # Inherits from Animal
    pass
```

## Simple Example:

```python
# Parent class
class Animal:
    def __init__(self, name):
        self.name = name
    
    def move(self):
        return f"{self.name} is moving"

# Child class
class Dog(Animal):
    def bark(self):
        return f"{self.name} says: Woof!"

dog = Dog("Buddy")
print(dog.move())   # Inherited from Animal
print(dog.bark())   # Own method
```

## Inheritance Hierarchy:

```
        Animal (Parent)
        │
        ├─── Dog
        │     └─ Properties: bark()
        │
        ├─── Cat
        │     └─ Properties: meow()
        │
        └─── Bird
              └─ Properties: fly()
```

## Types of Inheritance:

### 1. SINGLE Inheritance

```python
class Vehicle:
    pass

class Car(Vehicle):     # Car inherits from Vehicle
    pass
```

### 2. MULTI-LEVEL Inheritance

```python
class Animal:
    pass

class Mammal(Animal):       # Mammal inherits from Animal
    pass

class Dog(Mammal):          # Dog inherits from Mammal
    pass
```

### 3. MULTIPLE Inheritance

```python
class Flyer:
    def fly(self): return "Flying"

class Swimmer:
    def swim(self): return "Swimming"

class Duck(Flyer, Swimmer):  # Duck inherits from both!
    pass

duck = Duck()
print(duck.fly())    # From Flyer
print(duck.swim())   # From Swimmer
```

### 4. HIERARCHICAL Inheritance

```python
class Animal:
    pass

class Dog(Animal):
    pass

class Cat(Animal):
    pass

class Lion(Animal):
    pass
```

---

# PILLAR 4: POLYMORPHISM

## What is it?

**Polymorphism = "Many forms" - Same method, different behavior**

```
Real World:
  Shape.draw() → Circle draws circle
                → Square draws square
                → Triangle draws triangle
  Same method, different results!

OOP:
  class Shape:
    def draw(self): ...  # General method
  
  class Circle(Shape):
    def draw(self):      # Draws circle
        ...
  
  class Square(Shape):
    def draw(self):      # Draws square
        ...
```

## Example: Method Overriding

```python
# Parent class
class Animal:
    def make_sound(self):
        return "Some sound"

# Child classes override the method
class Dog(Animal):
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def make_sound(self):
        return "Meow!"

class Bird(Animal):
    def make_sound(self):
        return "Tweet!"

# Polymorphism in action
animals = [Dog(), Cat(), Bird()]
for animal in animals:
    print(animal.make_sound())  # Each animal makes different sound!
```

### Output:
```
Woof!
Meow!
Tweet!
```

## Method Overloading (Simulated in Python)

```python
class Calculator:
    def add(self, *args):
        # Multiple "forms" of add method
        if len(args) == 2:
            return args[0] + args[1]
        elif len(args) == 3:
            return args[0] + args[1] + args[2]

calc = Calculator()
print(calc.add(2, 3))        # 5
print(calc.add(2, 3, 4))     # 9
```

## Duck Typing (Python Style Polymorphism)

```python
class Dog:
    def speak(self):
        return "Woof!"

class Person:
    def speak(self):
        return "Hello!"

def make_sound(obj):
    print(obj.speak())  # Works with any object that has speak()

make_sound(Dog())       # Woof!
make_sound(Person())    # Hello!
```

---

# S: SINGLE RESPONSIBILITY PRINCIPLE

## What is it?

**Each class should do ONE thing, and do it well**

### ❌ BAD (Multiple Responsibilities):

```python
class User:
    def __init__(self, name):
        self.name = name
    
    def save_to_database(self):
        # Responsibility 1: Saving data
        pass
    
    def send_email(self):
        # Responsibility 2: Sending email
        pass
    
    def generate_report(self):
        # Responsibility 3: Generating reports
        pass
    
    def delete_account(self):
        # Responsibility 4: Deleting account
        pass

# Problems:
# - Too many reasons to change
# - Hard to test
# - Hard to reuse
```

### ✅ GOOD (Single Responsibility):

```python
# Responsibility 1: User data
class User:
    def __init__(self, name):
        self.name = name

# Responsibility 2: Database operations
class UserRepository:
    def save(self, user):
        pass

# Responsibility 3: Email operations
class EmailService:
    def send_welcome_email(self, user):
        pass

# Responsibility 4: Report generation
class ReportGenerator:
    def generate_user_report(self, user):
        pass

# Now each class has ONE reason to change
```

---

# O: OPEN/CLOSED PRINCIPLE

## What is it?

**Classes should be OPEN for extension, CLOSED for modification**

### ❌ BAD (Have to modify existing code):

```python
class PaymentProcessor:
    def process(self, payment_type, amount):
        if payment_type == "credit_card":
            self._process_credit_card(amount)
        elif payment_type == "paypal":
            self._process_paypal(amount)
        elif payment_type == "bitcoin":
            self._process_bitcoin(amount)
        
        # If we add new payment type, we modify this class!

# Problem: Every new payment type requires modifying existing code
```

### ✅ GOOD (Extend without modifying):

```python
from abc import ABC, abstractmethod

# Base class
class PaymentMethod(ABC):
    @abstractmethod
    def process(self, amount):
        pass

# Extensions for different payment types
class CreditCardPayment(PaymentMethod):
    def process(self, amount):
        return f"Processing ${amount} via Credit Card"

class PayPalPayment(PaymentMethod):
    def process(self, amount):
        return f"Processing ${amount} via PayPal"

class BitcoinPayment(PaymentMethod):
    def process(self, amount):
        return f"Processing ${amount} via Bitcoin"

# New payment types added WITHOUT modifying existing code!
class ApplePayPayment(PaymentMethod):
    def process(self, amount):
        return f"Processing ${amount} via Apple Pay"

# Processor uses abstraction
class PaymentProcessor:
    def process(self, payment_method: PaymentMethod, amount):
        return payment_method.process(amount)

# Usage
processor = PaymentProcessor()
processor.process(CreditCardPayment(), 100)  # Works
processor.process(ApplePayPayment(), 50)     # Works without changing PaymentProcessor!
```

---

# L: LISKOV SUBSTITUTION PRINCIPLE

## What is it?

**Objects of child class should be replaceable with parent class objects**

### ❌ BAD (Can't substitute):

```python
class Bird:
    def fly(self):
        return "Flying"

class Penguin(Bird):
    def fly(self):
        return "Can't fly!"  # Problem! Penguin is not a proper Bird

# Using penguin like a bird breaks things
def make_bird_fly(bird: Bird):
    print(bird.fly())

make_bird_fly(Penguin())  # Returns "Can't fly!" - breaks expectations!
```

### ✅ GOOD (Can substitute):

```python
class Bird:
    def move(self):
        pass

class FlyingBird(Bird):
    def move(self):
        return "Flying"

class SwimmingBird(Bird):
    def move(self):
        return "Swimming"

class Penguin(SwimmingBird):
    def move(self):
        return "Swimming"

# Now we can use any Bird substitute properly
def animal_moves(bird: Bird):
    print(bird.move())

animal_moves(FlyingBird())   # "Flying" - works!
animal_moves(Penguin())      # "Swimming" - works!
```

---

# I: INTERFACE SEGREGATION PRINCIPLE

## What is it?

**Don't force classes to implement methods they don't need**

### ❌ BAD (Fat interface):

```python
from abc import ABC, abstractmethod

class Worker(ABC):
    @abstractmethod
    def work(self):
        pass
    
    @abstractmethod
    def eat(self):
        pass
    
    @abstractmethod
    def sleep(self):
        pass

class Robot(Worker):
    def work(self):
        return "Working"
    
    def eat(self):
        return "Can't eat!"  # Forced to implement!
    
    def sleep(self):
        return "Can't sleep!"  # Forced to implement!
```

### ✅ GOOD (Segregated interfaces):

```python
from abc import ABC, abstractmethod

# Segregated interfaces
class Workable(ABC):
    @abstractmethod
    def work(self):
        pass

class Eatable(ABC):
    @abstractmethod
    def eat(self):
        pass

class Sleepable(ABC):
    @abstractmethod
    def sleep(self):
        pass

# Robot only implements what it needs
class Robot(Workable):
    def work(self):
        return "Working"

# Human implements everything
class Human(Workable, Eatable, Sleepable):
    def work(self):
        return "Working"
    
    def eat(self):
        return "Eating"
    
    def sleep(self):
        return "Sleeping"
```

---

# D: DEPENDENCY INVERSION PRINCIPLE

## What is it?

**Depend on abstractions, not concrete classes**

### ❌ BAD (Tightly coupled):

```python
class MySQLDatabase:
    def save(self, data):
        print(f"Saving to MySQL: {data}")

class UserService:
    def __init__(self):
        self.db = MySQLDatabase()  # Tightly coupled!
    
    def save_user(self, user):
        self.db.save(user)

# Problem: Can't switch to MongoDB without changing UserService!
```

### ✅ GOOD (Loosely coupled):

```python
from abc import ABC, abstractmethod

# Abstraction
class Database(ABC):
    @abstractmethod
    def save(self, data):
        pass

# Concrete implementations
class MySQLDatabase(Database):
    def save(self, data):
        print(f"Saving to MySQL: {data}")

class MongoDatabase(Database):
    def save(self, data):
        print(f"Saving to MongoDB: {data}")

# Service depends on abstraction
class UserService:
    def __init__(self, db: Database):  # Inject dependency
        self.db = db
    
    def save_user(self, user):
        self.db.save(user)

# Easy to switch databases!
mysql_service = UserService(MySQLDatabase())
mongo_service = UserService(MongoDatabase())
```

---

# CREATIONAL PATTERNS

## 1. SINGLETON PATTERN

**Ensures only ONE instance of a class exists**

```python
class Database:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance

db1 = Database()
db2 = Database()
print(db1 is db2)  # True! Same instance
```

## 2. FACTORY PATTERN

**Creates objects without specifying exact classes**

```python
class PaymentMethod:
    pass

class CreditCard(PaymentMethod):
    pass

class PayPal(PaymentMethod):
    pass

class PaymentFactory:
    @staticmethod
    def create(payment_type):
        if payment_type == "card":
            return CreditCard()
        elif payment_type == "paypal":
            return PayPal()

# Use factory
payment = PaymentFactory.create("card")
```

## 3. BUILDER PATTERN

**Builds complex objects step by step**

```python
class House:
    def __init__(self):
        self.rooms = 0
        self.bathrooms = 0
        self.garage = False
    
    def __str__(self):
        return f"House({self.rooms}rooms, {self.bathrooms}baths, garage={self.garage})"

class HouseBuilder:
    def __init__(self):
        self.house = House()
    
    def add_rooms(self, num):
        self.house.rooms = num
        return self
    
    def add_bathrooms(self, num):
        self.house.bathrooms = num
        return self
    
    def add_garage(self):
        self.house.garage = True
        return self
    
    def build(self):
        return self.house

# Build step by step
house = HouseBuilder()\
    .add_rooms(4)\
    .add_bathrooms(2)\
    .add_garage()\
    .build()

print(house)  # House(4rooms, 2baths, garage=True)
```

---

# STRUCTURAL PATTERNS

## 1. ADAPTER PATTERN

**Converts interface of one class to another**

```python
# Old interface
class OldPaymentProcessor:
    def make_payment(self, amount):
        return f"Old payment: ${amount}"

# New expected interface
class NewPaymentProcessor:
    def process_payment(self, amount):
        pass

# Adapter
class PaymentAdapter(NewPaymentProcessor):
    def __init__(self, old_processor):
        self.old = old_processor
    
    def process_payment(self, amount):
        return self.old.make_payment(amount)

# Use adapter
old = OldPaymentProcessor()
adapter = PaymentAdapter(old)
print(adapter.process_payment(100))  # Works!
```

## 2. DECORATOR PATTERN

**Adds behavior to objects dynamically**

```python
class Coffee:
    def cost(self):
        return 5

class CoffeeWithMilk:
    def __init__(self, coffee):
        self.coffee = coffee
    
    def cost(self):
        return self.coffee.cost() + 2

class CoffeeWithSugar:
    def __init__(self, coffee):
        self.coffee = coffee
    
    def cost(self):
        return self.coffee.cost() + 1

# Decorate step by step
coffee = Coffee()
coffee = CoffeeWithMilk(coffee)
coffee = CoffeeWithSugar(coffee)
print(coffee.cost())  # 5 + 2 + 1 = 8
```

## 3. FACADE PATTERN

**Provides simplified interface to complex subsystems**

```python
# Complex subsystem
class Engine:
    def start(self):
        return "Engine started"

class Transmission:
    def shift_gear(self):
        return "Gear shifted"

class FuelPump:
    def pump(self):
        return "Fuel pumped"

# Facade
class Car:
    def __init__(self):
        self.engine = Engine()
        self.transmission = Transmission()
        self.fuel = FuelPump()
    
    def start(self):
        # Hides complexity
        self.fuel.pump()
        self.engine.start()
        self.transmission.shift_gear()
        return "Car started!"

# User just calls start()
car = Car()
print(car.start())  # Simple interface!
```

---

# BEHAVIORAL PATTERNS

## 1. OBSERVER PATTERN

**Objects notify multiple observers about state changes**

```python
class Subject:
    def __init__(self):
        self.observers = []
    
    def attach(self, observer):
        self.observers.append(observer)
    
    def notify(self, message):
        for observer in self.observers:
            observer.update(message)

class Observer:
    def update(self, message):
        pass

class EmailObserver(Observer):
    def update(self, message):
        print(f"Email: {message}")

class SMSObserver(Observer):
    def update(self, message):
        print(f"SMS: {message}")

# Usage
subject = Subject()
subject.attach(EmailObserver())
subject.attach(SMSObserver())
subject.notify("New update!")  # All observers notified
```

## 2. STRATEGY PATTERN

**Encapsulates different algorithms**

```python
class PaymentStrategy:
    def pay(self, amount):
        pass

class CreditCardPayment(PaymentStrategy):
    def pay(self, amount):
        return f"Paid ${amount} with credit card"

class PayPalPayment(PaymentStrategy):
    def pay(self, amount):
        return f"Paid ${amount} with PayPal"

class ShoppingCart:
    def __init__(self, strategy: PaymentStrategy):
        self.strategy = strategy
    
    def checkout(self, amount):
        return self.strategy.pay(amount)

# Use different strategies
cart1 = ShoppingCart(CreditCardPayment())
cart2 = ShoppingCart(PayPalPayment())
```

## 3. STATE PATTERN

**Object behavior changes based on state**

```python
class State:
    def handle(self):
        pass

class HappyState(State):
    def handle(self):
        return "Smiling"

class SadState(State):
    def handle(self):
        return "Crying"

class Person:
    def __init__(self):
        self.state = HappyState()
    
    def change_state(self, state: State):
        self.state = state
    
    def act(self):
        return self.state.handle()

# Usage
person = Person()
print(person.act())  # "Smiling"
person.change_state(SadState())
print(person.act())  # "Crying"
```

---

# ACCESS MODIFIERS

## Public, Protected, Private

```python
class BankAccount:
    def __init__(self, balance):
        self.public_balance = balance              # PUBLIC
        self._protected_transactions = []          # PROTECTED
        self.__private_pin = "1234"                # PRIVATE
    
    def public_method(self):
        """Anyone can call"""
        pass
    
    def _protected_method(self):
        """Hint: use inside class and subclasses"""
        pass
    
    def __private_method(self):
        """Only this class"""
        pass

# Access levels
account = BankAccount(1000)

account.public_balance = 500            # ✅ OK
account._protected_transactions.append("payment")  # ⚠️ Can do but shouldn't
# account.__private_pin = "5678"        # ❌ Error! Can't access
```

---

# STATIC VS INSTANCE

## Instance Members (Per object)

```python
class Car:
    def __init__(self, color):
        self.color = color      # Instance variable
                                # Each car has its own color
    
    def describe(self):         # Instance method
        return self.color

car1 = Car("red")
car2 = Car("blue")
print(car1.describe())  # "red"
print(car2.describe())  # "blue" (different)
```

## Static Members (Shared by all)

```python
class Car:
    wheels = 4              # Static variable (shared)
    
    @staticmethod
    def honk():             # Static method
        return "Honk!"
    
    @classmethod
    def create_bike(cls):   # Class method
        return "Created bike"

print(Car.wheels)           # 4
print(Car.honk())           # "Honk!"
print(Car.create_bike())    # "Created bike"
```

---

# COMPOSITION VS INHERITANCE

## INHERITANCE (IS-A)

```
Use when: "Is a" relationship
Example: Dog IS-A Animal

class Animal:
    def move(self): ...

class Dog(Animal):  # Dog IS-A Animal
    pass
```

### ✅ Good for:
```
- Natural hierarchies
- Code reuse
- Behavioral inheritance
```

### ❌ Problems:
```
- Tight coupling
- Inflexible
- Deep hierarchies cause problems
```

## COMPOSITION (HAS-A)

```
Use when: "Has a" relationship
Example: Car HAS-A Engine

class Engine:
    def run(self): ...

class Car:
    def __init__(self):
        self.engine = Engine()  # Car HAS-A Engine
```

### ✅ Good for:
```
- Flexibility
- Loose coupling
- Easy to change behavior
```

### ❌ Problems:
```
- More code
- Less intuitive
```

## Comparison:

```python
# ❌ BAD: Inheritance creates problems
class Animal:
    def move(self): return "Moving"
    def eat(self): return "Eating"

class Car(Animal):  # Car IS-A Animal? NO!
    pass

# ✅ GOOD: Composition is flexible
class Engine:
    def run(self): return "Engine running"

class Car:
    def __init__(self):
        self.engine = Engine()  # Car HAS-A Engine
    
    def start(self):
        return self.engine.run()
```

---

# COMMON INTERVIEW QUESTIONS

## Q1: What are the four pillars of OOP?

**Answer:**
```
1. Encapsulation - Hide internal details
2. Abstraction - Show only interface
3. Inheritance - Reuse code
4. Polymorphism - Same method, different behavior
```

---

## Q2: Explain SOLID principles

**Answer:**
```
S - Single Responsibility: One class, one job
O - Open/Closed: Open for extension, closed for modification
L - Liskov Substitution: Child replaces parent properly
I - Interface Segregation: Don't force unused methods
D - Dependency Inversion: Depend on abstractions, not concrete
```

---

## Q3: What's the difference between abstract class and interface?

**Answer:**
```
Abstract Class:
  - Can have implemented methods
  - Can have state (variables)
  - Can have private members
  
Interface:
  - Only method declarations (abstract)
  - No state
  - All public
```

---

## Q4: Explain encapsulation with an example

**Answer:**
```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance    # Private
    
    def withdraw(self, amount):
        if amount <= self.__balance:
            self.__balance -= amount
    
    def get_balance(self):
        return self.__balance

# User can't access __balance directly
# But can use public methods
account = BankAccount(1000)
account.withdraw(100)
print(account.get_balance())  # 900
```

---

## Q5: What is polymorphism?

**Answer:**
```python
# Same method, different behavior
class Shape:
    def area(self): pass

class Circle(Shape):
    def area(self):
        return 3.14 * self.radius ** 2

class Square(Shape):
    def area(self):
        return self.side ** 2

# Same method name, different results
```

---

## Q6: Composition vs Inheritance - when to use which?

**Answer:**
```
Use INHERITANCE when:
  - Clear IS-A relationship
  - Code reuse is primary goal
  - Behavior is inherited
  
Use COMPOSITION when:
  - HAS-A relationship
  - Flexibility needed
  - Avoiding rigid hierarchies
  
Rule of thumb: Prefer composition!
```

---

## Q7: What are design patterns?

**Answer:**
```
Reusable solutions to common problems

Categories:
1. Creational - Object creation (Singleton, Factory, Builder)
2. Structural - Object composition (Adapter, Decorator, Facade)
3. Behavioral - Object interaction (Observer, Strategy, State)
```

---

# LEETCODE OOP PROBLEMS

## Problem 1: LRU Cache (Medium)

```python
from collections import OrderedDict

class LRUCache:
    def __init__(self, capacity):
        self.cache = OrderedDict()
        self.capacity = capacity
    
    def get(self, key):
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]
    
    def put(self, key, value):
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)
```

---

## Problem 2: Design HashMap (Easy)

```python
class MyHashMap:
    def __init__(self):
        self.map = {}
    
    def put(self, key, value):
        self.map[key] = value
    
    def get(self, key):
        return self.map.get(key, -1)
    
    def remove(self, key):
        if key in self.map:
            del self.map[key]
```

---

## Problem 3: Design Parking Lot (Hard)

```python
class ParkingLot:
    def __init__(self, levels, spots_per_level):
        self.levels = levels
        self.spots = [[True] * spots_per_level for _ in range(levels)]
    
    def park_vehicle(self):
        for level in range(self.levels):
            for spot in range(len(self.spots[level])):
                if self.spots[level][spot]:
                    self.spots[level][spot] = False
                    return (level, spot)
        return None
    
    def unpark_vehicle(self, level, spot):
        self.spots[level][spot] = True
```

---

# REAL-WORLD DESIGN EXAMPLES

## Example 1: E-Commerce System

```python
from abc import ABC, abstractmethod
from enum import Enum

class OrderStatus(Enum):
    PENDING = 1
    PROCESSING = 2
    SHIPPED = 3
    DELIVERED = 4

class Product:
    def __init__(self, id, name, price):
        self.id = id
        self.name = name
        self.price = price

class ShoppingCart:
    def __init__(self):
        self.items = []
    
    def add_item(self, product, quantity):
        self.items.append((product, quantity))
    
    def get_total(self):
        return sum(p.price * q for p, q in self.items)

class Order:
    def __init__(self, order_id, cart):
        self.order_id = order_id
        self.items = cart.items
        self.status = OrderStatus.PENDING
        self.total = cart.get_total()
    
    def process(self):
        self.status = OrderStatus.PROCESSING

class PaymentMethod(ABC):
    @abstractmethod
    def pay(self, amount):
        pass

class CreditCardPayment(PaymentMethod):
    def pay(self, amount):
        return f"Paid ${amount} with credit card"

class PaymentProcessor:
    def process_payment(self, order, payment_method):
        payment_method.pay(order.total)
        order.process()

# Usage
product = Product(1, "Laptop", 999)
cart = ShoppingCart()
cart.add_item(product, 1)
order = Order(1001, cart)
processor = PaymentProcessor()
processor.process_payment(order, CreditCardPayment())
```

---

## Example 2: Notification System

```python
from abc import ABC, abstractmethod

class Notification(ABC):
    @abstractmethod
    def send(self, message):
        pass

class EmailNotification(Notification):
    def send(self, message):
        print(f"Email: {message}")

class SMSNotification(Notification):
    def send(self, message):
        print(f"SMS: {message}")

class NotificationManager:
    def __init__(self):
        self.notifications = []
    
    def add_notification(self, notification):
        self.notifications.append(notification)
    
    def send_all(self, message):
        for notification in self.notifications:
            notification.send(message)

# Usage
manager = NotificationManager()
manager.add_notification(EmailNotification())
manager.add_notification(SMSNotification())
manager.send_all("Welcome!")
```

---

# MEMORY TECHNIQUES FOR OOP

## Technique 1: THE FOUR PILLARS

Remember with: **E-A-I-P**

```
E = Encapsulation (Hide details)
A = Abstraction (Show interface)
I = Inheritance (Reuse code)
P = Polymorphism (Same method, different behavior)
```

---

## Technique 2: SOLID ACRONYM

Remember: **SOLID**

```
S = Single Responsibility
O = Open/Closed
L = Liskov Substitution
I = Interface Segregation
D = Dependency Inversion
```

---

## Technique 3: DESIGN PATTERNS

Remember by category:

```
CREATIONAL:
  - Singleton (only 1)
  - Factory (create)
  - Builder (build step by step)

STRUCTURAL:
  - Adapter (convert)
  - Decorator (add behavior)
  - Facade (simplify)

BEHAVIORAL:
  - Observer (notify)
  - Strategy (different algorithms)
  - State (change behavior)
```

---

## Technique 4: VISUALIZE OOP

```
Real World → OOP Mapping

CAR (Real thing)
├─ Properties (Color, Speed)
├─ Methods (Drive, Stop, Park)

CLASS Car (In code)
├─ Attributes (self.color, self.speed)
├─ Methods (self.drive(), self.stop())

OBJECT car1 = Car() (Instance)
```

---

# PRACTICE STRATEGY

## Week 1: Learn Fundamentals

```
Day 1: Classes, Objects, Attributes
Day 2: Methods, Constructors
Day 3: Encapsulation
Day 4: Abstraction
Day 5: Inheritance
Day 6: Polymorphism
Day 7: Review & Quiz
```

---

## Week 2: Learn SOLID

```
Day 1: Single Responsibility
Day 2: Open/Closed
Day 3: Liskov Substitution
Day 4: Interface Segregation
Day 5: Dependency Inversion
Day 6: Real-world examples
Day 7: Practice coding
```

---

## Week 3: Learn Design Patterns

```
Day 1-2: Creational (Singleton, Factory, Builder)
Day 3-4: Structural (Adapter, Decorator, Facade)
Day 5-6: Behavioral (Observer, Strategy, State)
Day 7: Practice problems
```

---

## Week 4: LeetCode Practice

```
Day 1-2: Design HashMap (Easy)
Day 3-4: LRU Cache (Medium)
Day 5-6: Design Parking Lot (Hard)
Day 7: Design File System (Hard)
```

---

# SUMMARY CHECKLIST

## Do You Understand?

```
Fundamentals:
☐ What is OOP
☐ Class vs Object
☐ Attributes vs Methods
☐ Constructor

Four Pillars:
☐ Encapsulation (hiding)
☐ Abstraction (interface)
☐ Inheritance (reuse)
☐ Polymorphism (same method, different behavior)

SOLID Principles:
☐ Single Responsibility
☐ Open/Closed
☐ Liskov Substitution
☐ Interface Segregation
☐ Dependency Inversion

Design Patterns:
☐ Singleton
☐ Factory
☐ Builder
☐ Adapter
☐ Decorator
☐ Facade
☐ Observer
☐ Strategy
☐ State

Advanced:
☐ Access Modifiers (public, protected, private)
☐ Static vs Instance
☐ Composition vs Inheritance
☐ Abstract classes vs Interfaces
```

If you checked all boxes, you're ready for interviews! 🎉

---

## Made with ❤️ for Interview Success
## Awais Amjad BSCS @ UET Python Developer
