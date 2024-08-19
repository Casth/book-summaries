# Design Patterns - Elements of Reusable Object-Oriented Software

## General information
- Author: Erich Gamma, John Vlissides, Richard Helm, Ralph Johnson
- Book rating on Goodreads: 4.20 (updated: August 9th, 2024) [page link](https://www.goodreads.com/book/show/85009.Design_Patterns)
- A distilled (and shorter) book summary is located at [Design Patterns – Distilled summary](<Design Patterns – distilled summary.md>).
- Other summaries of the book
    + A short summary of the three categories of design patterns (creational, structural, behaviroal) [page link](https://santhosh-adiga-u.medium.com/my-notes-from-design-patterns-elements-of-reusable-object-oriented-software-book-2bf45dc33d1e). 
    + Summary and C++ code example for each design pattern [page link](https://medium.com/@murataslan1/summary-of-design-patterns-elements-of-reusable-object-oriented-software-book-3da3b347ec78)
    + Chapter-wise summary of the book [page link](https://danblevins.medium.com/my-reading-notes-from-design-patterns-elements-of-reusable-object-oriented-software-fc813ae05802)

![Design Patterns - Elements of Reusable Object-Oriented Software](<assets/Design Patterns - cover image.webp>)

---

## 01 Introduction
**Chapter summary**:  
- A design pattern is a description of communicating objects and classes that are customized to solve a general design problem in a particular context. Each design pattern of the introduced 23 ones has its own problem to solve, its solution, and consequences, but is still related to other patterns. 
- Three aspects are discussed: benefits of using design patterns, design pitfalls (that can be mitigated), and how to choose appropriate design patterns. 
    + Using design patterns brings several benefits. 
        * It gives the designer the ability to decompose a system into objects in the most suitable way. Designers can identify abstractions and objects with appropriate granularity in the software, which are less-obvious but can help to enable more flexible designs. 
        * It also helps to define the right interfaces of objects and classes, so that dynamic binding (issuing a request without committing to a particular implementation until run-time) can be done. This allows to separate the interface definition from the implementation of objects. 
        * Design patterns also help to design flexible implementation by depending on interface (instead of implementation), and favoring object composition over class inheritance. 
    + Design pitfalls (high dependency, tight coupling, etc.) cause rework at changes, and can also be mitigated with design patterns. 
    + Proper design patterns for the specific software need to be selected individually: understand how design patterns solve problems → revisit intention of each pattern (one-sentence summary of each design pattern) → understand relationship between patterns → study patterns in the relevant category (creational / structural / behavioral) → examine design pitfalls (8 common causes of rework with counteracting design patterns) → consider variable parts in own software design. 

**Scope in book**:  
This chapter emphasizes the necessity and the fundamental motivation of design patterns in OOP. It affects every aspect in the software design, including the decomposing a system into objects, designing interfaces, and implementation.

**Linkage to other books**: 
[Dive into Design Patterns](<Dive into Design Patterns – distilled summary.md>) has also discussed the motivation of design patterns, but more briefly with help of design principles. The explanation in this book is more in-depth and gives more insight to the original problems without design patterns.

(design pattern relationships)
![Alt text](<assets/Design Patterns - Design pattern relationships.png>)

(design aspects that design patterns allow to vary)
![Alt text](<assets/Design Patterns - Design aspects that design patterns allow to vary.png>)

---

## 02 A Case Study: Designing a Document Editor
**Chapter summary**:  
- A case study for designing a WYSIWYG document editor is shown. 
- Seven design challenges are raised at the beginning of the software design: fundamental document structure, formatting of elements (breaking texts into rows), flexible user interface, allowing different look-and-feel, supporting various operating systems, realizing uniformed mechanism for user operations, and flexible spelling checking and hyphenation. 
- These challenges are solved, after analyzing the problem, with appropriate design patterns. 
    1) With Composite pattern, text and graphic, as well as single elements and groups of elements are treated uniformly as glyph. 
    2) Strategy pattern is used for formatting, so that different formatting algorithms can be applied. 
    3) Decorator pattern is used for embellishing the user interface to add scroll bars, borders, and drop shadows in a flexible way. 
    4) Abstract Factory pattern is used for multiple look-and-feel, making sure that the same design is used for all the user interfaces elements within one look-and-feel. 
    5) Multiple operating systems support is realized with Bridge pattern by separating the functionality and the OS-dependent implementation from each other. In this way, the concept that varies is encapsulated. 
    6) User operations are formed as Command objects using the Command pattern. 
    7) For spelling checking and hyphenation, both Iterator and Visitor patterns are used. Iterator makes it possible to use different methods to traverse the glyphs (text, graphic, and group of them). Visitor pattern provides uniformed interface for spelling checking, while enabling different checking methods. 

