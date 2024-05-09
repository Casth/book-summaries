# Book Summary - Dive Into Design Patterns

Author: Alexander Shvets

![Dive Into Design Patterns](<assets/Dive Into Design Patterns - cover image.png>)

Book distilled in [[Book Key Points - Dive Into Design Patterns]].

---

## 01 Introduction to OOP
**Chapter summary**:  
The concept of object oriented programming (OOP) is introduced, which bases on classes and objects. 
- A class contains multiple attributes, which can be categorized to fields (state) and methods (behavior). 
- OOP has four pillars: **abstraction** (object models necessary attributes and ignores the rest), **encapsulation** (hide parts of state and behaviors, expose limited interface), **inheritance** (build new class based on existing ones), and **polymorphism** (ability to detect the real class of an object and call its implementation). 
- Various relations exist between classes and objects. The weakest relation is **dependency**. On top of it, the relations go in two separate directions: **association** (A knows B) → aggregation (A knows, consists of B) → composition (A knows, consists of, manages life cycle of B); **implementation** (A defines methods declared in interface B) → inheritance (A inherits interface and implementation of B but can extend it) 
![](<assets/Dive Into Design Patterns - OOP relations.png>)

**Scope in book**:  
Design patterns are based on OOP. This chapter introduces the foundation of OOP.

---

## 02 Introduction to Design Patterns
**Chapter summary**:  
- Design patterns are typical solutions to commonly occurring problems in software design. Every pattern has its intent, motivation, structure, and code example. 
- Patterns are categorized into three groups: 
    + **creational** (creation mechanism)
    + **structural** (assembling objects and classes to larger structures)
    + **behavioral** (communication and assignment of responsibilities between objects)
- The history of software design patterns is briefly described at the end of this chapter. 

**Scope in book**: 
This chapter gives the definition of design pattern and introduces different types of it. The details of them are explained in chapter 4.

---

## 03 Software Design Principles

### 3.1 Features of Good Design
**Chapter summary**: 
Good software design aims to increase the re-usability of code, and achieve high extensibility to adapt to changes in the software's life cycle. 

**Scope in book**: 
Good design can be achieved by applying design patterns.

---

### 3.2 Design Principles
**Chapter summary**: 
Three design principles help to achieve good software design: encapsulate varying parts of software, depend on abstraction and not on concrete classes, and favor composition over inheritance. 
- **Encapsulate**: parts of program shall be isolated in independent modules. This can be done on method (behavior of a class) level, or on class level. 
- **Depending on abstraction** increases the extensibility of the program. The steps for applying it are: determine which methods are used between the objects → describe the methods in a new interface or abstract class → set the class of the first object to implement this interface → set the class of the second object to  depend on this interface. 
- **Favoring composition** over inheritance reduces the complexity of the program and makes its structure more clear. 

**Scope in book**: 
Design principles are the concrete high-level ways to achieve features of good design (chapter 3.1).

---

### 3.3 SOLID Principles
**Chapter summary**: 
SOLID include five design principles that are compatible with the basic design principles in chap. 3.2, but are more in detail. These five principles are Single responsibility principle, Open/closed principle, Liskov substitution principle, Interface segregation principle, Dependency inversion principle. 
1. **Single responsibility** principle aims to reduce the complexity of classes by separating the responsibility into multiple classes. 
2. **Open/closed** principle addresses the point that when creating a subclass, the functions at existing clients with original class shall not be broken. This can be achieved with for example the strategy pattern. 
3. **Liskov substitution** principle says that the subclass shall remain compatible with the behavior of the superclass. Several formal requirements must be fulfilled regarding parameter types, return type, exception, pre-condition, post-condition, invariants, and private field of superclass. 
4. **Interface segregation** principle aims to make the interface narrow enough so that no unnecessary behaviors are implemented. 
5. **Dependency inversion** principle requests that the high-level classes shall not depend on low-level classes. This is similar to the second basic principle ("depending on abstraction not concrete class"). 

**Scope in book**: 
SOLID principles base on the three basic design principles in chapter 3.2 and go beyond them. 

---

## 04 Catalog of Design Patterns

### 4.1 Creational Design Patterns
Creational design patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.

