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
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/responsiblities.png"/>
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/Voilatiing-Single-Responsibility-Principle.png" width="100%"/>

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
- Bug Fixes are ok

### How can you predict future changes
- start concrete and modify the code the first time or two
- by the third modification, consider making the code open to extension for that axis of change

### How to Implement OCP
- adding new functionality to derived class (abstract class)
- or allow client to access the original class with abstract interface

### 1- Abstract Class
- first make the base class that contain original method abstract class and make the method abstract method don't have implementation,
- Create class/classes inherit from this abstract class to do these abstract method in different functionality .... so now it's close for modifications and open for extension new methods
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-abstract.png"/>

### 2- Interface
- Create an interface contains the common method that want to adding new functionality to it
- Create class/classes implement this interface to do the different functionality for this method
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-interface.png"/>

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
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ocp-packages.png"/>