**Scope in book**:  
The WYSIWYG document editor example shows that the architectural decisions are impacting the software structure and every aspect of the software. Proper design patterns help to encapsulate the varying parts of the software, and make it more flexible for future changes. Identifying the varying parts out of the whole software is a valuable ability of software architect.

---

## 03 Creational Patterns
Creational design patterns abstract the instantiation process, and help to make a system independent of how its objects are created, composed, and represented. A class creational pattern uses inheritance to vary the class that's instantiated, whereas an object creational pattern delegates the instantiation to another project.

---

### 03.1 Abstract Factory
**Chapter summary**:  
- Abstract Factory is used to provide an interface for creating families of related or dependent objects without specifying their concrete classes. 
- This pattern shall be used, when a system should be configured with one of multiple families of products, and the products in each family must be used together. 
- In this way, the system is independent of how its products are created, composed, and represented. Only the interfaces of the products are revealed to the client, but not the implementations. 

**Scope in book**:  
- Abstract Factory is often implemented with Factory Method, but can also be implemented with Prototype. 
- A Abstract Factory is often a Singleton.

(Structure of abstract factory)
![Alt text](<assets/Design Patterns - Abstract Factory.png>)

---

### 03.2 Builder
**Chapter summary**:  
- Builder separates the construction of a complex object (product) from its representation so that the same construction process can create different representations. 
- This pattern shall be used, when the algorithm for creating a product (using Director) should be independent of the parts that make up the product and how they're assembled (using Builder and ConcreteBuilder). 
- The client is responsible for creating the Director and configures it with the desired Builder object. After the product is created, the client retrieves the product from the Builder. 

**Scope in book**:  
- Builder ↔ abstract factory: Builder focuses on constructing a complex product step by step, and returns the product as final step, while abstract factory focuses on families of product objects, and returns the products immediately.

(Structure of Builder)
![Alt text](<assets/Design Patterns - Builder.png>)

---

### 03.3 Factory Method
**Chapter summary**:  
- Factory Method defines an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses. 
- This pattern shall be used, if a class can't anticipate the class of objects it must create, and wants its subclasses to specify the objects it creates. In this way, the responsibility is delegated to one of the subclasses. 
- The Creator declares the Factory Method, which returns an object of type Product. The ConcreteCreator (subclass) overrides the Factory Method to return an instance of a ConcreteProduct. 

**Scope in book**:  
- Abstract Factory is often implemented with Factory Method. Factory methods are usually called within Template methods.

(Structure of Factory Method)
![Alt text](<assets/Design Patterns - Factory Method.png>)

---

### 03.4 Prototype
**Chapter summary**:  
- Prototype specifies the kinds of objects to create using a prototypical instance, and create new objects by copying this Prototype. 
- This pattern shall be used to avoid complex class hierarchy of factories, or when the classes to instantiate are specified at run-time, e.g., by dynamic loading. 
- The Prototype declares the interface for cloning itself. The ConcretePrototype implements the operation for this interface. The client can create new object by asking a Prototype to clone itself. 

**Scope in book**:  
Prototype ↔ abstract factory: Prototype and abstract factory are competing patterns (see chap. 03.6 Discussion). Software designs that heavily uses Composite and Decorator patterns can often benefit from Prototype as well.

(Structure of Prototype)
![Alt text](<assets/Design Patterns - Prototype.png>)

---

### 03.5 Singleton
**Chapter summary**:  
- Singleton ensures a class only has one instance, and provides a global point of access to it. 
- This pattern shall be used if exactly one instance of a class is allowed and accessible to clients from well-known access point, such as ``Instance()`` operation. 

**Scope in book**:  
Singleton is used in many other patterns, such as abstract factory, Builder, and Prototype.

(Structure of Singleton)
![Alt text](<assets/Design Patterns - Singleton.png>)

---