#### Factory method
**Chapter summary**: 
- Factory method deals with the problem, in which different variants of products need to be created. 
- This method provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects to be created. 
- The structure of it can be seen in two parts: the product and the creator. 
    1. The product part is first abstracted with an interface (⓵ in image below), which is then implemented by the different concrete product variants (⓶). 
    2. The creator part is built with a superclass as the base factory method, which uses the product interface (⓷). Creating new product is not the primary responsibility of the creator. It contains many other logics. This creator superclass is inherited by subclasses (⓸), each one of them overrides the base factory method so it can create a specific product variant. 
    ![](<assets/Dive Into Design Patterns - Factory Method.png>)
- With this factory method, the coupling between the creator and concrete products is loose. Therefore, when new product variant needs to be added, only a new product implementation and a new factory method subclass need to be added to the code. The main code remains intact.  

**Scope in book**: 
The factory method practices the single responsibility principle by moving all product creation code into one place, and the open/closed principle by allowing extending products without breaking existing client code.

---

#### Abstract factory
**Chapter summary**: 
- Abstract factory deals with the problem, in which variants of a product family need to be created. The product family can have different variants. At creation, the abstract factory makes sure that only products belonging to the same variant are produced, avoiding mixture of products across variants. 
- This method can be seen as an extension of the factory method, where the factory is now coupled with multiple products instead of a single product. 
- The structure of abstract factory can (like in factory method) be seen in two parts: the product family and the factory. 
    1. The product family with contained products is first declared as interfaces with abstract methods (⓵ in image below). The interfaces are implemented by the concrete product families (⓶). 
    2. An abstract factory is created also as interface, defining the methods for creating the products in the product family (⓷). Concrete factories can then implement this abstract factory, and create a specific variant of the product family (⓸). The client code is however not coupled with the concrete factory, but with the abstract factory (⓹). The desired variant of the product family is specified using initialization, which instantiates one concrete factory depending on the application configuration. This concrete factory is then used for product creation. 
    ![](<assets/Dive Into Design Patterns - Abstract Factory.png>)

**Scope in book**: 
The abstract factory is very similar to the factory method, but extends it. Instead of a single product, a product family is now produced. The varying part of the product is the product variants. Like factory method, the abstract factory also practices the single responsibility and the open/closed principle from SOLID.

---

#### Builder
**Chapter summary**: 
- Builder deals with the problem, in which the construction of a complex product consists of many steps. Based on the requirements, the necessary steps can vary, for example to construct a normal and a simplified version of the product. 
- Furthermore, even with the same steps, different variants of the product may be needed, for example products made by different materials but following the same steps. 
- The structure of builder can be seen in three parts: builder itself, director, and the client. 
    1. The builder is the central part for the construction of the product. The construction is first abstracted with a builder interface (⓵ in image below), which defines the common construction steps among all product variants (e.g., with different materials). This interfaces is then implemented by the concrete builders for the specific product variants (⓶), which construct the products (⓷). The product doesn't have to belong to the builder interface due to non-common return types of the product variants (e.g., metal product vs. wooden product). 
    2. The director is an optional part (⓸). The client can also directly interact with the concrete builder. The director defines the necessary construction steps in the right order, and can call a concrete builder to execute them. Different sets of steps can be defined in director (e.g., for normal and simplified product). 
    3. The client creates both the concrete builder and the director, and assigns the concrete builder to the director (⓹). Then it calls the director to start the construction, but gets the built product from the concrete builder. 
    ![](<assets/Dive Into Design Patterns - Builder.png>)
- In summary, the builder (interface and concrete) solves the problem of different product variants, while the director solves the problem of different construction steps for multiple product variants. 

**Scope in book**: 
The builder deals with complex products, where the construction cannot be built into the "creator" (as in factory method) or "factory" (as in abstract factory) due to its size and complexity. The construction part is therefore extracted and declared as an interface. 

---

#### Prototype
**Chapter summary**: 
- Prototype deals with object cloning. It solves two problems that are linked together: 
    + First, rather than creating new objects from the original class and copying all fields from the existing object to the new ones, prototype embeds the clone method into the objects, allowing it clones itself directly. 
    + Second, prototype also avoids the need to create a new class (based on the original class) only to address the small modification between the existing and the new objects. It allows to copy the existing object (without knowing its belonging class) and modify it from there. 
- The core structure of prototype is the prototype interface (⓵ in first image below), e.g., shape interface (or abstract class), which declares an abstract clone method. 
    + The concrete prototype then implements this interface (⓶) along with fields and other methods, e.g., rectangle, circle class. The concrete prototype class defines the clone method in detail. Based on the concrete prototype, objects (subclass prototypes) can be created by inheritance, e.g., big and small circle, big and small rectangle. These objects have the ability to clone themselves using the clone method, without to call the concrete prototype class. 
    + The client is coupled with the prototype interface. After the cloning, the parameters of the cloned objects can be modified. 
    ![](<assets/Dive Into Design Patterns - Prototype basic.png>)
