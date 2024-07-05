# Book Summary – Software Architecture in Practice (4th Edition)

## General information
- Authors: Len Bass, Paul Clements, Rick Kazman
- Book rating on Goodreads: 3.86 (updated: July 5th, 2024) [page link](https://www.goodreads.com/book/show/58472161-software-architecture-in-practice)
- A distilled (and shorter) book summary is located at [Software Architecture in Practice – Distilled Summary](<Software Architecture in Practice – distilled summary.md>).
- Suprisingly, there are not so many summaries or reviews of the book out there.
    + LosTechnies.com ([page link](https://lostechies.com/evanhoff/2008/04/08/book-review-software-architecture-in-practice/)): Brief summary of the key take aways such as quality attributes, tactics, architecture evaluation, etc.
    + Community reviews on GoodReads (see GoodReads link above).

![cover image](<assets/Software Architecture in Practice - cover image.jpg>)

---

## Part I: Introduction
### 01. What is Software Architecture?
> We are called to be architectures of the future, not its victims. \
> ––– R. Buckminster Fuller

**Chapter summary**: 
- Software architecture is defined as the set of structures needed to reason about the system, comprising of software elements, relations among them, and properties of both. 
- The structures are divided into three categories: 
    + module structures (shows system code and data structure, e.g. decomposition, use, layer, class/generalization, data)
    + component-and-connector (C&C) structure (shows runtime behavior and interactions, e.g. service, concurrency)
    + allocation structure (shows relation of module and C&C structures to non-software structures, e.g. deployment, implementation, work assignment). 
- The three structures are related to each other, e.g. one module is manifested in several components in C&C structure. Mapping between structures are many to many. 

**Scope in book**: \
As first chapter, the definition of software architecture, and major structures are explained. 

---

### 02. Why is Software Architecture Important?
> Ah, to build, to build! That is the noblest art of all the arts. \
> ––– Henry Wadsworth Longfellow

**Chapter summary**: This chapter emphasizes the importance of software architecture. The main drivers for software architecture are achieving desired quality, enhancing communication among stakeholders, carrying important design decisions, providing constraints for implementations. 

**Scope in book**: \
This chapters listed 13 reasons for creating software architecture. These reasons are also the use cases / functions of a software architecture.


---

## Part II: Quality Attributes
### 03. Understanding Quality Attributes
> Quality is never an accident; it is always the result of high intention, sincere effort, intelligent direction and skillful execution. \
> ––– William A. Forster

**Chapter summary**: Functionality is independent of architecture, but is achieved by assigning responsibilities to architectural elements (module decomposition). This architecture (structure and behavior) serves mainly the goal of fulfilling the quality attributes. 
- As the tool to capture the quality attribute requirement, the quality attribute scenario is used, which consists of six parts (source of stimulus, stimulus, environment, artifact, response, response measure). 
- In order to achieve the quality attributes, architecture tactics and pattern are used. 
    + An architectural tactic is a design decision that affects the response of a single quality attribute. 
    + A architectural pattern is a bundle of tactics. 
- At the end of the chapter, the tactics-based questionnaires are introduced, which is used to shed light on the strengths and weaknesses of an architecture.  

**Scope in book**: \
This opening chapter of part II gives an overview of the quality attributes and the corresponding tool for in-depth analysis of them.

(Quality attribute scenario) \
![](<assets/Software Architecture in Practice - quality attribute scenario.png>)

---

### 04. Availability
> Technology does not always rhyme with perfection and reliability. Far from it in reality! \
> ––– Jean-Michel Jarre

**Chapter summary**: Availability is the ability of a system to mask or repair faults such that they do not become failures, ensuring the cumulative service outage does not exceeds specified time. 
- Availability subsumes reliability and robustness. A common availability expression is MTBF / (MTBF + MTTR). 
- The three major tactics for availability are detect faults, recover from faults, and prevent faults. 
- Major patterns for availability are redundancy (active / passive redundancy, spare), tripple modular redundancy (TMR), circuit breaker, roll back, and roll forward.  

**Scope in book**: \
Available is the first required property of a software. It is the foundation of the software functionalities and all other properties.

(Availablity tactics) \
![](<assets/Software Architecture in Practice - availability tactics.png>)

---

### 05. Deployability
> From the day we arrive on the planet \
> And blinking, step into the sun \
> There's more to be seen than ever be seen \
> More to do that can ever be done \
> ––– The Lion King

**Chapter summary**: Deployability is the property of a software for deployment (and being able to be rolled back if specifications are not met) within a predictable and acceptable amount of time and effort. 
- Deployability is strongly related to continuous development. 
- Two tactics for deployability are manage deployment pipeline (controls how to carry out deployment, incl. roll back) and manage deployed system (controls how the content of and the linkages between the deployed artifacts). 
- Corresponding to these tactics, two patterns are available, which are not independent. 
    + The first pattern is used for the deploy process, incl. complete (blue/green, rolling upgrade) or partial (canary testing, A/B testing) replacement of services. 
    + The second pattern (microservice architecture) structures services to be deployed. 

**Scope in book**: \
Deployability is the precondition of software maintenance and changes in execution environment. Therefore, this deployability is given a high priority in the quality attributes list.

(Deployability tactics) \
![](<assets/Software Architecture in Practice - deployability tactics.png>)

---

### 06. Energy Efficiency
> Energy is a bit like money: If you have a positive balance, you can distribute it in various ways, but according to the classical laws that were believed at the beginning of the century, you were't allowed to be overdrawn. \
> ––– Stephen Hawking

**Chapter summary**: Energy efficiency is getting more relevant in mobile and IoT contexts. 
- The major tactics for energy efficiency are monitor resources, allocate resources (assigning resources in a mindful way of energy consumption), and reduce resource demand (explicitly manage the demand). 
- Common patterns for energy efficiency are sensor fusion (combined usage of low- and high-power sensors), kill abnormal tasks, and power monitor (automatically disable devices and interfaces that are not actively used by application). 

**Scope in book**: \
Energy efficiency is a software property which isn't aware by most architects, but is critical to many software applications.

(Energy efficiency tactics) \
![](<assets/Software Architecture in Practice - energy efficiency tactics.png>)

---

### 07. Integrability
> Integration is a basic low of life; when we resist it, disintegration is the natural results, both inside and outside of us. Thus we come to the concept of harmony though integration. \
> ––– Norman Cousins

**Chapter summary**: Integrability is about discerning and bridging the distance between the elements for each potential dependency, which is related to the property of modifiability. 
- Integrability is affected by the size (number of potential dependencies) and distance (difficulty of resolving differences) between the interfaces. There are five types of distances: syntactic, data semantic, behavioral semantic, temporal, and resource distances. 
- Major tactics for integrability are limit dependencies (encapsulate, use intermediary, etc.), adapt (discover, tailor interface, etc.), and coordinate (orchestrate, etc.). 
- Useful patterns include wrappers / bridges / mediators, service-oriented architecture pattern, and dynamic discovery. 

**Scope in book**: \
Integrability is an indicator for the dependency, and therefore a pre-condition for the modifiability, and is also related to deployability.

(Integrability tactics) \
![](<assets/Software Architecture in Practice - integrability tactics.png>)

---

### 08. Modifiability
> It is not the strongest of the species that survive, nor the most intelligent, but the one most responsive to change. \
> ––– Charles Darwin

**Chapter summary**: Modifiability is about change with the target to lower the cost and risk of making changes. Specific flavors of modifiability are scalability, variability, portability, and location independence. 
- The tactics for modifiability address the four key factors in software changes: coupling, cohesion, size of module, and binding time of modification. The major tactics are increase cohesion, reducing coupling, and defer binding. 
- Useful patterns for modifiability include client-server pattern, plug-in (microkernel) pattern, layers pattern, publish-subscribe pattern. 

**Scope in book**: \
Modifiability addresses the inevitable changes of software and how to reduce the effort. It overlaps to some extent with the integrability, while the latter focuses on changes due to adding elements from external and how the existing software can absorb them. On the other side, modifiability has a broader meaning. 

(Modifiability tactics) \
![](<assets/Software Architecture in Practice - modifiability tactics.png>)

---

### 09. Performance
> An ounce of performance is worth pounds of promises. \
> ––– Mae West

**Chapter summary**: Performance is the software system's ability to meet timing requirements. Performance is often linked to scalability and modifiability. 
- Major tactics are divided into two categories: control resource demand (incl. manage work requests, prioritize events, increase efficiency of resource usage {"better programming"} etc.) and manage resources (incl. increase resources, introduce concurrency, schedule resources, etc.). 
- Common patterns for performance include service mesh, load balancer, throttling, and map-reduce. 

**Scope in book**: \
Performance is for many people the most obvious property of a software, since it is what the software shows toward outside. The real problem behind a performance issue may be elsewhere and related to other properties though.

(Performance tactics) \
![](<assets/Software Architecture in Practice - performance tactics.png>)

---

### 10. Safety
> Giles: Well, for god's sake, be careful ... If you should be hurt or killed, shall take it amiss. \
> Willow: Well, we try not to get killed. That's part of our whole mission statement: Don't get killed.  \
> Giles: Good. \
> ––– Buffy the Vampire Slayer, Season 3, episode "Anne"

**Chapter summary**: Safety is a system's ability to avoid straying into states that cause or lead to damage, injury, or loss of life to actors in its environment. 
- During architecture work for safety, it should begin with identifying system's safety-critical functions using FMEA and FTA. For each failure identified, mechanisms to detect and mitigate the faults should be designed. 
- Safety is strongly related to availability (chap. 4). Therefore the tactics and patterns of these two properties are similar. 
- Common tactics for safety are categorized into four groups: unsafe state avoidance, unsafe state detection, containment (limit the harm associated with an unsafe state), and recovery. 
- Major patterns are redundant sensors, monitor-actuator (additional monitor conducts redundant checks on actuator controller computations), separated safety (divide system into safety-relevant and non-safety-relevant portions).  

**Scope in book**: \
Safety is strongly related to availability.

(Safety tactics) \
![](<assets/Software Architecture in Practice - safety tactics.png>)

---

### 11. Security
> If you reveal your secrets to the wind, you should not blame the wind for revealing them to the trees. \
> ––– Kahlil Gibran

**Chapter summary**: Security is the system's ability to protect data and information from unauthorized access while still providing access to people and systems that are authorized. It is therefore strongly related to privacy. 
- Security is characterized with CIA (confidentiality, integrity, availability). 
- The tactics are categorized into four groups: detect, resist, react, and recover. 
- Major patterns for security include intercepting validator (verifying message), and intrusion prevention system (looking for suspicious pattern of overall usage, not only anomalous messages). 

**Scope in book**: \
Security is linked with availability (e.g. due to service-of-denial attach) and usability. 

(Security tactics) \
![](<assets/Software Architecture in Practice - security tactics.png>)

---

### 12. Testability
> Testing leads to failure, and failure leads to understanding. \
> ––– Burt Rutan

**Chapter summary**: Testability refers to the ease with which software can be make to demonstrate its faults through testing. Increasing the testability of a software can significantly reduce the cost. 
- Tactics for testability are categorized into two groups: add controllability and observability ("control and observe system state", incl. specialized interfaces, record/playback, executable assertions, etc.), and limit complexity in system's design (incl. limit structural complexity, limit nondeterminism). 
- Three patterns are described for testability: dependency injection, strategy pattern, and intercepting filter. 

**Scope in book**: \
Testability is the outwards expression of the software's behavior (with the focus of fault detection). It is therefore related to modifiability, since modification needs to be done after a fault is detected and the root cause of it is analyzed. Further, a simpler structure that is beneficial for testability makes it also easy to modify the software.

(Testability tactics) \
![](<assets/Software Architecture in Practice - testability tactics.png>)

---

### 13. Usability
> People ignore design that ignores people. \
> ––– Frank Chimero

**Chapter summary**: Usability refers to how easy it is for the user to accomplish a desired task and the kind of user support that the system provide. 
- Human-computer interactions can be sorted into three types: user initiative (e.g. click cancel button), system initiative (e.g. shows progress bar), and mixed initiative. 
- The tactics are therefore categorized to two groups: support user initiative (incl. cancel, undo, pause/resume, aggregate) and support system initiative (incl. maintain task / user / system model). 
- Common patterns for usability include model-view-controller (MVC, separating logic from user interface), observer (link functionality with more views), and momento pattern (create snapshot of system's existing state to implement undo). 

**Scope in book**: \
Usability is strongly related to modifiability, since the user interface design process is iterative and requires multiple modifications based on feedbacks.

(Usability tactics) \
![](<assets/Software Architecture in Practice - usability tactics.png>)

---

### 14. Working with Other Quality Attributes
> Quality is not what happens when what you do matches your intentions. It is what happens when what you do matches your customers' expectations. \
> ––– Guaspari

**Chapter summary**: This chapter introduces several other quality attributes (beside the ones in chap. 4-13), such as buildability, conceptual integrity, development distributability. 
- With all these quality attributes, it is emphasized that even though software architecture has huge impact on the system quality, the system itself shall always considered a boundary condition at designing the software architecture (e.g. no weather forecasting on Grandpa's laptop). 
- A quality attribute list can never be complete. Therefore, it is important to have own list, which is most suitable for own system targets. In this context, if we are facing new quality attribute, it is recommended to create quality scenario, model, and corresponding design approaches for it. 

**Scope in book**: \
This chapter gives recommendations for quality attributes on a higher level, emphasizing not rely on any fixed quality attribute list, but focusing on the targets of own system.

---

## Part III: Architectural Solutions
### 15. Software Interfaces
> NASA lost its $125-million Mars Climate Orbiter because spacecraft engineers failed to convert from English to metric measurements when exchanging vital data before the craft was launched ... \
> In a sense, the spacecraft was lost in translation. \
> ––– Robert Lee Hotz, "Mars Probe Lost Due to Simple Math Error", Los Angeles Times, October 1, 1999

**Chapter summary**: An interface is a boundary across which elements meet and interact. 
- All elements have interfaces, which are two-way (provided and required) and can evolve with the time. 
- The resources represent the direct interaction points with an element, and can be seen as part of the element's interface. Resources of provided interfaces consist of operations, events, and properties. Resources have syntax and semantics. 
- At designing an interface, several aspects need attention: interfaces scope (defines the collection of available resources to actors), interaction style (e.g. RPC, REST), representation and structure of the exchanged data (coverts between internal and external representation, e.g. XML, JSON, binary), and error handling. 
- The importance of documenting the interface is addressed at the end of chapter. 

**Scope in book**: \
Interfaces are the visible parts of a system for the actors and define the contract for the interactions between the system and its environment. 

---

### 16. Virtualization
> Virtual means never knowing where your next byte is coming from. \
> ––– Unknown

**Chapter summary**: The main goal of virtualization is to reach high utilization of resources (CPU, memory, disk storage, network connection) by sharing them among different applications. 
- With hypervisor, multiple virtual machines (VM) can run in a single physical computer. The hypervisor – an operating system for VM – is responsible for managing the code in each VM, and managing the VM themselves. It requires that the VM uses the same instruction set as the underlying physical CPU. 
- Two types of hypervisor are available: bare-metal / Type 1 hypervisor is typically used in data center or cloud, while hosted / Type 2 hypervisor runs as a service on top of a host OS, and is used on desktop or laptop computers. 
- Each VM can run almost any OS, inside which multiple services can run. 
- Containers are more compact as VM. They require however a container runtime engine to run, which acts as a virtualized OS and controls the services in the container. 
- At the end of the chapter, the serverless architecture is introduced, where the fast allocation of container is utilized by reallocating a new container instance within a VM to process every request and exiting it when complete. 

**Scope in book**: \
Virtualization is sometimes required at designing an architecture. This chapter gives an overview of the most important terms and the tradeoffs.

(Bare-metal / Type 1 hypervisor) \
![](<assets/Software Architecture in Practice - bare metal (type 1) hypervisor.png>)

(Hosted / Type 2 hypervisor) \
![](<assets/Software Architecture in Practice - hosted (type 2) hypervisor.png>)

---

### 17. The Cloud and Distributed Computing
> A distributed system is one in which the failure of a computer you didn't even know existed can render your own computer unusable. \
> ––– Leslie Lamport

**Chapter summary**: Cloud computing is about the on-demand availability of resources. 
- At creating a request for a new VM instance in the cloud, the cloud region, the instance type (CPU, memory), and the VM image ID are configured and sent via the management gateway. The management gateway identifies a hypervisor with enough CPU and memory capacity, and returns the IP and host name of the allocated VM. 
- Several potential issues must be dealt with in cloud computing, including latency (e.g. time out), high request load, time and data coordination in distributed system. Common solutions include load balancers, which distribute the requests between the service (VM) instances. 
- New service instances can be created or deleted dynamically using autoscaler, which coordinates the creation and deletion based on resource (CPU, memory) utilization. With the multiple instances of service, it is recommended to keep the services stateless, allowing easier recovery from failure and addition of new instances.  

**Scope in book**: \
Cloud computing bases on the virtualization technology and utilizes VMs and containers (chap. 16). It is characterized by the distribution of the large number of service instances, and therefore requires its own architectural tactics.

---

### 18. Mobile Systems
> The telephone will be used to inform people that a telegram has been sent. \
> ––– Alexander Graham Bell

**Chapter summary**: A mobile system must deliver some or all its functionality in movement. Typical mobile systems are phones, trains, planes, and automobiles. 
- Five major characteristics are discussed in this chapter: energy, network connectivity, sensors and actuators, resources, and life cycle. 
- Energy management of mobile system requires power source monitoring, throttling energy usage, and tolerating loss of power. 
- Wireless Networks connectivity concerns include communication interfaces to support, transitions between protocols, bandwidth, limited connectivity, and security. 
- For sensors and actuators, an architect shall consider the data reading, smoothing, converting, and fusion. 
- Resource choices affect volume, weight, and cost. Considerations must be made regarding task assignment, offloading functionality to cloud, functions shut down in proper mode, and information displaying. 
- Life-cycle concerns include choice of hardware, testing, deploying updates, and logging. 

**Scope in book**: \
Mobile system as a special kind requires specific consideration at architecture design. The measures to ensure the software quality are different than for the non-mobile systems.

---

## Part IV: Scalable Architecture Practices

### 19. Architecturally Significant Requirements
> The most important single aspect of software development is to be clear about what you are trying to build. \
> ––– Bjarne Stroustrup, creator of C++

**Chapter summary**: An ASR is a requirement that has a profound effect on the architecture and a high business or mission value. 
- ASR can be extracted from requirements document (although the most information in a requirement specification is not QA requirements and therefore does not affect the architecture), from stakeholders workshop (e.g. QAW, Quality Attribute Workshop), and from business goals. 
- The extracted ASRs shall be captured in a utility tree, which contains the major QAs for the system. Each QA is then further refined (e.g. performance → data latency, transaction throughput, etc.). Under each refinement, the specific ASRs are expressed as QA scenarios and then evaluated with business value and technical risk. 
- Attention shall be paid to the changes of the requirements and business goals. 

**Scope in book**: \
ASR concretizes the QAs to understandable and traceable QA scenarios, and gives them priorities. Therefore, this chapter shows the practical way to organize and achieve the QAs (in Part II) in alignment with the stakeholders, requirements documents, and business goals. 

---

### 20. Designing an Architecture
> A designer knows he has achieved perfection not when there is nothing left to add, but when there is nothing left to take away. \
> ––– Antoine de Saint-Exupéry

**Chapter summary**: The Attribute-Driven Design (ADD) is described in detail in this chapter. The ADD consists of 7 steps: 1) review inputs 2) establish iteration goal by selecting drivers 3) choose one or more elements of the system to refine 4) choose one or more design concepts that satisfy the selected drivers 5) instantiate architectural elements, allocate responsibilities, and define interfaces 6) sketch views and record design decisions 7) perform analysis of current design and review iteration goal and achievement of design purpose.  