### 03.6 Discussion of creational patterns
**Chapter summary**:  
Creation of class or object is commonly carried out in two ways. 
1) The first way is to subclass the class that creates the objects. Typical pattern is Factory Method. With this approach, new subclass is created only to change the class of the product. In some cases, the subclassing can repeat in multiple layers, causing lower subclass must even override the class that is several layers above. On the other side, this way (such as Factory Method) is the simplest approach and is widely used as starting point in software design. 
2) The second way is to reply on object composition, in which an object that knows the class of the product objects, and make it a parameter of the system. This is a key aspect of abstract factory, Builder, and Prototype. All three pattern involve creating a new "factory object", whose responsibility is to create product objects. Often, designs start out using Factory Method, and evolve toward other creational patterns to increase the flexibility (but also complexity). 

**Scope in book**:  
This chapter compares the creational patterns with each other, and points out the key characteristics of them.

---

## 04 Structural Patterns
Structural patterns are concerned with how classes and objects are composed to form larger structures. Structural class patterns use inheritance to compose interfaces or implementations. Structural object patterns describe ways to compose objects to realize new functionality. The added flexibility of object composition comes from the ability to change the composition at run-time, which is impossible with static class composition.

### 04.01 Adapter
**Chapter summary**:  
- Adapter converts the interface of a class into another interface that clients expect. 
- This pattern shall be used if the interface of an existing class doesn't match the one needed. 
- The implementation of Adapter is straightforward. Adapter can be done on the class or object level. The latter case is applicable, when there are several existing classes, but it's impractical to adapt their interface by subclassing every one. 

**Scope in book**:  
Bridge has similar structure to object Adapter, but focuses on the separation of interface from its implementation, while Adapter focuses on changing the interfaces of an existing object. Proxy does not change the interface of an object, while defining a surrogate for it.

(Structure of class Adapter)
![Alt text](<assets/Design Patterns - Class Adapter.png>)

(Structure of object Adapter)
![Alt text](<assets/Design Patterns - Object Adapter.png>)

---

### 04.02 Bridge
**Chapter summary**:  
- Bridge decouples an abstraction from its implementation so that the two can vary independently. 
- This pattern shall be used when a permanent binding between abstraction and its implementation shall be avoided, for example when the implementation must be switched at run-time. 
- Both the abstraction and the implementation should be extensible by subclassing. The methods in abstraction call the methods of the implementation object. 

**Scope in book**:  
Abstract Factory can create and configure a particular Bridge. Adapter is meant to make incompatible classes to work after they're designed, while Bridge is used up-front in a design to separate the abstraction and implementations.

(Structure of Bridge)
![Alt text](<assets/Design Patterns - Bridge.png>)

---

### 04.03 Composite
**Chapter summary**:  
- Composite lets clients treat individual objects and compositions of objects uniformly by composing objects into tree structures to represent part-whole hierarchies. 
- This pattern shall be used when the difference between composition of objects and individual objects shall be ignored. 
- Several issues need to be considered at using Composite, including having explicit referent to parent object, maximizing component interface, etc. 

**Scope in book**:  
Decorator is often used with Composite. Iterator can be used to traverse Composites.

(Structure of Composite)
![Alt text](<assets/Design Patterns - Composite.png>)

---

### 04.04 Decorator
**Chapter summary**:  
- Decorator attaches additional responsibilities to an object dynamically. It can be seen as an alternative to subclassing for extending functionality. 
- This pattern shall be used if the responsibilities need to be added dynamically and transparently (without affecting other objects), and also when extension by subclassing is impractical (e.g., causing an explosion of subclasses). However, using Decorator should be avoided when adding only one responsibility. 
- Applying Decorator pattern requires interface conformance. The class of the common component shall be lightweight.   

**Scope in book**:  
- Decorator ↔ Adapter: Decorator only changes an object's responsibility, not its interface, while an Adapter gives an object a completely new interface. 
- Decorator ↔ Composite: Decorator can be viewed as a Composite with only one component, but is intended to add responsibilities rather than object aggregation. 
- Decorator ↔ Strategy: Decorator allows to change the skin of an object, while Strategy allows to change the guts.

(Structure of Decorator)
![Alt text](<assets/Design Patterns - Decorator.png>)

---

