# Book Summary - Learning UML 2.0

Authors: Russ Miles, Kim Hamilton

![cover image](<assets/Learning UML 2.0 - cover image.png>)

---

## 01. Introduction
**Chapter summary**: \
UML 2.0 is a formal modeling language, and includes use cases, activities, class, object and further different diagram types. The Kruchten's 4+1 view model incl. use case, logical, process, development, physical views are used in this book. The UML diagrams can be used to contribute to each of these views.

### Summary of listed diagrams into 4+1 views
- **Logical View**
	+ class diagram
	+ object diagram
	+ sequence diagram
	+ communication diagram (not categorized in any view in book)
	+ interaction overview diagram (not categorized in any view in book)
	+ composite structure
	+ state machine diagram
- **Physical View**
	+ deployment diagram
- **Process View**
	+ activity diagram
	+ timing diagram (not categorized in any view in book)
- **Development View**
	+ component diagram
	+ package
- **Use Case View**
	+ use case diagram


---

## 02. Modeling Requirements: Use Cases
**Chapter summary**: \
Use cases are normally the starting point at designing a system based on requirements. A use case diagram consists of actors, use cases, communication lines, system boundaries and use case description. Relationships between the use cases can be indicated in use case diagram including "include", "special case" and "extend". 

**Scope in book**: \
Use case diagram is the first diagram type in UML 2.0. It contributes to the use case view of Kruchten's 4+1 view model (chap. 01). Use case view affects all other four views.

### Use Case Diagram
- A *use case* is a situation where the system fulfills one or more of user's requirements. It captures a piece of functionality that the system provides. The use cases correspond to the system's functional requirements.
- The use cases shall be the starting point of the project. 
- Benefits of building use cases are:
	+ identify gaps in the requirements 
	+ prioritize use cases and determine workload
	+ derive test cases
- Building blocks of a use case
	+ actors
	+ use cases
	+ communication lines
	+ system boundaries
	+ use case description
- **Actors**
	+ an actor interacts with the system and is not part of the system
	+ tricky actors are e.g. system clock \
      ![](<assets/Learning UML 2.0 - tricky actors.png>)
- **Use cases**
	+ use case represents that the system is used to complete a specific job for an actor
	+ use case must have very clear pass/fail criteria
- **Communication lines**
	+ a communication line connects an involved actor and a use case
	+ a use case can be connected with multiple actors
	+ the communication line does not show direction or which actor starts the use case
- **System boundaries**
	+ show explicitly what is inside and outside the system
- **Use case description**
	+ use case diagram alone lacks of enough detail to understand the system functionalities
	+ therefore, (at least one) text-based use case description is required for each use case diagram
	+ use case description is used also for identifying gap in the use case diagram (e.g. forgotten actors)
	+ the following information can be included in the use case description \
      ![](<assets/Learning UML 2.0 - use case description.png>)
	+ example \
      ![](<assets/Learning UML 2.0 - use case example.png>)

### Use Case Relationships
- Use case relationships
	+ include
	+ special cases
	+ extend
- **"Include" relationship**
	+ multiple use cases share repetitive behavior, which can be captured with a new use case
	+ the "include" relationship declares at the tail of the dotted arrow the complete reuse of all steps of the included use case
	+ in the use case description, the repetitive steps of the use cases must be removed and replaced by ``include::<included use case>``, for example ``include::Check Identity``
	+ the "include" relationship indicates the reusable part of the system
	  (example: "Check Identity" is the included use case and is repetitive for the other two use cases) \
      ![](<assets/Learning UML 2.0 - use case include relationship.png>)
- **"Special cases" relationship**
	+ multiple use cases are special cases of (and point with generalization arrow to) a general use case
	+ the general use case is also called the parent use case
	+ every step and every actor relationship in the general use case must be valid in the specialized use case
	  (example: "Create a new Blog Account" is the general and parent use case) \
      ![](<assets/Learning UML 2.0 - use case special cases relationship.png>)
- **"Extend" relationship**
	+ "extend" stereotype is the most controversial type of use case relationship within UML
	+ an "extended" relationship denotes the extended use case as an optional step, that can be added ("extended") to a use case
	  (example: "Record Application Failure" can be added optionally to the other two use cases) \
      ![](<assets/Learning UML 2.0 - use case extended relationship.png>)

