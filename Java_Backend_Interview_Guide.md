# ☕ Java Backend Interview Guide

A **complete structured guide** for mastering **Java for Backend Engineering Interviews**.

Designed for:

* Backend Engineers
* SDE I / SDE II Interview Preparation
* Java Developers
* System Design + Concurrency heavy roles

---

# 📚 Study Roadmap

Recommended learning order:

```
1. Core Java Fundamentals
2. Object-Oriented Programming
3. Java Memory Model & JVM
4. Java Collections Framework
5. Exception Handling
6. Generics
7. Multithreading & Concurrency
8. Concurrent Collections
9. Java 8+ Features
10. Modern Java (Java 17+)
11. Common Interview Problems
```

---

# 1️⃣ Core Java Fundamentals

## Java Execution Flow

```
Java Source Code (.java)
        ↓
Java Compiler (javac)
        ↓
Bytecode (.class)
        ↓
JVM
        ↓
Machine Code
```

---

## JVM Components

```
ClassLoader
Runtime Data Areas
Execution Engine
Garbage Collector
```

### Runtime Data Areas

```
Heap
Stack
Method Area (Metaspace)
PC Register
Native Method Stack
```

---

# 2️⃣ Object-Oriented Programming (OOPS)

## Encapsulation

Bundling data and methods together while restricting access using **access modifiers**.

```
private
default
protected
public
```

---

## Inheritance

```
class A {}
class B extends A {}
```

Child class inherits:

* fields
* methods

But **constructors are not inherited**.

---

### Access Modifiers in Inheritance

| Modifier  | Inherited | Accessible                    |
| --------- | --------- | ----------------------------- |
| public    | Yes       | Everywhere                    |
| protected | Yes       | Subclass even across packages |
| default   | Yes       | Same package only             |
| private   | No        | Not accessible                |

---

## Polymorphism

### Compile-time (Method Overloading)

```
int add(int a, int b)
double add(double a, double b)
```

Resolved **at compile time**.

---

### Runtime (Method Overriding)

```
class Animal {
    void sound() {}
}

class Dog extends Animal {
    void sound() {}
}
```

Resolved **during runtime**.

---

## Abstraction

Hiding implementation details while exposing only essential behavior.

### Abstract Class

```
abstract class Vehicle {
    abstract void start();
}
```

Features:

* can have state
* can have concrete methods

---

### Interface

```
interface Flyable {
    void fly();
}
```

Features:

* contract-based design
* multiple implementations allowed

---

### Abstract Class vs Interface

| Feature     | Abstract Class        | Interface       |
| ----------- | --------------------- | --------------- |
| Inheritance | Single                | Multiple        |
| Fields      | Allowed               | Constants only  |
| Methods     | Abstract + concrete   | Mostly abstract |
| Purpose     | Shared implementation | Contract        |

---

# 3️⃣ Important Java Keywords

## Static

Belongs to **class level**, not object.

Examples:

```
static variable
static method
static block
```

Use cases:

* shared resources
* utility methods

---

## Final

```
final variable
final method
final class
```

Examples:

```
final int x = 10
final class MathUtils
```

Effects:

```
variable → cannot change
method → cannot override
class → cannot extend
```

---

# 4️⃣ Mutable vs Immutable Objects

## Mutable

State can change.

Example:

```
ArrayList
HashMap
StringBuilder
```

---

## Immutable

State cannot change after creation.

Examples:

```
String
Integer
LocalDate
```

Benefits:

```
Thread safety
Caching
Security
```

---

# 5️⃣ String Internals

## String Pool

Java stores string literals inside a **String Pool**.

```
String a = "hello";
String b = "hello";
```

Both point to **same memory**.

---

### Creating New String

```
String s = new String("hello");
```

Creates:

```
Heap Object
+ Pool Entry
```

---

### String vs StringBuilder vs StringBuffer

| Type          | Thread Safe | Mutable |
| ------------- | ----------- | ------- |
| String        | Yes         | No      |
| StringBuilder | No          | Yes     |
| StringBuffer  | Yes         | Yes     |

---

# 6️⃣ Java Collections Framework

Hierarchy:

```
Iterable
   ↓
Collection
   ↓
List / Set / Queue
```

Maps are separate.

---

# List Implementations

```
ArrayList
LinkedList
Vector
CopyOnWriteArrayList
```

### ArrayList

Internally uses:

```
dynamic array
```

Resizing:

```
newCapacity = oldCapacity + oldCapacity/2
```

---

### LinkedList

Structure:

```
Doubly Linked List
```

Good for:

```
frequent insertions
```

---

# Set Implementations

```
HashSet
LinkedHashSet
TreeSet
```

| Type          | Ordering        |
| ------------- | --------------- |
| HashSet       | No order        |
| LinkedHashSet | Insertion order |
| TreeSet       | Sorted          |

---

# Map Implementations