### 04.05 Facade
**Chapter summary**:  
- Facade provides a unified interface to a subsystem, which includes multiple classes with different interfaces. With Facade, a higher-level interface is created that makes the subsystem easier to use. 
- This pattern shall be used when there are many dependencies between clients and the implementation classes, or when an entry point (Facade) to the subsystem shall be defined. 
- The Facade to the subsystem is analogue to the public interface of a class. It reduces the client-subsystem coupling. 

**Scope in book**:  
- Facade ↔ abstract factory: Abstract Factory can be used with Facade to provide an interface for creating subsystem objects in a subsystem-independent way. 
- Facade ↔ Mediator: Mediator is intended to abstract communication between colleague objects instead of let them communicate with each other directly. The colleague objects are aware of the Mediator. Facade merely abstracts the interface to subsystem, and doesn't define new functionality, and the subsystem classes aren't aware of the Facade. 

(Structure of Facade)
![Alt text](<assets/Design Patterns - Facade.png>)

#quick-questions 
- How can Abstract Factory be combined with Facade? Is there any code example?

---

### 04.06 Flyweight
**Chapter summary**:  
- Flyweight uses sharing to support large numbers of fine-grained objects efficiently. A Flyweight is a shared object that can be used in multiple context simultaneously. 
- It shall be distinguished between intrinsic and extrinsic state. 
    + Intrinsic state is stored in the Flyweight, and contains information that is independent of the Flyweight's context and therefore is sharable. 
    + Extrinsic state depends on and varies with the context and can't be shared. 
- Client is responsible for passing extrinsic state to the Flyweight when using it. 
- This patterns shall be used when an application uses a large number of objects, which would cost high storage, but most object state can be made extrinsic.  

**Scope in book**:  
- Flyweight ↔ Composite: Flyweight is often combined with Composite to implement a logically hierarchical structure with shared leaf nodes. 
- Flyweight ↔ State ↔ Strategy: State and Strategy objects should be implemented as flyweights.

(Structure of Flyweight)
![Alt text](<assets/Design Patterns - Flyweight.png>)

#quick-questions 
- How can Flyweight be combined with Composite? Is there any code example?

---

### 04.07 Proxy
**Chapter summary**:  
- Proxy provides a surrogate or placeholder for another object to control access to it. 
- This pattern shall be used whenever the reference to an object should be more than a simple pointer, but rather a more sophisticated reference, such as remote Proxy (represents locally for an object in different address space), virtual Proxy (creates expensive objects on demand), protection Proxy (controls access to the object), and smart reference (performs additional actions when an object is accessed).  

**Scope in book**:  
- Proxy ↔ Adapter: An Adapter provides a different interface to the object, while a Proxy provides the same interface. 
- Proxy ↔ Decorator: A Decorator adds responsibility to an object, while a Proxy controls access to an object.

(Structure of Proxy)
![Alt text](<assets/Design Patterns - Proxy.png>)

---

### 04.08 Discussion of structural patterns
**Chapter summary**:  
Structural patterns rely on small set of language mechanisms for structuring code and objects: single and multiple inheritance for class-based patterns, and object composition for object patterns. Two similar groups of patterns are discussed in this chapter: 
1) Adapter and Bridge both provide a level of indirection to another object. The key difference lies in the intents. Adapter focuses on resolving incompatibilities between two existing interfaces, without considering how the interfaces might evolve independently. Bridge, on the other side, bridges an abstraction and its implementations. Due to these differences, Adapter makes things work together after they're already designed, while Bridge makes them work before they are. 
2) Composite, Decorator, and Proxy are also similar patterns. Composite ↔ Decorator: The similarity between Decorator and Composite ends at recursive composition, because of differing intents. Decorator allows to add responsibilities to objects without subclassing, while Composite focuses on structuring classes so that related objects can be treated uniformly, and multiple objects can be treated as one. Decorator ↔ Proxy: In Proxy pattern, the subject defines the key functionality, and the Proxy provides (or refuses) access to it. In Decorator, the component provides only part of the functionality, and one or more decorators furnish the rest.  

**Scope in book**:  
This chapter underlines the key differences between the similar structural patterns. Although these patterns are similar in the implementation, the intention of the individual patterns differ strongly from each other.

---

## 05 Behavioral Patterns
Behavioral patterns deal with algorithms and assignment of responsibilities between objects. They describe not only patterns of objects or classes, but also the patterns of communication between them.

