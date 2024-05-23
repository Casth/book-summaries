# Book Key Points - Software Architecture in Practice

This key points summary is created based on [Software Architecture in Practice – full summary](<Software Architecture in Practice – full summary.md>).

---

## Part I: Introduction
Part I sheds light on the meaning and importance of software architecture. A software architecture is the set of software elements, the relations between them, and the properties of both. The architectural structures are categorized into three groups: module structure, component-and-connector structure, and allocation structure. The three structure categories have m:n relation to each other. Software architecture is an important vehicle for achieving software quality, enhancing communication, providing constraints for implementations.

---

## Part II: Quality Attributes
Functionality is independent of architecture, but can only be achieved by assigning responsibilities to architectural elements (module decomposition). The architecture (structure and behavior) serves mainly the goal of fulfilling the quality attributes. Quality attribute scenario (source of stimulus, stimulus, environment, artifact, response, response measure) is used to capture the quality attribute requirement. Architectural tactics and patterns are used to achieve the quality attributes. 10 different quality attributes (availability, deployability, energy efficiency, integrability, modifiability, performance, safety, security, testability, usability) are described in detail, explaining their architectural tactics and patterns. There are strong and weak linkages between the introduced quality attributes. Beyond these 10 quality attributes, further attributes are also existing. The list of quality attributes shall be suitable for the specific system targets. 

---

## Part III: Architectural Solutions
Software interfaces are the boundary between a software element with others, and shape the interactions of it with its actors. The software interface controls the resources (operations / events / properties, all have syntax and semantics) that belong to the interface. The scope, interaction style, representation of the exchanged data, and error handling must be taken into consideration at designing interfaces. Virtualization means to increase the utilization of hardware resources, such as CPU, memory, network connection. The most common way for virtualization is the hypervisor, which is an operating system for VMs (Virtual Machines). Two types of hypervisor (bare-metal, hosted) are available. Container is another way of virtualization, which requires the container runtime engine. Using the virtualization, cloud and distributed computing are realized, where multiple VMs with desired OS (and multiple containers within a VM) are instantiated on a single server. CPU, memory and other resources are distributed by the hypervisor between the VMs. In contrary to cloud solution, mobile systems deliver their functionality in movement. Therefore, energy consumption, network connectivity, sensors and actuators, resources, and life cycle of these systems must be paid more attention to.

---

## Part IV: Scalable Architecture Practices
An architectural significant requirement (ASR) is a requirement that has a profound effect on the architecture and a high business or mission value. ASRs shall be extracted from requirement documents, stakeholder workshops, and business goals. They are then captured in utility tree, with major quality attributes (QAs), their refined sub-attributes, corresponding QA scenarios, as well as rated business value and technical risk. Architecture design based on Attribute-Driven Design (ADD) takes the functional requirements, design constraints, and QA requirements as input. Based on the QA requirements, the suitable tactics and patterns (implementation) for one architecture element are selected and evaluated against the input (as architectural drivers). ATAM (Architecture Tradeoff Analysis Method), LAE (Lightweight Architecture Evaluation) and further methods are used to evaluate the designed architectures. Architecture documentation serves multiple purposes (education, communication, analysis, construction). Static architectural structure is documented with views (module, C&C, allocation, quality view), while behavior is documented trace-oriented (use cases, sequence diagram, communication diagram, activity diagram) or comprehensive (state machine). The mapping between views, rationales, glossary and further documentations are also important. DSM (Design Structure Matrix) as a type of documentation visualizes the architecture debt and shows necessity for refactoring.

---

## Part V: Architecture and the Organization
An architect has duties, skills and knowledge. Experiences and technical skills are gained from the duties. Non-technical skills also important, such as communication, leadership, time management, incremental development. The body of knowledge shall be mastered. Mentoring others and being mentored are good ways to improve the competences. Architects shall support the project manager for internal technical aspects. 

---

## Part VI: Conclusions
Quantum computing will shape the future of software regarding programming language, networking, security, etc.