**Scope in book**: \
In step 4), the introduced tactics and patterns of the QAs (Part II) shall be taken into consideration to select the best suitable concept. This step is related to the module structure (chap. 1). Step 5) is related more to the component-and-connector structure (chap. 1). 

(Attribute-Driven Design (ADD) steps) \
![](<assets/Software Architecture in Practice - Attribute-Driven Design (ADD).png>)

---

### 21. Evaluating an Architecture
> A doctor can bury his mistakes, but an architect can only advise his clients to plant vines. \
> ––– Frank Lloyd Wright

**Chapter summary**: Architecture evaluation is a process of determining the degree to which an architecture is fit for the purpose for which it is intended. The evaluation is comparable to insurance policy – one has to weigh the cost of the evaluation itself and the cost of undiscovered risks. 
- An evaluation includes four activities: reviewers understand the architecture → reviewers determine the drivers to guide the review (typically in form of high-priority quality attribute scenarios) → for each scenario, each reviewer determine whether the scenario is satisfied → reviewers capture potential problems exposed during the prior step. 
- The ATAM method is described in detail, which is used for comprehensive evaluation. 
- For project-internal evaluation on regular basis, the LAE (Lightweight Architecture Evaluation) can be used, which can be completed in a day. 

**Scope in book**: \
Architecture evaluation comes hand in hand with the design, and provides a way to predict the quality attributes of the system before building it. The evaluation is based on the ASRs (in the form of QA scenarios) and the documentation of the architecture, to detect any mismatch between the architectural approach / decisions and the QAs.

