# 🧠 Object-Oriented Design Patterns in Python

This project demonstrates five commonly used **object-oriented design patterns** implemented in Python:

- **State Pattern (Паттерн Состояние)**
- **Composite Pattern (Паттерн Компоновщик)**
- **Iterator Pattern (Паттерн Итератор)**
- **Facade Pattern (Паттерн Фасад)**
- **Strategy Pattern (Паттерн Стратегия)**

Each pattern is implemented as a standalone, easy-to-read example that highlights the **core behavior and usage**.

---

## 🧩 1. State Pattern

**Purpose**: Allows an object to alter its behavior when its internal state changes.  
**Example Use Case**: A context object switching between modes or phases.

**How it works**:  
- `Context` holds a reference to a `State`.
- Calling `request()` transitions the state and delegates behavior.

---

## 🌿 2. Composite Pattern

**Purpose**: Treat individual objects and compositions of objects uniformly.  
**Example Use Case**: Representing hierarchical tree structures like GUI components or filesystems.

**How it works**:  
- `Leaf` represents a basic object.
- `Composite` can contain `Leaf` and other `Composite` objects.
- Both implement a shared interface.

---

## 🔁 3. Iterator Pattern

**Purpose**: Provide a way to access the elements of a collection sequentially without exposing its underlying representation.  
**Example Use Case**: Custom iterable containers.

**How it works**:  
- A custom `Iterator` class implements `__iter__()` and `__next__()`.
- A `Collection` class creates and returns its iterator.

---

## 🎛 4. Facade Pattern

**Purpose**: Provide a simplified interface to a complex subsystem.  
**Example Use Case**: Simplifying interaction with multiple APIs or services.

**How it works**:  
- Subsystems are encapsulated behind a unified `Facade` interface.
- Client interacts only with the facade.

---

## ⚙️ 5. Strategy Pattern

**Purpose**: Define a family of algorithms, encapsulate each one, and make them interchangeable.  
**Example Use Case**: Choosing between different behaviors dynamically at runtime (e.g. sorting, data transformation).

**How it works**:  
- The `Context` is configured with a `Strategy` object.
- Strategies are swappable at runtime to change behavior.
