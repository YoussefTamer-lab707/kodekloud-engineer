---
title: Java OOP Questions and Answers
tags:
 - java
 - oop
 - programming
description: 30 Java Object-Oriented Programming questions and answers for all levels.
---

# Java OOP Questions and Answers

This page contains 30 coding-related questions and answers about Java Object-Oriented Programming, ranging from beginner to advanced levels.

## Beginner Level

### 1. Create a simple Class and Object
**Question:** Define a class named `Car` with a field `model` and a method `display()`. Create an object of this class and call the method.

**Answer:**
```java
class Car {
    String model;

    void display() {
        System.out.println("Car model: " + model);
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.model = "Tesla Model 3";
        myCar.display();
    }
}
```

### 2. Constructor Implementation
**Question:** How do you use a constructor to initialize an object's state?

**Answer:**
```java
class Book {
    String title;

    Book(String t) {
        title = t;
    }

    void showTitle() {
        System.out.println("Book Title: " + title);
    }
}

public class Main {
    public static void main(String[] args) {
        Book b = new Book("Effective Java");
        b.showTitle();
    }
}
```

### 3. Encapsulation using Private Fields
**Question:** Implement encapsulation by making fields private and providing public getters and setters.

**Answer:**
```java
class Person {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        Person p = new Person();
        p.setName("John");
        System.out.println(p.getName());
    }
}
```

### 4. Basic Inheritance
**Question:** Create a base class `Animal` and a derived class `Dog` that inherits from it.

**Answer:**
```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();
        d.bark();
    }
}
```

### 5. Method Overloading
**Question:** Demonstrate method overloading by creating multiple `add` methods with different parameters.

**Answer:**
```java
class MathUtils {
    int add(int a, int b) {
        return a + b;
    }
    int add(int a, int b, int c) {
        return a + b + c;
    }
}

public class Main {
    public static void main(String[] args) {
        MathUtils mu = new MathUtils();
        System.out.println(mu.add(5, 10));
        System.out.println(mu.add(5, 10, 15));
    }
}
```

### 6. Method Overriding
**Question:** Override a method `sound()` in a subclass.

**Answer:**
```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Meow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myCat = new Cat();
        myCat.sound();
    }
}
```

### 7. The `this` Keyword
**Question:** Use the `this` keyword to resolve ambiguity between instance variables and parameters.

**Answer:**
```java
class Employee {
    String name;
    Employee(String name) {
        this.name = name;
    }
}
```

### 8. The `static` Keyword
**Question:** How do you use a static variable to count the number of objects created?

**Answer:**
```java
class Counter {
    static int count = 0;
    Counter() {
        count++;
    }
}

public class Main {
    public static void main(String[] args) {
        new Counter();
        new Counter();
        System.out.println(Counter.count); // Output: 2
    }
}
```

### 9. Default Constructor vs Parameterized Constructor
**Question:** Can a class have both? Show an example.

**Answer:**
```java
class Laptop {
    String brand;
    Laptop() { brand = "Unknown"; }
    Laptop(String b) { brand = b; }
}
```

### 10. Access Modifiers (Protected)
**Question:** Show how a `protected` member is accessible in a subclass.

**Answer:**
```java
class Parent {
    protected String familyName = "Smith";
}
class Child extends Parent {
    void display() {
        System.out.println(familyName);
    }
}
```

## Intermediate Level

### 11. Abstract Class
**Question:** Create an abstract class `Shape` with an abstract method `draw()`.

**Answer:**
```java
abstract class Shape {
    abstract void draw();
}

class Circle extends Shape {
    void draw() { System.out.println("Drawing Circle"); }
}
```

### 12. Interface implementation
**Question:** Define an interface `Playable` and implement it in `VideoPlayer`.

**Answer:**
```java
interface Playable {
    void play();
}

class VideoPlayer implements Playable {
    public void play() { System.out.println("Playing video..."); }
}
```

### 13. Multiple Interfaces
**Question:** How does Java support multiple inheritance via interfaces?

**Answer:**
```java
interface Printable { void print(); }
interface Showable { void show(); }

class Document implements Printable, Showable {
    public void print() { System.out.println("Printing"); }
    public void show() { System.out.println("Showing"); }
}
```

### 14. The `super` keyword (Method)
**Question:** Use `super` to call a parent class method that has been overridden.