- As an extended version, prototypes objects, which are frequently used can be stored in a prototype registry (⓵ in second image below), and be ready to be cloned. 
    + In this case, the client is coupled with the prototype registry. 
    ![](<assets/Dive Into Design Patterns - Prototype registry.png>) 

**Scope in book**: 
Prototype reduces the number of subclasses by cloning objects and then modified their parameters, avoiding the need of creating new subclasses for minor modifications. Comparing to it, factory method creates a new subclass for each product.

---

#### Singleton
**Chapter summary**: 
- Singleton ensures that a class has a single instance and there is globally a single access to this instance. 
- The structure of singleton is made in three steps: 
    1. In the target class, make the constructor private. This prevents the other objects to create new instance with the ``new`` operator. 
    2. Create a private static field to store the singleton instance which is to be constructed. 
    3. Create a public static method (e.g., ``getInstance()``, ⓵ in image below) that acts as a constructor. This constructor is the only method that can call the private constructor to create a new instance, and saves it in the static field. After the instance is created, all following calls to the static method (also ``getInstance()``) return the cached instance. In this way, all other objects are using the same instance of the class. 
    ![](<assets/Dive Into Design Patterns - Singleton.png>)
- Attention shall be taken in multithreaded environment so that multiple threads won't create a singleton instance multiple times. 

**Scope in book**: 
Singleton pattern can be used in abstract factory, builder, prototype, so that the constructor / factory / creator / builder / prototype is instanced only once by replacing the ``new`` (e.g., ``new concreteFactory()``) with the singleton static method (e.g., ``getInstance()``). Singleton violates the Single responsibility principle from SOLID, since it solves two problems at the time (ensure a single instance, and ensure a single global access to the instance). However, it doesn't prevent singleton to be a useful pattern.

---

### 4.2 Structural Design Patterns
Structural design patterns explain how to assemble objects and classes into larger structures, while keeping these structures flexible and efficient.

#### Adapter
**Chapter summary**: 
- Adapter deals with the problem that two classes (e.g., client and service class) in existing code have incompatible interfaces. It uses an adapter class, which converts the objects of the service class to compatible objects that fit the client interface. 
- The core structure of adapter is the adapter class (⓸ in first image below), which implements (or extends) the client interface (⓶). 
    + Inside the adapter class, the object of the service class (⓷) is set as private (⓸) and converted to compatible object of client interface. The converted object is then returned to the client. 
    + The client (⓵) isn't coupled to the adapter, but with the client interface, for example, the client "round hole" class always receives "round peg" class as interface, no matter whether the "round peg" object is an original one or a converted object from "square peg" by the adapter. This make it possible to modify the adapter or create new adapter without breaking the existing client code. 
    ![](<assets/Dive Into Design Patterns - Adapter object.png>)
- In an advanced adapter (class adapter), the adapter inherits interfaces from both the client and service (second image). 
    + This is however only possible in programming languages that supports multiple inheritance, such as C++. 
    ![](<assets/Dive Into Design Patterns - Adapter class.png>)

**Scope in book**: 
Adapter applies the single responsibility principle and the Open/closed principle from SOLID. It is used primarily to make existing classes compatible to each other, after the software is already created. Bridge pattern on the other hand is used usually up-front.

---

#### Bridge
**Chapter summary**: 
- Bridge solves the problem where a class contains several variants in form of combination of multiple orthogonal dimensions. It separates the class into independent hierarchies, with each of them corresponding to one specific dimension, and "bridges" these hierarchies. 
- The structure of bridge bases on the aggregation relation between the abstraction class (⓵ in image below) and the implementation interface (⓶). 
    + The "abstraction" represents one dimension and describes e.g. the high-level control logic for the client (⓹). The "abstraction" can be optionally extended (as a base abstraction) by "refined abstractions" (⓸), which represent the variants in this first dimension. 
    The "implementation" interface represents another independent dimension, and contains e.g. the low-level work. The "implementation" interface is then implemented by concrete implementations (⓷), which are the variants in this second dimension. The "implementation" is referenced as private field in the "abstraction", forming therefore the bridge. This methods of the referenced implementation are called in the methods of the "abstraction" class. 
    ![](<assets/Dive Into Design Patterns - Bridge.png>)