### 05.01 Chain of Responsibility (CoR)
**Chapter summary**:  
- Chain of Responsibility avoids coupling the sender of a request to its receiver by giving more than one object a chance to handle the request. The request is passed along the chain until an object handles it. 
- This pattern shall be used if the handle isn't known a priori, and the handler should be specified dynamically. 
- For the implementation, the chain of successor needs to be built, with which the handlers forward the request by default, but process the request if it can be handled. 
- In this way, the coupling between the sender and receiver(s) are reduced. New handlers can be added to the chain flexibly at runtime. 
- To be noticed is that if no handler in the chain can handle the request, the request can remain unhandled. 

**Scope in book**:  
CoR is often applied with Composite.

(Structure of CoR)
![Alt text](<assets/Design Patterns - Chain of Responsibility.png>)

---

### 05.02 Command
**Chapter summary**:  
- Command encapsulates a request as an object, and therefore allows to parameterize clients with different requests, queue or log requests, and supports undoable operations. Commands can be seen as object-oriented replacement for callbacks. 
- This pattern shall be used if the requests need to be specified, queued, and executed at different times, or if undoable and logged requests are required. As result, the invoker and the receiver of the request are decoupled. 
- For the implementation, the invoker shall invoke a Command only via the Command interface. Concrete commands inherit the interface and invoke the receiver's operation(s) to do the work. To support undo and redo, commands shall store additional state including the receiver object, the arguments to the operation performed on the receiver, and any original values in the receiver that will be changed due to the operation. 
- The application needs to keep a history list of commands that have been executed. 

**Scope in book**:  
- Command ↔ Memento: Memento can keep state the Command requires to undo its effect. 
- Command ↔ Prototype: A Command that must be copied before being placed on the history list acts as a Prototype.

(Structure of Command)
![Alt text](<assets/Design Patterns - Command.png>)

---

### 05.03 Interpreter
**Chapter summary**:  
- Interpreter is not mentioned in [[Book - Dive Into Design Patterns]], possibly due to its limited special usage. It defines a representation for its grammar for a given language, along with an Interpreter that uses the representation to interpret sentences in the language. Interpreter uses a class to represent each grammar rule. 
- This pattern shall be used when a language is to be interpreted, and when the statements in the language can be represented as abstract syntax trees. It is suitable for simple grammar, and where the efficiency is not a critical concern. 

**Scope in book**:  
- Interpreter ↔ Composite: The abstract syntax tree is an instance of Composite. Interpreter ↔ Iterator: Interpreter can use an Iterator to traverse the structure. 
- Interpreter ↔ Visitor: Visitor can be used to maintain the behavior in each node of the abstract syntax tree in one class.

(Structure of Interpreter)
![Alt text](<assets/Design Patterns - Interpreter.png>)

---

### 05.04 Iterator
**Chapter summary**:  
- Iterator provides a way to access the elements of an aggregate object (list) sequentially without exposing its underlying representation. It allows to traverse the list in different ways, and also to have more than one traversal pending on the same list. 
- The key idea is to take the responsibility for access and traversal out of the list object and put it into an Iterator object, which keeps track of the current element and the already traversed elements. 
- In its structure (image below), the Iterator defines the interface for accessing and traversing elements. The concrete Iterator implements the interface, and keeps track of the current position in the traversal. The aggregate defines an interface for creating an Iterator object. The concrete aggregate implements the Iterator creation interface to return an instance of concrete Iterator. 

**Scope in book**:  
- Iterator ↔ Composite: Iterators are often applied to recursive structures such as Composite. 
- Iterator ↔ Factory Method: Iterators rely on Factory Method to instantiate the appropriate Iterator subclass. 
- Iterator ↔ Memento: Memento is often used together with Iterator. An Iterator uses Memento to capture the state of an iteration. The Iterator stores the Memento internally. 

(Structure of Iterator)
![Alt text](<assets/Design Patterns - Iterator.png>)

---

### 05.05 Mediator
**Chapter summary**:  
- Mediator defines an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it allows to vary their interactions independently. 
- This pattern shall be used when a set of objects communicate in well-defined but complex ways, resulting in unstructured and hard-to-understand interdependencies, or when the reusing of an object is difficult because it refers to and communicates with many other objects. 
- As a result of this pattern, a Mediator replaces many-to-many interactions with one-to-many interactions between the Mediator and its colleagues. It trades complexity of interaction for complexity in the Mediator. 

