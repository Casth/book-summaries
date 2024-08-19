# Key Points - Design Patterns - Elements of Reusable Object-Oriented Software

## General information
- Author: Erich Gamma, John Vlissides, Richard Helm, Ralph Johnson
- Book rating on Goodreads: 4.20 (updated: August 9th, 2024) [page link](https://www.goodreads.com/book/show/85009.Design_Patterns)
- A full (and longer) book summary is located at [Design Patterns – Full summary](<Design Patterns – full summary.md>).
- Other summaries of the book
    + A short summary of the three categories of design patterns (creational, structural, behaviroal) [page link](https://santhosh-adiga-u.medium.com/my-notes-from-design-patterns-elements-of-reusable-object-oriented-software-book-2bf45dc33d1e). 
    + Summary and C++ code example for each design pattern [page link](https://medium.com/@murataslan1/summary-of-design-patterns-elements-of-reusable-object-oriented-software-book-3da3b347ec78)
    + Chapter-wise summary of the book [page link](https://danblevins.medium.com/my-reading-notes-from-design-patterns-elements-of-reusable-object-oriented-software-fc813ae05802)

![Design Patterns - Elements of Reusable Object-Oriented Software](<assets/Design Patterns - cover image.webp>)

---

## Part I – Introduction
Chapter 1 and 2 describe on a high-level the motivation and benefits of design patterns, and gives also recommendations for selecting proper design pattern for specific software.

The mastering of design patterns enables the designers to identify abstractions and objects with appropriate granularity in a software, and to decompose the system in the most suitable way. The usage of design patterns also helps to define the right interfaces of objects and classes, and to create flexible implementations by depending on interface (instead of implementation) and favoring object composition (over class inheritance).

The selection of proper design pattern for a specific software follows several steps: 
1. Understand how design patterns solve problems.
2. Revisit intention of each pattern (one-sentence summary of each design pattern).
3. Understand relationship between patterns.
4. Study patterns in the relevant category (creational / structural / behavioral).
5. Examine design pitfalls (8 common causes of rework with counteracting design patterns).
6. Consider variable parts in own software design.

(design pattern relationships)
![Alt text](<assets/Design Patterns - Design pattern relationships.png>)

---

## Part II – Creational Patterns
Creational design patterns abstract the instantiation process, and help to make a system independent of how its objects are created, composed, and represented. A **class** creational pattern uses inheritance to vary the class that's instantiated, whereas an **object** creational pattern delegates the instantiation to another project.

- **Abstract Factory**
	+ aspects that vary: families of product objects
	+ pattern's intention: provide an interface for creating families of related or dependent objects without specifying their concrete classes
- **Builder**
	+ aspects that vary: how a composite object gets created
	+ pattern's intention: separate the construction of a complex object from its representation so that the same construction process can create different representations
- **Factory Method**
	+ aspects that vary: subclass of object that is instantiated
	+ pattern's intention: define an interface for creating an object, but let subclasses decide which class to instantiate
- **Prototype**
	+ aspects that vary: class of object that is instantiated
	+ pattern's intention: specify the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype
- **Singleton**
	+ aspects that vary: the sole instance of a class
	+ pattern's intention: ensure a class only has one instance, and provide a global point of access to it

---

## Part III – Structural Patterns
Structural patterns are concerned with how classes and objects are composed to form larger structures. Structural **class** patterns use inheritance to compose interfaces or implementations. Structural **object** patterns describe ways to compose objects to realize new functionality. The added flexibility of object composition comes from the ability to change the composition at run-time, which is impossible with static class composition.

- **Adapter**
	+ aspects that vary: interface to an object
	+ pattern's intention: convert the interface of a class into another interface that clients expect
- **Bridge**
	+ aspects that vary: implementation of an object
	+ pattern's intention: decouple an abstraction from its implementation so that the two can vary independently
- **Composite**
	+ aspects that vary: structure and composition of an object
	+ pattern's intention: let client treat individual objects and compositions of objects uniformly by composing objects into tree structures to represent part-whole hierarchies
- **Decorator**
	+ aspects that vary: responsibilities of an object without subclassing
	+ pattern's intention: attach additional responsibilities to an object dynamically
- **Facade**
	+ aspects that vary: interface to a subsystem
	+ pattern's intention: provide a unified interface to a subsystem, which includes multiple classes with different interfaces
- **Flyweight**
	+ aspects that vary: storage costs of objects
	+ pattern's intention: use sharing to support large number of fine-grained objects efficiently
- **Proxy**
	+ aspects that vary: how an object is accessed; its location
	+ pattern's intention: provide a surrogate or placeholder for another object to control access of it

---

## Part IV – Behavioral Patterns
Behavioral patterns deal with algorithms and assignment of responsibilities between objects. They describe not only patterns of objects or classes, but also the patterns of communication between them.

- **Chain of Responsibility (CoR)**
	+ aspects that vary: object that can fulfill a request
	+ pattern's intention: avoid coupling the sender of a request to its receiver by giving more than one object a chance to handle the request
- **Command**
	+ aspects that vary: when and how a request is fulfilled
	+ pattern's intention: encapsulate a request as an object, and therefore allows to parameterize clients with different requests, queue or log requests, and supports undoable operations
- **Interpreter**
	+ aspects that vary: grammar and interpretation of a language
	+ pattern's intention: define a representation for its grammar for a given language, along with an interpreter that uses the representation to interpret sentences in the language
- **Iterator**
	+ aspects that vary: how an aggregate's elements are accessed, traversed
	+ pattern's intention: provide a way to access the elements of an aggregate object (list) sequentially without exposing its underlying representation
- **Mediator**
	+ aspects that vary: how and which objects interact with each other
	+ pattern's intention: define an object that encapsulate how a set of objects interact
- **Memento**
	+ aspects that vary: what private information is stored outside an object, and when
	+ pattern's intention: capture and externalize an object's internal state without violating encapsulation, so that the object can be restored to this state later
- **Observer**
	+ aspects that vary: number of objects that depend on another object; how the dependent objects stay up to date
	+ pattern's intention: define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically
- **State**
	+ aspects that vary: states of an object
	+ pattern's intention: allow an object to alter its behavior when its internal state changes
- **Strategy**
	+ aspects that vary: an algorithm
	+ pattern's intention: define a family of algorithms, encapsulate each one, and make them interchangeable
- **Template Method**
	+ aspects that vary: steps of an algorithm
	+ pattern's intention: define the skeleton of an algorithm in an operation, deferring some steps to subclasses
- **Visitor**
	+ aspects that vary: operations that can be applied to object(s) without changing their class(es)
	+ pattern's intention: represent an operation to be performed on the elements of an object structure; allow to define a new operation without changing the classes of the elements on which it operates 