**Answer:**
```java
class Parent {
    void message() { System.out.println("Parent message"); }
}
class Child extends Parent {
    void message() {
        super.message();
        System.out.println("Child message");
    }
}
```

### 15. The `super` keyword (Constructor)
**Question:** Use `super()` to call a parent class constructor.

**Answer:**
```java
class Person {
    Person(String name) { System.out.println("Name: " + name); }
}
class Student extends Person {
    Student(String name) {
        super(name);
    }
}
```

### 16. The `final` Keyword (Variable)
**Question:** What happens if you try to change a `final` variable?

**Answer:**
```java
class Test {
    final int LIMIT = 100;
    void change() {
        // LIMIT = 200; // Compile-time error
    }
}
```

### 17. The `final` Keyword (Method and Class)
**Question:** Prevent overriding and inheritance using `final`.

**Answer:**
```java
final class Immutable { }
// class Sub extends Immutable { } // Error

class Base {
    final void secure() { }
}
```

### 18. Polymorphism (Upcasting)
**Question:** Demonstrate Upcasting in Java.

**Answer:**
```java
class Bank { float getRate() { return 0; } }
class SBI extends Bank { float getRate() { return 8.4f; } }

Bank b = new SBI(); // Upcasting
System.out.println(b.getRate());
```

### 19. Composition
**Question:** Demonstrate Composition (Has-A relationship).

**Answer:**
```java
class Engine { }
class Car {
    private final Engine engine;
    Car() { this.engine = new Engine(); }
}
```

### 20. Inner Class
**Question:** Create a simple inner class.

**Answer:**
```java
class Outer {
    class Inner {
        void msg() { System.out.println("Inside inner class"); }
    }
}
```

## Advanced Level

### 21. Dynamic Method Dispatch
**Question:** Explain Dynamic Method Dispatch with a code snippet.

**Answer:**
```java
class A { void m1() { System.out.println("Inside A"); } }
class B extends A { void m1() { System.out.println("Inside B"); } }

A a = new B();
a.m1(); // Output: Inside B (decided at runtime)
```

### 22. Interface with Default Methods
**Question:** How do default methods help in interfaces?

**Answer:**
```java
interface MyInterface {
    void existingMethod();
    default void newMethod() {
        System.out.println("New default method");
    }
}
```

### 23. Interface with Static Methods
**Question:** Can interfaces have static methods?

**Answer:**
```java
interface Utils {
    static int cube(int x) { return x * x * x; }
}
```

### 24. Covariant Return Type
**Question:** Demonstrate covariant return types in overriding.

**Answer:**
```java
class A {
    A get() { return this; }
}
class B extends A {
    @Override
    B get() { return this; } // Covariant return type
}
```

### 25. The `instanceof` Operator
**Question:** Use `instanceof` to check object type.

**Answer:**
```java
Animal a = new Dog();
if (a instanceof Dog) {
    System.out.println("It's a dog");
}
```

### 26. Aggregation vs Composition
**Question:** Show a code-level distinction of Aggregation.

**Answer:**
```java
class Address { }
class Student {
    Address address; // Student has an address (Aggregation)
    Student(Address addr) { this.address = addr; }
}
```

### 27. Singleton Pattern
**Question:** Implement a simple thread-safe Singleton.

**Answer:**
```java
class Singleton {
    private static Singleton instance;
    private Singleton() {}
    public static synchronized Singleton getInstance() {
        if (instance == null) instance = new Singleton();
        return instance;
    }
}
```

### 28. Anonymous Inner Class
**Question:** Use an anonymous inner class to implement an interface.

**Answer:**
```java
interface Greet { void sayHi(); }
Greet g = new Greet() {
    public void sayHi() { System.out.println("Hello!"); }
};
```

### 29. Deep Copy vs Shallow Copy
**Question:** Briefly explain the difference in a constructor.

**Answer:**
```java
// Shallow Copy
this.data = original.data;

// Deep Copy
this.data = new Data(original.data);
```

### 30. SOLID Principles (Dependency Inversion)
**Question:** Show a simple example of Dependency Inversion.

**Answer:**
```java
interface Keyboard { }
class StandardKeyboard implements Keyboard { }

class Computer {
    private final Keyboard keyboard;
    // Dependency is injected, not hardcoded
    Computer(Keyboard k) { this.keyboard = k; }
}
```