**Scope in book**:  
- Mediator ↔ Facade: The protocol in Facade is unidirectional, meaning Facade object makes requests of the subsystem classes but not vice versa, while Mediator's protocol is multidirectional. 
- Mediator ↔ Observer: Colleagues can communicate with the Mediator using the Observer pattern.

(Structure of Mediator)
![Alt text](<assets/Design Patterns - Mediator.png>)

---

### 05.06 Memento
**Chapter summary**:  
- Memento captures and externalizes an object's internal state without violating encapsulation, so that the object can be restored to this state later. 
- The originator (see structure below) creates a Memento containing its current internal state and uses it later to restore the state. The originator has access to a wider interface of the Memento, which lets it access all data necessary to previous state (``GetState()`` and ``SetState()``). Ideally, only the originator that created the Memento will assign or retrieve its state. 
- The caretaker is responsible for the Memento's safekeeping, but never operates on or examines the contents of a Memento. It has access only to a narrow interface of the Memento (allowing only passing the Memento to other objects). 

**Scope in book**:  
- Memento ↔ Command: Commands can use mementos to maintain state for undoable operations. 
- Memento ↔ Iterator: Mementos can be used for iteration.

(Structure of Memento)
![Alt text](<assets/Design Patterns - Memento.png>)

---

### 05.07 Observer
**Chapter summary**:  
- Observer defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically. This pattern is also know as publish-subscribe. 
- The subject class provides an interface for attaching and detaching Observer objects. In this way, the subject knows all its Observers. It also defines the method to notify all Observers. 
- The Observer class defines an updating interface. At updating, the concrete Observer fetches the lastest states via the methods defined in the concrete subject (``GetState()`` and ``SetState()``). 
- With Observer pattern, the coupling between subject and Observer is abstract. When the dependency relationship between subjects and Observers is fairly complex, a Change Manager can be used to maintain the relationships, such as ensure that Observers are notified only after all the relevant subjects have been modified to avoid unnecessary multiple notifications. 

**Scope in book**:  
- Observer ↔ Mediator: Change Manager acts as Mediator between subjects and Observers. 
- Observer ↔ Singleton: Change Manager may use Singleton  pattern to make it unique and globally accessible.

(Structure of Observer)
![Alt text](<assets/Design Patterns - Observer.png>)

(Collaboration between a subject and two Observers)
![Alt text](<assets/Design Patterns - Observer - collaboration between a subject and two Observers.png>)

---

### 05.08 State
**Chapter summary**:  
- State allows an object to alter its behavior when its internal state changes. The object will appear to change its class. 
- This pattern shall be used if an object's behavior depends on its state, and must change its behavior at run-time. 
- The context class defines the interface of interests to client. It is also the primary interface for clients. It maintains an instance of a concrete State subclass that defines the current state. The context may pass itself as an argument to the State object, and lets the State object access the context if necessary. 
- The State class defines the interface for encapsulating the behavior associated with a particular state of the context. Each concrete State subclass implements the specific behavior. 
- State pattern puts all behavior associated with a particular state into one object, and makes it easy to add new states and transitions. 
- Also as a consequence of this pattern, the state transitions is explicit. 

**Scope in book**:  
- State ↔ Flyweight: Flyweight pattern explains when and how State objects can be shared. 
- State ↔ Singleton: State objects are often Singletons.

(Structure of State)
![Alt text](<assets/Design Patterns - State.png>)

---

### 05.09 Strategy
**Chapter summary**:  
- Strategy defines a family of algorithms, encapsulates each one, and makes them interchangeable. It lets the algorithm vary independently from clients that use it. 
- The Strategy declares the interface to all supported algorithms. The context uses this interface to call the algorithm defined by a concrete Strategy. 
- A potential drawback of this pattern is that the clients must be aware of the different strategies before it can select the appropriate one. 

**Scope in book**:  
- Strategy ↔ Flyweight: Strategy objects often make good flyweights.

(Structure of Strategy)
![Alt text](<assets/Design Patterns - Strategy.png>)

**Linkage to other books**: 
- According to [Dive into Design Patterns](<Dive into Design Patterns – distilled summary.md>), Strategy and State have very similar structure. But Strategy objects are independent and unaware of each other, while concrete States can be dependent from each other.

---