### Use Case Overview Diagram
- *Use Case Overview diagram* shall not be confused with use case diagram. This diagram shows the system context (actors, relationships with actors) but not the use cases.
  (example)
  ![](<assets/Learning UML 2.0 - use case overview diagram.png>)

---

## 03. Modeling System Workflows: Activity Diagrams
**Chapter summary**: \
The activity diagram is the only diagram in the process view. It describes how (step by step) the system realizes the required functions. An activity diagram consists of the elements such as initial node, actions, edges / paths, decision, merge, and final node (and further elements that are used less frequently). 

**Scope in book**: \
While the use case diagram shows the realized functions of the system in a static way, the activity diagram shows how this functions are realized step by step. It displays therefore more internal parts of the system, and contributes to the white box model. 

(Activity diagram) \
![](<assets/Learning UML 2.0 - activity diagram.png>)

---

## 04. Modeling System's Logical Structure: Classes and Class Diagrams
**Chapter summary**: \
Classes contribute to the logical view of the system. A class encapsulates both the data (attributes) and the operations. Visibility can be defined for both the class's attributes and operations (public / protected / package / private) to control the allowed access to them. 

**Scope in book**: \
Classes (and the derived objects) define the elements in a system, and therefore contribute to the logical architecture view. 

(Class attributes) \
![](<assets/Learning UML 2.0 - class attributes.png>)

(Class operation) \
![](<assets/Learning UML 2.0 - class operation.png>)

---

## 05. Modeling System's Logical Structure: Advanced Class Diagrams
**Chapter summary**: \
This chapter describes the functions beyond the basic function of a class. Firstly, classes can have various relationships with each other. These are (from weak to strong coupling) dependency, association, aggregation, composition, inheritance (also called generalization). These relationships make the description of complex system modeling possible. Secondly, this chapter describes also several advanced features of class, such as class constraints (invariant, precondition, postcondition), abstract class, interfaces (similar to class, has only operations without method implementations), and template. 

**Scope in book**: \
This chapter builds upon the last chapter and has introduced more sophisticated usage of classes.

(Relationships) \
![](<assets/Learning UML 2.0 - relationships.png>)

(Abstract class) \
![](<assets/Learning UML 2.0 - abstract class.png>)

(Interface) \
![](<assets/Learning UML 2.0 - interface.png>)

---

## 06. Bringing Classes to Life: Object Diagrams
**Chapter summary**: \
Object diagram shows how the objects (as instances) in the system work with each other (while class diagram shows the object types and their relationships). Therefore, the object diagram shows the logical view. The representation of objects is fairly simple and in some way similar to the classes. 

**Scope in book**: \
The objects are the instances of the classes defined in chapter 4 and 5. The attributes, operations of the classes and their associations are inherited by the objects, and therefore must be complied with.

(Object) \
![](<assets/Learning UML 2.0 - object.png>)

(Link) \
![](<assets/Learning UML 2.0 - link.png>)

---

## 07. Modeling Ordered Interactions: Sequence Diagrams
**Chapter summary**: \
Sequence diagram belongs to interaction diagrams and shows runtime interactions of the system. A sequence diagram consists of multiple parts, including participants, time lines, events, messages (or signals), message signatures, activation bars, etc. Message can be synchronous (caller waits for return of invocation from receiver) or asynchronous (caller doesn't wait). Sequence fragments can be used for complex interactions, such as optional, reference, loop fragments etc. 

**Scope in book**: \
Sequence diagrams shows the dynamic behavior of the system. Static behaviors, such as in use case diagrams, can be transferred to sequence diagrams, showing more dynamic details such as messages, orders of actions, conditions, etc. 

---

## 08. Focusing on Interaction Links: Communication Diagrams
**Chapter summary**: \
Communication diagram shows almost the same information as sequence diagram. It consists of three parts: participants, communication links, and messages. The links indicate the participants can communicate with each other. The messages are numbered in order to indicate the order of the messages. 

**Scope in book**: 
1) Relationship to sequence diagram: A sequence diagram can be converted to communication diagram without losing information. Since the messages in communication diagram are not listed from top to bottom any more, the messages must be numbered to show the order. 
2) Relationship to object diagram: Communication diagram is somehow similar to object diagram, while the former shows the dynamic behavior of the system, and the latter shows the static behavior. Both diagrams contain links, indicating communication between the participants / objects. However, the links in object diagram shows rather the association between the object (with no message on the links), while the communication diagram shows the communication messages sent between the participants.