- To apply the bridge pattern, the orthogonal dimensions shall be identified first, such as GUI / platform, front-end / back-end, etc. The operations for the clients shall then be defined in the base "abstraction" class, while the common operations in the other dimension shall be defined in the "implementation" interface. 
- After that, a reference field shall be defined in the "abstraction" for the implementation type. Several abstraction variants can optionally be extended from the base one. 
- The client shall pass an concrete implementation object to the abstraction's constructor. 

**Scope in book**: 
Bridge is designed up-front, allowing developing the classes of different dimensions independently from each other. Comparing to it, adapter is used to existing apps to make classes compatible together. Bridge applies the design principle of favoring composition over inheritance. Bridge pattern can be combined with abstract factory (when some abstractions can only work with specific implementations) and builder (director acts as abstraction, builders act as implementations).

---

#### Composite
**Chapter summary**: 
- Composite deals with the case, in which the object has a tree-like structure, containing leaves and containers, which contain again leaves or containers. 
- With composite pattern, all elements (leafs and containers) will have unified interface, which makes the nested recursive call of the components easier and independent of their concrete classes. 
- The core element of the composite structure is the "component" interface (⓵ in image below), which provides the unified interface for leaf (⓶) and container ("composite", ⓷). 
    + The leaf class and the container class implement the "component" interface. The container class contains an array field to reference its sub-elements (further leaves and containers), and additional methods for adding and removing sub-elements from the array field. 
    + When the execution (e.g., ``execute()`` method) of the leaf class is called, the work is carried out as implemented. When execution of the container class is called, it delegates it to the contained sub-elements that are referenced in the array field (e.g., with ``foreach`` operator). 
    + With this unified interface, the client (⓸) can use the same interface (``execute()`` method), without to differentiate between the classes of the components. 
    ![](<assets/Dive Into Design Patterns - Composite.png>)

**Scope in book**: 
Builder can be used to create complex composite trees by conducting the construction steps recursively.

---

#### Decorator
**Chapter summary**: 
- Decorator provides a way to combine the functionality of several classes (with same interfaces) by recursively wrapping (referencing) one class within another. 
- Using this pattern, combinatorial inheritance of classes (as a bad way to combine functionality) can be avoided. 
- The structure of decorator can be seen in two parts: the component and the decorator. 
    1. A component interface (⓵ in image below) is the fundamental element in decorator pattern. It defines the unified interfaces for all components and decorators (e.g., ``execute()`` method). Concrete component class (⓶) implements the interface. It is the most basic element in the decorator pattern, and is responsible for conduct the work (with ``execute()`` method). 
    2. A base decorator class (⓷) implements also the component interface. It contains a private field that references the wrapped component or decorator (realizing recursive wrapping). When it's called (also via ``execute()`` method), it passes the call to the referenced item. Concrete decorator classes (⓸) are created by inheriting the base decorator classes, and can add more methods (``extra()`` method). Concrete decorators also override the methods of the base decorator, so that additional functionality are done before (or after) calling the parent methods. By following the same interface, the decorator provides a mechanism to wrap classes within each other, and extending the functionality with each wrapping. Example wrapping could be component → concrete decorator No.1 → concrete decorator No.2. 
    ![](<assets/Dive Into Design Patterns - Decorator.png>)
- The client (⓹) is responsible for creating the decorators and composing them in the desired order. 

**Scope in book**: 
Decorator ↔ composite: both have similar structures, however, a decorator has only one child item, while a composite can have multiple. Furthermore, decorator adds additional functionality to the wrapped item, while composite only passes the call to its child item. Decorator ↔ adaptor: decorator keeps the interface the same and enables recursive composition, while adaptor modifies the interfaces and realizes one-time composition. 

---

#### Facade
**Chapter summary**: 
- Facade simplifies the access of client to a complex system, which contains multiple subsystems. 
- Instead of interacting with the subsystems directly from the client, a facade is responsible for receiving the client request, and initializing and further life cycle management of the subsystems that are associated with the client request. 
- The core element of the facade structure is the facade class (⓵ in image below). 
    + It contains the private fields that reference various subsystems (⓷), and provides specific methods for client (⓸) requests. Within the specific methods, subsystems methods are called to realize the desired functionality. 
    + The subsystems are unaware of the facade, and can interact with each other. In this way, the details of the system is hidden from the client. 
    + Additional facade (⓶) class can be created to prevent the facade to be too complex. 
    ![](<assets/Dive Into Design Patterns - Facade.png>)