```
HashMap
LinkedHashMap
TreeMap
ConcurrentHashMap
Hashtable
```

---

## HashMap Internals

Structure:

```
Array of Buckets
```

Bucket contains:

```
LinkedList (Java 7)
LinkedList → Tree (Java 8)
```

Tree conversion when:

```
bucket size ≥ 8
```

Load factor default:

```
0.75
```

---

# 7️⃣ Exception Handling

Types:

```
Checked Exceptions
Unchecked Exceptions
Errors
```

---

### Checked Exceptions

```
IOException
SQLException
```

Must be handled at compile time.

---

### Unchecked Exceptions

```
NullPointerException
IndexOutOfBoundsException
ArithmeticException
```

Runtime exceptions.

---

# 8️⃣ Generics

Generics allow **type-safe collections**.

Example:

```
List<String> names = new ArrayList<>();
```

Benefits:

```
Type safety
No casting
Compile-time checks
```

---

# 9️⃣ Java Memory Model (JMM)

Defines how threads interact with memory.

Important concepts:

```
Visibility
Atomicity
Ordering
```

---

## Stack vs Heap

Stack:

```
Method calls
Local variables
```

Heap:

```
Objects
Class instances
```

---

# 🔟 Multithreading

Thread = **independent execution path**.

---

## Creating Threads

### Using Thread Class

```
class MyThread extends Thread {
    public void run() {}
}
```

---

### Using Runnable

```
Runnable task = () -> {}
new Thread(task).start();
```

---

### Using Callable

```
Callable<Integer> task = () -> 10;
```

Returns result.

---

# Thread Lifecycle

```
NEW
RUNNABLE
BLOCKED
WAITING
TIMED_WAITING
TERMINATED
```

---

# Thread Safety Problems

```
Race Condition
Deadlock
Livelock
Starvation
```

---

# Synchronization

## synchronized

```
synchronized(object) {
}
```

Uses **monitor lock**.

---

## ReentrantLock

More flexible lock.

Features:

```
tryLock()
fairness
interruptible locks
```

---

## volatile

Guarantees:

```
visibility
```

But **not atomicity**.

---

## Atomic Classes

```
AtomicInteger
AtomicLong
AtomicReference
```

Uses:

```
CAS (Compare And Swap)
```

---

# Executor Framework

Manages thread pools.

```
ExecutorService
ThreadPoolExecutor
ScheduledExecutorService
```

---

## Types of Thread Pools

```
FixedThreadPool
CachedThreadPool
ScheduledThreadPool
SingleThreadExecutor
```

Benefits:

```
Thread reuse
Better performance
Controlled concurrency
```

---

# Concurrent Collections

```
ConcurrentHashMap
CopyOnWriteArrayList
BlockingQueue
```

---

## ConcurrentHashMap

Features:

```
Thread-safe
Lock striping
CAS operations
```

Used in **highly concurrent systems**.

---

# Synchronization Utilities

## Semaphore

Controls **number of permits**.

Use case:

```
connection pools
rate limiting
```

---

## CountDownLatch

Used when threads must **wait for other threads**.

Example:

```
service startup
```

---

## CyclicBarrier

Used when threads must **wait for each other**.

Example:

```
parallel algorithms
```

---

# Java 8 Features

## Lambda Expressions

```
(x, y) -> x + y
```

---

## Functional Interfaces

Examples:

```
Predicate
Function
Supplier
Consumer
```

---

## Streams API

Example:

```
list.stream()
    .filter(x -> x > 10)
    .map(x -> x * 2)
    .collect(...)
```

---

### Stream vs Parallel Stream

Parallel streams use:

```
ForkJoinPool
```

---

# Modern Java (Java 17+)

## Virtual Threads

Lightweight threads introduced with **Project Loom**.

Benefits:

```
millions of threads
low memory
better scalability
```

---

# Important Interview Topics

You should be able to explain:

```
HashMap internals
ConcurrentHashMap internals
Java Memory Model
ThreadPoolExecutor
volatile vs synchronized
String immutability
Garbage collection
```

---

# Must Practice Coding Problems

```
LRU Cache
Producer Consumer
Thread-safe Singleton
Rate Limiter
Blocking Queue
Thread Pool implementation
```

---

# Revision Strategy

Study in cycles:

```
Cycle 1 → Concepts
Cycle 2 → Internals
Cycle 3 → Interview Questions
Cycle 4 → Coding
```

---

# Recommended Learning Order

```
OOPS
Collections
JVM
Exception Handling
Generics
Multithreading
Concurrency Utilities
Java 8+
Virtual Threads
```

---

If you want, I can also give you a **second MD file** that senior engineers use called:

```
Java_Internal_Working.md
```

It explains deeply:

* HashMap internal algorithm
* ConcurrentHashMap internals
* ThreadPoolExecutor internals
* JVM memory + GC
* synchronized at JVM level

That file is **extremely powerful for interviews**.