---

## 09. Focusing on Interaction Timing: Timing Diagrams
**Chapter summary**: \
Timing diagram shows the timing aspects of the system, such as events and messages timing, system states over time, and timing constraints. The form of a timing diagram is similar to a logic analyzer (or CANalyzer diagram), containing participants, states of each participant, time axis, state line, event and messages, and timing constraints. There is an alternative notation for timing diagram, where the states of the participants are not listed upon each other but shown horizontally, where the state is active. This alternative notation reduced the height and complexity of the diagram. 

**Scope in book**: \
Timing diagram is the only diagram indicating timing aspects, showing timing constraints which are not shown in sequence diagram.

---

## 10. Completing the Interaction Picture: Interaction Overview Diagrams
**Chapter summary**: \
Interaction overview diagram is similar to activity diagram, and shows the activities between the initial and final node. However, instead of short name, the activities are represented with detailed (embedded) diagrams, such as in form of sequence diagram, timing diagram, communication diagram etc. The participants in the interaction overview diagrams are listed in the diagram title. The interaction overview diagram provides therefore more information than normal activity diagram, is however more complex. 

**Scope in book**: \
The interaction overview diagram can be understood as a combination of different kinds of diagrams for system dynamic behavior, with the foundation / basic structure of activity diagram.

---

## 11. Modeling a Class's Internal Structure: Composite Structures
**Chapter summary**: \
This chapter shows with composite structures several ways to represent internal structures of class. The internal structure diagram shows contained parts in a class and the relationships between them. These relationships apply only within the containing class, but not inter-class. Further, ports and interfaces (balls and lollipops) of a class are shown. Collaboration diagram shows objects working together, and indicates to some extent the design pattern. 

**Scope in book**: \
The composite structure is a more detailed representation of class, focusing less on the general sides of a class, and more on the relationships of class objects. The main diagrams for representing classes shall be class diagram (chapter 4 and 5) and object diagram (chapter 6).

---

## 12. Managing and Reusing Your System's Parts: Component Diagrams
**Chapter summary**: \
Component is building block of the software. It can range from a small class to a large subsystem. A component has provided and required interfaces, and ports. A delegation connector connects a component (required / provided) interface and an internal sub-component. An assembly connector connects two internal sub-components. A component can contain classes to implement its functionality. The used classes are said to realize a component.  

**Scope in book**: \
The component diagram is similar to the class in composite structure in chapter 11. However, the composite structure shows the logical view (with classes), while the component diagram shows the development view (with components).

---

## 13. Organizing Your Model: Packages
**Chapter summary**: \
Package is not a UML diagram, but a collection of classes (or sometimes use cases). It groups classes together, which serve same purpose, such as search, gui, security, etc. Packages can depend on other packages, for example a class in one package uses a class in another package. A package can also have "import" or "access" dependency to another package. 

**Scope in book**: \
Package can be used to include anything, and therefor can sometimes used interchangeably with component. However, the most common usage of package is to group classes together. This differentiates it from component, which can be realized by classes (see chapter 12). 

---

## 14. Modeling an Object's State: State Machine Diagrams
**Chapter summary**: \
State machine diagram shows the possible states and the transitions between the states. A state can be shown briefly with the name of the state, or in detail with internal behaviors and internal transitions (both in textual form). A transition can contain any combination (or none) of trigger, guard and behavior in form of ``trigger [guard] / behavior``. As unique point of UML, it allows multiple states at the same time in form of composite states, where the concurrent states are separated in regions.  

**Scope in book**: \
The state machine diagram belongs to the Logical view. It is somehow similar to the activity diagram, but differs from it in a way that it focuses on the stable states of the system, whereas the activity diagram (belongs to Process view) focuses on the steps / processes of the dynamic behavior.

---

## 15. Modeling Your Deployed System: Deployment Diagrams
**Chapter summary**: \
The deployment diagram shows the physical view of the system. The hardware (server, PC, disk drives) or software resource (OS, J2EE container, web server, application server) that can host software or related files are represented with nodes. Artifacts are physical files that execute or used by the software, and are deployed (shown) in corresponding nodes. The nodes can communicate with each other via communication path. 

**Scope in book**: \
Deployment diagram shows the physical environment of the software and the physical files. It represents therefore the touch point of the software with the real world. 