**Scope in book**: 
Facade ↔ adapter: adapter wraps one object, while facade works with an entire subsystems. Facade ↔ abstract factory: facade focuses on the usage of existing subsystems, while abstract factory can be used to hide the creation of subsystems from the client. Facade ↔ mediator: in facade pattern, the subsystems are unaware of the facade and can interact with each other directly, while in mediator pattern, the components only know the mediator and don't communicate directly. Facade ↔ singleton: facade can be created as singleton, since a single facade is sufficient in most cases.

---

#### Flyweight
**Chapter summary**: 
- Flyweight reduces the required amount of RAM of the software by merging the common parts among objects (with high RAM demand) and allowing variation of the uncommon part (with low RAM demand). 
- To apply the flyweight pattern, the objects in the software shall be analyzed regarding the attributes that have only a few unique values among all the objects (e.g., "texture" attribute has only five various values among >10k objects). 
    + These attributes are called intrinsic, and are kept stable for the object once they're instantiated. The corresponding class containing the intrinsic attributes is called the flyweight class. 
    + Other attributes have unique value for each object (e.g., "position" attribute has unique value in each of >10k objects) and are called extrinsic. These extrinsic attributes requires only small amount of RAM (e.g., "position" attribute uses only several Bytes of RAM). 
- The main idea behind flyweight pattern is to create as few flyweight objects as possible (therefore reducing RAM usage), and instantiate multiple final objects by extending each flyweight object with different values of extrinsic attributes. 
- The core of the structure of flyweight pattern is the flyweight class (⓵ in image below). 
    + It contains the intrinsic attributes (``repeatingState`` field). The client (⓹) doesn't create the flyweight objects directly, but asks the flyweight factory (⓺) to do it. The flyweight objects makes sure that only a single flyweight object is created for each unique flyweight type. The created flyweight objects are then passed to the context. 
    + The context class (⓷) contains a private field that references the corresponding flyweight object. It also contains the extrinsic attributes. The context adds the extrinsic attributes to the flyweight object, generating – based on one flyweight object – multiple final objects.  
    ![Alttext](<assets/Dive Into Design Patterns - Flyweight.png>)

**Scope in book**: 
Flyweight pattern makes the code complicated and shall be used only when necessary. Flyweight ↔ singleton: flyweight class can have multiple instances with different intrinsic values, while singleton class has only one instance. Furthermore, flyweight objects are immutable, while singleton can be mutable.

**Connecting other books** 
As mentioned in "Book - Making Embedded Systems > Chapter 6: Communicating with Peripherals", lightweight pattern can be used to change data in communication with peripherals in embedded system.

---

#### Proxy
**Chapter summary**: 
- Proxy adds pre-processing functionality to an existing service while keeping the interfaces to the client identical as the original service (hence proxy). 
- With proxy, various pre-processing functionality can be realized, such as lazy initialization, access protection, remote connection, requests logging, caching, heavyweight service object detection. This "added" functionality is especially useful as an extension of the original service, when the service is provided as 3rd-party service and not changeable. 
- The structure of proxy pattern includes the defined service interface (⓵ in image below) that is provided to the client (⓸). 
    + This interface is implemented both by the original service class (⓶) and the proxy class (⓷). The service class contains the real business logics (``operation()`` method) for the client. 
    + The proxy class contains a private field that references the service object and therefore manages the life cycle of this object. The proxy acts as a wrapper of the service object, and conducts pre-processing before calling the business logics of the service object. 
    ![](<assets/Dive Into Design Patterns - Proxy.png>)
- Since the the proxy has the identical interface as the service, the client isn't aware of the proxy's existence. The creation method shall decide whether the client gets a proxy or a real service. 

**Scope in book**: 
Proxy ↔ adapter ↔ decorator: Proxy has the identical interface as the service, while adapter provides different interfaces than the existing object, and decorator enhances the interface of the object by recursive wrapping. Proxy ↔ facade: Proxy is interchangeable with the service object thanks to identical interface, while facade hides the complex interfaces of the subsystems and provides simplified interface to client.

---

### 4.3 Behavioral Design Patterns
Behavioral design patterns are concerned with algorithms and the assignment of responsibilities between objects.