---

### 22. Documenting an Architecture
> Documentation is a love letter you write to your future self. \
> ––– Damian Conway

**Chapter summary**: Architecture documentation serves multiple purposes, including as means of education, as a vehicle for communication with and among stakeholders, as basis for system analysis and construction, and as basis for forensics at incident. 
- Static architectural structure is documented with views. Four views are introduced in this chapter, which are: 
    + module view (module responsibilities of and relations between modules, incl. is-part-of / depends-on / is-a)
    + C&C view (runtime components and their interactions, such as "attachments")
    + allocation view (mapping of software units to environment with the relation of "allocated-to")
    + quality view (for specific QAs). 
- Behavior documentation complements the views and describes how architecture elements interact with each other. The behavior can be documented either trace-oriented (incl. use cases, sequence diagram, communication diagram, activity diagram) or comprehensive (incl. state machine). 
- In addition to the views and behavior, further information such as mapping between views, used patterns, variability guide, rationale, glossary etc. shall also be documented. 
- At presenting the architecture to the stakeholders, the proper documentation type shall be selected according to interest. 
- At end of the chapter, several practical suggestions for documentation such as high architectural dynamism, traceability, are given. 

**Scope in book**: \
Documentation tracks the decisions during the whole architecture design process and shall be an integral part of this process.

