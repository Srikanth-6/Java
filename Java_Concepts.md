# Java and OOPS

## Basic Java

- Mutable Vs Immutable Objects
- Static Key word significance
- Abstract key work, abstract class, abstract method

## OOPS

### Encapsulation

- Encapsulation (Bundling data (fields) and methods together, and restricting direct access to data using access modifiers.)

### Inheritance

- Inheritance [**extends parent class**] (Mechanism where one class (child) acquires properties and behaviors of another class (parent))
- Inheritance vs. Accessibility

| Modifier              | Inherited? | Accessible in Subclass?                                             |
| --------------------- | ---------- | ------------------------------------------------------------------- |
| public                | Yes        | Always                                                              |
| protected             | Yes        | Always (even if the subclass is in a different package)             |
| Default (no modifier) | Yes        | Only if the subclass is in the same package                         |
| private               | No\*       | Never. The member exists in memory, but the subclass cannot see it. |

- A(Parent), B(Subclass) = B extends A
- Static members are inherited
- A subclass does not inherit the parent’s constructor. It must define its own, though it usually calls the parent's constructor using super().
- Subclass will inherit the parent methods but can override the methods.
- This is a common point of confusion. Static members are inherited, but they are not "overridden" in the traditional sense. it hides the one in Class A rather than overriding it.

### Polymorphism

"One interface, many implementations" → Same method name, different behaviors

**Compile-time Polymorphism (Method Overloading):**

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

**Runtime Polymorphism (Method Overriding):**

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Bark");
    }
}

// Usage
Animal a = new Dog(); // Upcasting
a.sound(); // Output: Bark (runtime decision)
```

- Compile time polymorphism - means compiler will know at the time of compilation it self how to resolve the ambuguity.
- Run time polymorphism - means system doesnot know how to resolve the ambuguity until unless it sees the execution flow or during run time

### Abstraction

Hiding implementation details and showing only essential features to the user.

**Abstract Class vs. Interface:**

| Feature     | Abstract Class                               | Interface                                           |
| ----------- | -------------------------------------------- | --------------------------------------------------- |
| Inheritance | A class can extend only one abstract class.  | A class can implement many interfaces.              |
| State       | Can have instance variables (fields).        | Can only have constants (static final).             |
| Methods     | Can have both abstract and concrete methods. | Mostly abstract (though default methods exist now). |
| Purpose     | "Is-a" relationship (An Apple is a Fruit).   | "Can-do" relationship (A Plane can Fly).            |

- A class can be declared abstract even if it has zero abstract methods. However, if a class has at least one abstract method, it must be declared abstract.
- abstract class/ interface cannot be instatiated.

**Class Types Summary:**

| Class Type     | Can have abstract methods? | Can be instantiated (new)? | Must have abstract methods? |
| -------------- | -------------------------- | -------------------------- | --------------------------- |
| Regular Class  | No                         | Yes                        | No                          |
| Abstract Class | Yes                        | No                         | No                          |
| Interface      | Yes                        | No                         | No (can have default)       |

#### Interfaces vs Abstract Classes

- Both provide abstraction but differ in purpose and flexibility.
- Interface: Contract (pure abstraction), Abstract Class: Partial implementation (shared code)

#### Abstraction vs Inheritance

- Inheritance - Use it for: "IS-A" Relationships.
- Abstraction - Use it for: "PARTIALLY DEFINED" Objects.
- Interface - Use it for: "CAN-DO" / "CONTRACT" Relationships.