#### Chain of Responsibility
**Chapter summary**: 
- Chain of responsibility (CoR) provides a way to link multiple handlers of requests into a chain. Each handler decides either to pass the received request to the next handler, or process it. In this way, for requests with type or sequence unknown beforehand, an order of request handling can be designed. 
- Optionally, the order or handlers can be dynamically changed in runtime, since all handlers have the same interface. 
- The structure of CoR bases on the handler interface (⓵ in image below), which includes a single method for handling request. Optionally, it can contain a second method for setting the next handler. 
    + The base handler (⓶) implements the handler interface, and contains a private field that references the next handler. Common "next" relations include container, child, etc. By using this reference, the chain of responsibility is established. 
    + Multiple concrete handlers (⓷) inherit the base handler, and contain the real code for processing requests. It decides on its own, whether to process the received request, or to pass it along the chain. The client (⓸) may compose the chain just once or dynamically. 
    ![](<assets/Dive Into Design Patterns - Chain of Responsibility.png>)
- A request doesn't necessarily need to be sent to the first handler, but to any one within the chain. 

**Scope in book**: 
CoR ↔ decorator: both patterns rely on recursive composition to pass the execution though a series of objects. However, CoR handlers execute operations independently of each other and can stop passing request an any point, while decorators aren't allowed to break the flow of request.

---

#### Command
**Chapter summary**: 
- Command removes the tight coupling between the request sender and the request receiver by turning the request into stand-alone object, and use it as the intermediate interface between the sender and receiver. 
- The fundamental element of command's structure is the command interface (⓶ in image below). 
    + It contains a private method (``execute()`` method). The concrete command classes (⓷) implement the command interface, with each of them covers a command in the application. 
    + The concrete command class contains fields for storing the request arguments and for referencing the receiver object (⓸). It acts therefore as a request carrier from the sender to the receiver. 
    + The receiver is responsible to do the actual work caused by the request. 
    + The invoker (sender) class (⓵) communicate with its commands, which are referenced in its private field (``command`` field), only via the command interface. In this way, tight coupling with the concrete commands are avoided. 
    + The client (⓹) is responsible to initialize the objects in the following order: receivers → commands and associating them with receivers → senders and associating them with concrete commands. 
    ![](<assets/Dive Into Design Patterns - Command.png>)
- The advantage of command pattern is that it turns a specific call into a stand-alone object, which opens up new possibilities, such as stored inside other objects, queued, scheduled, or sent over the network. 

**Scope in book**: 
CoR, command, mediator, and observer all address the topic of connecting senders and receivers of requests.

---

#### Iterator
**Chapter summary**: 
- Iterator hides the complex data structure from the client by turning the data operation (such as traversal) into an object called iterator. It decouples the data collection from the data operation, and therefore makes the extension of new data operation or new data collection flexible. 
- The structure of iterator pattern includes two major parts: iterator and data collection. 
    1. The iterator interface (⓵ in image below) abstracts the data operation, and contains at least a method for fetching the next element from the data collection (``getNext()`` method). It can also contains other methods for fetching previous element, tracking current position, checking end of iteration, etc. The concrete iterator class (⓶) implements the iterator interface, and contains the specific algorithms for the data operation. It also contains field for referencing the concrete collection. 
    2. Data collection is abstracted first with the iterable collection interface. It contains methods to create compatible iterator for the data collection. The concrete collection class (⓸) implements the iterable collection interface, and creates new instances of particular concrete iterator class. The client (⓹) works with both iterator interfaces and data collection interfaces. In this way, tight coupling between the client with concrete iterator and data collection objects is avoided. 
    ![](<assets/Dive Into Design Patterns - Iterator.png>)

**Scope in book**: 
Iterator ↔ composite: iterator can be used to traverse composite trees. Iterator ↔ factory: Factory can be used to produce compatible iterator for data collection.

---

#### Mediator
**Chapter summary**: 
- Mediator reduces the dependencies between objects by redirecting all communications to the mediator object, not allowing direct communications between the components. 
- As result, the components aren't aware of other components and are only coupled with the mediator. At event, the component's job is to notify the mediator object, which then decides which components shall do the work. In this way, the reusability of the components is increased. 
- The structure of mediator pattern includes multiple components (⓵ in image below). 
    + The mediator interface (⓶) declares methods of communication with the components, which usually contain just a single notification method. All components use this method (such as ``notify(this)``) to pass the event to the mediator. 
    + The concrete mediator class (⓷) implements the mediator interface. It contains private fields for referencing all the associated components. On the other side, the instantiated mediator object is also referenced in all components in a private field. The concrete mediator receives the event from the component via the communication methods (e.g., ``notify(sender)`` method), and decides which actions to take based on the notified event. If components shall be involved in these actions, the concrete mediator calls them via the referenced fields. 
    ![](<assets/Dive Into Design Patterns - Mediator.png>)