---

### 23. Managing Architecture Debt
> Some debts are fun when you are acquiring them, but non are fun when you set about retiring them. \
> ––– Ogden Nash

**Chapter summary**: Architecture debt is caused by high coupling and low cohesion, which are represented by high static dependencies and evolutionary dependency. 
- The DSM (Design Structure Matrix) method visualizes the dependencies with thee inputs: source code, revision history (to detect co-evolution of code units), and issue information (to determine reason for changes). Each row in DSM represents a file with entries in the row to show the dependencies. 
- An architecture with low debt shall have sparse matrix, and lower diagonal (entries appear below the diagonal). Further, time of the co-evolution between two structurally independent files shall be low. 
- Using the DSM, anti-patterns (hotspots) can be identified, including unstable interface, modularity violation, unhealthy inheritance, cyclic dependency or clique, package cycle, and crossing. The architecture debt of these identified anti-patterns can be quantified and to determine whether a refactoring is necessary.  

**Scope in book**: \
While the architecture evaluation (chap. 21) focuses on the quality attributes, this chapter concentrates on the dependencies between the components (files). It is therefore a subset of the QAs, most related to modifiability. 

---

## Part V: Architecture and the Organization

### 24. The Role of Architects in Projects
> I don't know why people hire architects and then tell them what to do. \
> ––– Frank Gehry

