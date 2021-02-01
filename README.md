# Table of Contents
  - [Single Responsibility Principle (SRP)](#single-responsibility-principle-srp)
  - [Open/Closed Principle (OCP)](#openclosed-principle-ocp)
  - [Liskov Substitution Principle (LSP)](#liskov-substitution-principle-lsp)
  - [Interface Segregation Principle (ISP)](#interface-segregation-principle-isp)
  - [Dependency Inversion Principle (DIP)](#dependency-inversion-principle-dip)
  - [Organizing and extending SOLID Principles into your project](#organizing-and-extending-solid-principles-into-your-project)
  
# Solid-Principles
**SOLID** principles are the design principles that enable us manage most of the software design problems promoted by Robert C. Martin and introduced by Michael Feathers.

it is a mnemonic acronym. It helps to define the five basic object-oriented design principles to make software designs more understandable, flexible and maintainable:

1. **S**ingle Responsibility Principle
2. **O**pen-Closed Principle
3. **L**iskov Substitution Principle
4. **I**nterface Segregation Principle
5. **D**ependency Inversion Principle

<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/solid.png"/>

## Single Responsibility Principle (SRP)

- The Code/Class/Method "do one thing and do it well"
- Uncle Bob, "There should never be more than one reason for a class to change"
- A Class or method Should have one and only one reason to change, Meaning that a class should have only one job or responsible for one part of the functionality

### Examples of responsibilities of the application
<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/responsiblities.png" width="300" hight="300"/>
</p>
<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/Voilatiing-Single-Responsibility-Principle.png" width="500" hight="500"/>
</p>


### Example 1 for <a href="https://github.com/ardalis/SolidSample/tree/SRP-START">the code here</a>:
Finding Responsibilities in one class that make the code difficult and longer to test one responsibility in isolation
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-pro.png" width="50%" height ="350"/>
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-pro-2.png" width="49%" height ="350"/>
Solution after making them in different classes that now are easily tested
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-solu.png"/>
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-solu-2.png" width="50%" height ="350"/>
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-solu-3.png" width="49%" height ="350"/>

### Example 2:
- Problem:
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex1-pro.png"/>
- Solution: 
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex1-slou.png"/>


## Open/Closed Principle (OCP)
- Software entities(modules, classes, methods) should be open for extension, but closed for modification.
- any new functionality should be done by adding new classes instead of changing existing one

### Why Should Code be closed to modification ?

- Less Likely to introduce bugs in code we don't touch
- Less Likely to break dependent code when we don't have to deploy updates
- Fewer conditionals in code that is open to extension results in simpler code
- All the attributes and behaviors are encapsulated
- Proven to be stable within your system
- Bug Fixes are ok

`closed`does not mean that changes cannot be made to a class during **development**. It happens  when most of the design decisions have been **finalized** and once you have implemented **most of your system.**

### How can you predict future changes
- start concrete and modify the code the first time or two
- by the third modification, consider making the code open to extension for that axis of change

### How to Implement OCP
- adding new functionality to derived class (abstract class)
- or allow client to access the original class with abstract interface

### 1- Abstract Class
- first make the base class that contain original method abstract class and make the method abstract method don't have implementation,
- Create class/classes inherit from this abstract class to do these abstract method in different functionality .... so now it's close for modifications and open for extension new methods
<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-abstract.png" width="500" hight="500"/>
</p>

### 2- Interface
- Create an interface contains the common method that want to adding new functionality to it
- Create class/classes implement this interface to do the different functionality for this method
<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-interface.png" width="500" hight="500"/>
</p>

### Other Typical Approaches to OCP
- 1- Parameters
- 2- Inheritance
- 3- Composition/ Injection

Applying these approaches to this simple code
```csharp
public class DoOneThing 
{
	public void Execute()
	{
		Console.WriteLine("Hello World.");
	}
}
```
| Parameters | Inheritance | Composition/ Injection |
| ------------- | ------------- | ------------- |
![](https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-parameter.png)  |  ![](https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-inherit.png) | ![](https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-inject.png)

### Example OCP in Packages and Libraries in NuGet or NPM
using extension methods in C# like [this example](https://github.com/ardalis/guardclauses)
<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-packages.png" width="500" hight="500"/>
</p>

## Liskov Substitution Principle (LSP)
- if you have class **B** inherit from class **A** then class **A** should be replaceable by class **B** without any changes/ problems
- LSP Is a Subset of Polymorphism
<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/lsp.png" width="300" hight="300"/>
</p>

### How to Apply LSP
- Make the method in base class is **virtual**
- to override this method while used in derived class when create object
### Example

```csharp
namespace SOLID_PRINCIPLES.LSP
{
    class Program
    {
        static void Main(string[] args)
        {
            Fruit fruit = new Orange();
            Console.WriteLine(fruit.GetColor());
            fruit = new Apple();
            Console.WriteLine(fruit.GetColor());
        }
    }
    public abstract class Fruit
    {
        public abstract string GetColor();
    }
    public class Apple : Fruit
    {
        public override string GetColor()
        {
            return "Red";
        }
    }
    public class Orange : Fruit
    {
        public override string GetColor()
        {
            return "Orange";
        }
    }
}
```

### Detecting LSP Violations in your code
- Type Checking with **is** or **as** in polymorphic code
```csharp
foreach(var employee in employees)
{
   if(employee is Manager)
   {
     Helpers.PrintManager(employee as Manager);
     break;
   }
   Helpers.PrintEmployee(employee);
}
```
- null checks
```csharp
foreach(var employee in employees)
{
   if(employee == null)
   {
     Console.WriteLine("Employee not found.");
     break;
   }
   Helpers.PrintEmployee(employee);
}
```
- NotImplementException in interface implementation 

### Detecting LSP Violations in your code
- Follow the <a href="https://martinfowler.com/bliki/TellDontAsk.html">"Tell, Don't Ask"</a> Principle
- Minimize null checks with
	- c# features
	- Guard clauses
	- Null Object Design Pattern
- Follow ISP and be sure to fully implement interfaces

## Interface Segregation Principle (ISP)
- uncle bob said "Clients should not be forced to depend on methods they do not use"
- Many client-specific interfaces are better than one general-purpose interface.
    - avoid fat interface so prefer small
- Client must not implement unnecessary methods

> The Interface Segregation Principle states that any classes that implement an interface, should not have "dummy" implementations. Instead you should split large interfaces into smaller generalizations.
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/isp.png"/>

### Detecting ISP Violations in your code
- Large Interfaces
- NotImplementedException
- Code uses just small subset of a larger interface

### Fixing ISP Violations
- Split interface Up into smaller ones and if you need use multiple interface inheritance

### Example 1
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/isp-ex1.png"/>

### Example 2
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/isp-ex2.png"/>
<p float="left">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/isp-ex2-1.png" width="49%" height ="50%"/>
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/isp-ex2-2.png" width="49%" height ="50%"/> 
</p>

## Dependency Inversion Principle (DIP)
The principle states that high level modules should depend on high level generalizations, and not on low level details. This mean your class should depend in Interface or Abstract class not concrete class. Interfaces and Abstract classes are high level resources. A concrete class is a low level resource. 

- High Level Modules should not depend upon Low Level Modules. Both should depend upon abstractions.
    - abstractions should not depend on details
    - details should depend on abstractions
    ![](https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/dpi.png)
- Applying this principle would make your code loosely coupling and highly cohesive (don't depend on low level classes)
- **High level Module** is the module has business rules, more abstract, process-oriented, further from (I/O) while **Low Level Module** is closer to (I/O) and interacts with specific external systems and hardware (keep plumbing code separate from high level business logic)
- **Low Level Dependencies** like **Database, File system, Email, Web APIs, Configuration** and **Clock**
- This principle name "Dependency Inversion" for studying in a book , but in actual coding called "dependency injection" like in [asp.net](http://asp.net) core that is completely depend on it and follow it
- **dependency injection (DI)** say don't create your own dependencies instead you should depend on abstractions and request that dependencies from client. there are three method on how to apply that
    - Constructor arguments (Prefer one because it's follow [explicit dependencies principle](https://docs.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/architectural-principles))
    - Properties injection
    - Method Constructor
- Like this design/problem that causes pain like tight coupling, low cohesive, difficult to isolate and unit test and duplicate the code
    ![](https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/dpi-ex1.png)
- but the solution would be :
    ![](https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/dpi-ex1-sol.png)
    ![](https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/dpi-dep.png)
    
So instead of the following diagram that implement low level concrete class/details which it consume a lot of work if there are any changes.
<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/DIP-1.png" width="300" hight="300"/>
</p>
Applying DIP to depend on High Level Generalization will be become like this
<p align="center" width="100%">
  <img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/DIP-2.png" width="500" hight="500"/>
</p>
This means that the Client is depended on expected behaviors (high level), not on a specific implementation (low level).

## Least Knowledge Principle (Law of Demeter)

This principle states that **classes should know about and interact with as few other classes as possible**. Not every other class of the system. It reduce coupling and provide stability to your systems.

According to this design principle a method `M` of and object should only call other methods if they are:

- Encapsulated within the same object
- Encapsulated within an object that is in the parameters of `M`
- Encapsulated within an object that is instantiated inside of `M`
- Encapsulated within an object that is referenced in an instance variable of the class for `M`

All this rules of this law mean ⇒ **that a method should not invoke methods of any object that is not local.** Don't call objects that you shouldn't know about or unknown type of object don't exist into your class.

**Returned objects** from methods must be of the same type as:

- Those declared in the method parameter
- Those declared and instantiated locally in the method.
- Those declared in instance variables of the class that encapsulates the method.

Classes should know as little as possible about your system as a whole to reduce the amount of coupling and prevent unwanted effects from cascading through your entire system

## Organizing and extending SOLID Principles into your project
cause following all these principles would need to many files that focus in more classes and interfaces so do the following technique for avoid that problem by
- **Use Folders!**
    - several folders with each folder has few classes/interfaces
    - each folder should be specific in it's task by naming them appropriately, it should be pretty easy to find what you're looking
    - default way is by **kind of thing the file** is, so might put controllers in one folder, models in another, folder for interfaces and another for services ... etc
    - another way specially when app is grow, is to use **feature folders** by organize your app with feature not kind of thing like in online store might have top-level folders for catalog, search and cart instead of controllers, models, views and services...... also follow [this repo](https://github.com/ardalis/CleanArchitecture)