- As an advanced step, the mediator can given the responsibility to manage the life cycle of the components by creating and destruction of the component objects. 

**Scope in book**: 
Mediator ↔ facade: in  mediator pattern, the components know only the mediator and don't communicate directly, while in facade pattern, the subsystems aren't aware of the facade, and communicate with each other directly. 

---

#### Memento
**Chapter summary**: 
- Memento deals with producing snapshots of an object and restoring them when needed. 
- The term "memento" is a snapshot of the object's state. Its content is immutable after being produced, and only limited accessible from external. 
- The structure of memento relies on nested classes (e.g., C++, C#, Java), with which the originator (⓵ in first image below) and the memento (⓶) are referencing each other (⓸), and the originator being able to access the (private) states in memento. 
    + The originator is the object with states, which need to be stored in snapshots. These states defined as private fields and not accessible from external. The originator contains public methods to produce (e.g., ``save(): Memento`` method) and restore (e.g., ``restore(m: Memento)`` method) mementos. 
    + The produced memento object has mirrored private fields as in the originator class to store the states. The fields are set only once during the construction of memento object. Afterwards, the fields are immutable, since there is no setter method. 
    + The caretaker (⓷) stores a stack of produced mementos. It is responsible for initiating the capturing of originator's state by calling the methods in originator. It can also initiate the restoring of states, by fetching the topmost memento from the stack and calling its method. 
    ![](<assets/Dive Into Design Patterns - Memento.png>)
- An advanced memento structure further restricts the access to the originator's state through the memento (second image below). 
    + In this case, neither originator nor the memento expose the state to anyone. 
    + The caretaker is independent from the originator, since the restoration method is defined in the memento class. Memento is linked to the originator object that produced it, and can restore the state of the originator by calling the setter method in the originator. 
    ![](<assets/Dive Into Design Patterns - Memento stricter encapsulation.png>)

**Scope in book**: 
Memento ↔ prototype: sometimes prototype can be a simpler alternative to memento, if the originator is straightforward.

---

#### Observer
**Chapter summary**: 
- Observer realizes the publish-subscribe pattern. Changes on the object of interest can be pushed to registered subscribers, without notifying unrelevant other objects. 
- Subscribers can be added or removed in the runtime. 
- The center in structure of observer is the publisher (⓵ in image below), which runs also the business logic. 
    + It is responsible for subscribing, unsubscribing, and notification of the subscribers. The publisher keeps the subscriber list, and provides methods for adding and removing objects into the list. It contains also the notification method (e.g., ``notifySubscriber()`` method) to notify all subscribers (⓶). 
    + Subscriber interface (⓷) is defined to provide the unified interface (e.g., ``update(context)`` method) for all concrete subscribers (⓸). Via the interface, contextual information (such as message, status) can be transferred from publisher to subscribers (⓹). 
    + The client (⓺) is responsible for creating publisher and subscriber objects separately, and for registering the subscribers into the list (using methods of publisher). 
    ![](<assets/Dive Into Design Patterns - Observer.png>)

**Scope in book**: 
Observer ↔ mediator: Observer is used to establish dynamic one-way connections between objects, while mediator is used to eliminate mutual dependencies among components. In extreme case, a mediator can be permanently connected with all components, but doesn't resemble the observer pattern. On the other side, even if all components become publishers (and realizing the observer pattern), no mediator exists in this case.

---

#### State
**Chapter summary**: 
- State deals with the situation, where a class have state-specific behavior, meaning the behavior of the function is different depending on the current state. 
- Instead of using state machine with complex if-else or switch statements, the state pattern defines a class for each state, which then defines the specific behavior in that state. 
- The starting point of the state pattern is the context (⓵ in image below), which includes business methods to do the real work, and also methods for changing state. 
    + It also references the state object with a private field. A state interface (⓶) is used, which contains abstract methods that mirror part of the methods (e.g., ``doThis()``, ``doThat()`` method) in context class. 
    + Concrete states (⓷) implement the state interface. It references also the context object with a private field. The now concretized methods (e.g., ``doThis()``, ``doThat()`` method) can be seen as state-dependent capsulation of the business methods in context class. Each concrete state uses and combines the business methods differently, in order to realize the specific behavior of the corresponding state. The state transition can be initiated by the context or the concrete state by replacing the state object linked to the context (⓸). 
    + The client can create context and state objects. By passing a specific state object to the context object, the context is dependent on the state object and behaves as defined in the specific state. 
    ![](<assets/Dive Into Design Patterns - State.png>)

**Scope in book**: 
State pattern enables adding or removing system states without breaking current codes. It could be an overkill if a state machine has only a few states or rarely changes.

---

#### Strategy
**Chapter summary**: 
- Strategy provides a structured approach to separate the different ways of realizing the functionality into separated classes called strategies. Each strategy is independent of other ones, and defines a specific way or algorithm for the functionality. 
- Based on the needs, different strategies can be chosen and set at runtime. 
- The structure of strategy includes the context class (⓵ in image below), which contains a private field to reference one concrete strategy. 
    + The strategy interface (⓶) defines the method (e.g., ``execute(data)`` method) that context uses to execute a strategy. 
    + Concrete strategies (⓷) implement the strategy interface, and concretizes the method (e.g., ``execute(data)`` method) with specific algorithm. 
    + The client creates strategy objects and passes it to the context (⓹). 
    + Every time the context is asked by the client (⓸) to run the business logic, it calls the strategy method to run the algorithm. The context doesn't know the detail of the strategy and its algorithm. The context provides a setter method, which lets client to replace the strategy at runtime.   
    ![](<assets/Dive Into Design Patterns - Strategy.png>)

**Scope in book**: 
Strategy ↔ state: Structure of both patterns are very similar, but strategy objects are independent and unaware of each other, while dependencies between concrete state objects aren't restricted.

---

#### Template Method
**Chapter summary**: 
- Template provides a framework of business logic in a superclass and allows subclasses to override part of it. 
- The business logic's outline of steps is declares as a normal method in a superclass, which contains multiple steps that need to be followed by all subclasses. The steps are declared as abstract methods. 
- In the subclasses, the abstract methods for the steps can be overwritten to provide specific algorithms. 
- The structure of template includes 
    + the abstract class (⓵ in image below), which defines the template method (e.g., ``templateMethod()``) that acts as the outline of steps. Optionally, the abstract class can also define several default methods that are common to all subclasses (e.g., ``step1()``, ``step2()`` methods). Other methods are abstract (e.g., ``step3()``, ``step4()`` methods) that need to be defined in subclasses. 
    + The concrete classes (⓶) inherit the abstract class, and can overwrite the abstract classes, but not the template method. In this way, different implementations of the business logic are realized. 
    ![](<assets/Dive Into Design Patterns - Template Method.png>)

**Scope in book**: 
Template ↔ factory: Template is a specialization of template, and can serve as a step in a large template. Template ↔ strategy: Template works as the class level and is therefore static, while strategy works at the object level and allows switch behavior at runtime. Further, template is based on inheritance and alters parts of an algorithm by extending those parts in subclasses. Strategy is based on composition and alters parts of object's behavior by supplying different strategies.

---

#### Visitor
**Chapter summary**: 
- Visitor allows to perform the same operation with different variants on all elements of a complex object structure. 
- The operation is placed in a class called visitor, which is separated from the existing object (or class). However, the decision to call which operation variant is not made within the visitor, but in the existing object, according to its class. This makes sure that the existing code needs to be modified as little as possible. 
- The structure of visitor pattern consists of two major parts: visitor and element. 
    1. The visitor interface (⓵ in image below) declares a set of methods that take concrete elements as input argument (e.g., ``visit(e: ElementA)`` method). These methods can have the same name (but different types of input arguments) if overloading is supported by the programming language. Otherwise, different names shall be selected for each type of concrete elements. The concrete visitors (⓶) implement the visitor interface, and define the methods with specific operations. 
    2. Element interface (⓷) declares a method for accepting visitors (e.g., ``accept(v: Visitor)`` method). This method has one input argument with the type of visitor interface. The concrete elements (⓸) implement the element interface (beside their business logics), and define the acceptance method. In this method, each concrete element (since it knows its own class) calls the corresponding method in the visitor. The client (⓹) works with element interface, and creates concrete visitor object. It calls the acceptance method of the elements (with the visitor object as input argument), which in turn calls the corresponding method of the visitor object (with the concrete element object as input argument), which finally performs the desired operation. Since the call is dispatched firstly to the concrete element, and then to the visitor, it is also called double dispatch. 
    ![](<assets/Dive Into Design Patterns - Visitor.png>)

**Scope in book**: 
Visitor can be used to execute an operation over an entire composite tree. It can be used along with iterator pattern to traverse complex data structure and execute operation over its elements, even if they have different classes.

---
Resource: 
- Alexander Shvets. Dive Into Design Patterns. refactoring.guru, 2018.