**Chapter summary**: Software architect is responsible for the internal technical aspects of a project, and supports the project manager at external-facing aspects. A good working relationship between the software architect and the project manager is vital. 
- The "Iteration 0" approach is a good choice for the architecture work in agile environment. The first architectural increment should include module decomposition structure, module "uses" structure, and a preliminary C&C structure. The release tempo and content of each increment shall be aligned with stakeholders. 
- For a distributed development (team not co-located), the allocation of responsibilities to teams is more important than in a traditional co-located development, considering module dependencies, proper documentation, and communication in project.  

**Scope in book**: \
This chapter deals with aspects more on the non-technical side, including project management, agile development, and organization, which have impacts on the software (architecture) development. 

---

### 25. Architecture Competence
> The lyf so short, the craft so long to lerne. \
> ––– Geoffrey Chaucer

**Chapter summary**: The competence of a software architect consists of duties (e.g. "design the architecture"), skills (e.g. "ability to think abstractly"), and knowledge (e.g. "patterns and tactics"). The way to improve the competence includes gain experience at carrying out the duties, improve non-technical skills (e.g. leadership, time management, communication), and master the body of knowledge. Being mentored and mentoring others are recommended ways to become a better architect. At the end of the chapter, the competence of a software architecture organization is also discussed, which includes also the aspects of duty, skill, and knowledge. 

**Scope in book**: \
This chapter puts the architecture in a broader context and gives software architect and corresponding organizations valuable recommendations for competence improvement.

---

## Part VI: Conclusions

### 26. A Glimpse of the Future: Quantum Computing
> (A quantum computer can be compared) to the airplane the Wright brothers flew at Kitty Hawk in 1903. The Wright Flyer barely got off the ground, but it foretold a revolution. \
> ––– wired.com

**Chapter summary**: Quantum computing is currently in infancy, however, it will reshape the future of software. Many aspects will be disrupted such as programming language, networking, security, etc. All these have profound impacts on the software architecture.  

**Scope in book**: \
This chapter raises the potential challenge caused by quantum computing. It reminds the importance of keeping the same pace with the technology development and reflect for own work.
