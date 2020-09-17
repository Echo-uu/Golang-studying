## UP

### UP discipline

* business modeling : domain model , visualize the important conception
* requirements : use case and supplementary
* design : design software objects

### UP  Phase

* Inception
* elaboration
* construction
* transition

## Evolutionary requirements

### FURPS+ 

(the  types and categories of requirements)

* functional
* usability
* reliability
* performance
* supportability
* +
  * Implementation
  * interface
  * operation
  * packaging
  * legal



## Use case

### Guideline

* essential UI-Free style
* terse (简洁)
* Black-Box
* Actor and actor's goal

### Test for use case

* Boss test 
* EBP test : 基本业务过程
* Size test

### Relationship

* **include**
* extensive
* generation



## Diagram and model

* use case diagram
* sequence diagram
* system sequence diagram SSD
  * actors generates **system events**, handle by the **system operation**
* package diagram
  * use to describe the logic architecture of system
* activity diagram : shows sequential and parallel activities in a process
  * it  can shows both control flow and data flow(DFD)
  * usually used to visualize the business work flows and process, and use-case
* state diagram
  * illustrates the interesting events and states of an object, and the behavior of an object in reaction to an event.

### Domain model

* conceptual perspective
  * domain objects or conceptual class
  * the association between conceptual class
  * the attributes of conceptual class
* association : represents meaningful and concerned connection
* super class and sub class

### Operation contract

* defined for the system operation

### Class diagram

(static object diagram) **DCD** : design class diagram

* the differences between domain model ![image-20200809160132844](C:\Users\Echo-\AppData\Roaming\Typora\typora-user-images\image-20200809160132844.png)
* relationship between class
  * generalization
  * dependency
  * Interface
  * aggregation and composition
  * association (qualified and )
* singleton
* template class and interface
* active class
* the relation of interaction
  * the information of interaction diagram represents the operation of the class diagram
  * the identified class in the interaction diagram should be declared in class diagram 

* **interaction (collaboration) diagram**

  to illustrate how objects interact via messages (dynamic object modeling)

  * sequence diagram
    * frame : loop , alt  (互斥) , opt
    *  relate interaction diagram : **ref** , **sd** 
  * communication diagram
  * interaction overview diagram

## Logic architecture

from software classes into packages(or namespaces), subsystems, and layers.



### Layered architecture

* cohesive Responsibility and separation of concerns



## GRASP and GoF



### GRASP pattern

* Creator : B contains/aggregate | records | use directly | initial data of A
* Controller : different scenario has controller to accept and handle issue
* Pure Fabrication : a set of high cohesion responsibilities
* Information Expert : to the class which has the essential information
* High Cohesion
* Indirection : avoid direct coupling m using the intermediate object 
* Low Coupling
* Polymorphism : assign responsibility for the behavior using polymorphic operations to the types for which the behavior varies
* Protected Variations : create a stable interface



### GoF

* **Adapter** : use intermediate adapter object to convert the original interface of a component into another interface to resolve incompatible interfaces or provide a stable interface to similar components with different interfaces
* **Factory** : create factory (pure fabrication obj) to handle create responsibility. (return type is interface)
* **Singleton** : define the static method of the class to implement global visibility and single point of access
* **Strategy** : define each algorithm/policy/strategy in separately class which have the same interface.
* **Composition** : define composition and atomic object class which implements the same interface
* **Façade** : define a single point of contact to the subsystem a façade object that wraps the subsystem. This façade object presents a single unified interface and is responsible for collaborating with the subsystem components.（对一组完全不同的接口或实现如子系统，需要一个统一的接口）（对子系统定义一个唯一的接触点，使用façade封装子系统，façade提供唯一和统一的接口，负责与子系统构建合作）
* **Observer/Publish-Subscribe** : define "subscriber" or "listener" interface. Subscriber implements the interface. Publisher can dynamically register subscribers who are interested in an event and notify them when an event occurs (想要对发布者产生事件时以自己独特的方式做出反应)
* **Proxy** : add a level of indirection with a surrogate proxy object that implements the same interface as the subject, and is responsibility for controlling or enhancing access to it.



### Relationship

* composition
* Aggregation
* generalization and specialization
* association
  * qualified association
  * reflexive association



* Why do we model
  * visualize a system
  * give us a template for constructing a system
  * documents our decisions



### 4+1 Views

* logical view
* process view
* data view
* deployment view 
* use-case view

## Others

### Visibility of objects

* attributes : B is the attributes of A
* parameters : B is the parameter of the method in A
* local : B is the local object of the method in A
* global : B is in some way globally visible



### Development 

* test-driven
  * refactoring
* risk-driven
* client-driven
* data_driven
* responsibility-driven **RDD**(GRASP)