### 05.10 Template Method
**Chapter summary**:  
- Template Method defines the skeleton of an algorithm in an operation, deferring some steps to subclasses. It lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure. 
- In this way, the invariant parts of the algorithm are implemented once, and the varying parts are deferred to the subclasses to be defined. 
- Hook operations (may be overridden) can be defined in template and do nothing by default, which are different than the abstract operations (must be overridden). 

**Scope in book**:  
- Template Method ↔ Factory Method: Factory Method is often called by Template Method. 
- Template Method ↔ Strategy: Template Method uses inheritance to vary part of an algorithm, while Strategy uses delegation to vary the entire algorithm.

(Structure of Template Method)
![Alt text](<assets/Design Patterns - Template Method.png>)

---

### 05.11 Visitor
**Chapter summary**:  
- Visitor represents an operation to be performed on the elements of an object structure. Visitor allows to define a new operation without changing the classes of the elements on which it operates. 
- With this pattern, specific operations can be performed depending on the concrete classes. 
- The Visitor declares a visit operation for each class of concrete element in the object structure. The concrete Visitor implements the declared operation. 
- The element defines an accept operation that takes a Visitor as an argument, which is then implemented by the concrete elements. The object structure provides a high-level interface to allow the Visitor to visit its elements. When an element is visited, it calls the Visitor operation that corresponds to its class, and supplies itself as an argument to this operation if necessary. 
- The Visitor can access the state of the element. In the Visitor pattern, new operations can be added easily (by adding new Visitor), while adding new concrete elements is hard. 

**Scope in book**:  
- Visitor ↔ Composite: Visitor can be used to apply an operation over an object structure defined by Composite. 
- Visitor ↔ Interpreter: Visitor may be applied to do the interpretation.

(Structure of Visitor)
![Alt text](<assets/Design Patterns - Visitor.png>)

(Interaction diagram between an object structure, a Visitor, and two elements)
![Alt text](<assets/Design Patterns - Visitor interactions.png>)

---

### 05.12 Discussion of Behavioral Patterns
**Chapter summary**:  
Four characteristics are discussed: encapsulating variation, objects as arguments, encapsulated or distributed communication, and decoupling senders and receivers. 
1) Encapsulating variation: When an aspect of a program changes frequently, many behavioral patterns define an encapsulation of that aspect by defining an abstract class that describes the encapsulating object. Examples are Strategy, state, Mediator, Iterator. 
2) Objects as arguments: In some behavioral patterns, the object is used as an argument to allow to access the methods of the objects. Example are Visitor, Command, Memento. 
3) Encapsulated or distributed communication: Observer pattern distributes communication while Mediator pattern encapsulates it. It is therefore easier to make reusable Observers than mediators, although the communication flow is easier to understand in Mediator than Observer. 
4) Decoupling senders and receivers: Command, Observer, Mediator, Chain of Responsibility allow to decouple senders and receivers, but with different trade-offs.  
    + Commands supports decoupling by using a Command object as the binding (first image below). 
    + Observer realizes the decoupling by defining an interface for signaling changes in subjects (second image below). 
    + Mediator decouples objects by having them refer to each other indirectly through a Mediator object (third image below). 
    + Chain of Responsibility decouples the objects by passing the request along a chain of potential receivers (fourth image below). 

**Scope in book**:  
This chapter summarizes the major characteristics of the behavioral patterns, and highlights the differences between them.

(Decoupling with Command)
![Alt text](<assets/Design Patterns - Decoupling with Command.png>)

(Decoupling with Observer)
![Alt text](<assets/Design Patterns - Decoupling with Observer.png>)

(Decoupling with Mediator)
![Alt text](<assets/Design Patterns - Decoupling with Mediator.png>)

(Decoupling with Chain of Responsibility)
![Alt text](<assets/Design Patterns - Decoupling with Chain of Responsibility.png>)

---

## 06 Conclusions
**Chapter summary**:  
- The design pattern catalog came originally from the Ph.D. thesis of Erich Gamma. A brief history of the book was given in this chapter. 
- It also summarizes the benefits of design patterns. They can be used as a common design vocabulary, for better understanding of existing systems and designing better systems, as an adjunct method for OOP, and for refactoring existing software. 
- A comparison between the software design patterns and the pattern language by Christoph Alexander for buildings is described. 

**Scope in book**:  
This chapter gives a final thoughts on the design patterns on a higher level. It gives an overview of existing researches in this area as well as the similarity and difference between the software design patterns and patterns for buildings.