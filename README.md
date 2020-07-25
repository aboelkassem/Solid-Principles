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
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/Voilatiing-Single-Responsibility-Principle.png" width="1000"/>

### Example 1 for <a href="https://github.com/ardalis/SolidSample/tree/SRP-START">the code here</a>:
Finding Responsibilities in one class that make the code difficult and longer to test one responsibility in isolation
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-pro.png" width="470" height ="350"/>
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-pro-2.png" width="470"  height ="350"/>
Solution after making them in different classes that now are easily tested
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-solu.png"/>
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-solu-2.png" width="470" height ="350"/>
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex2-solu-3.png" width="470" height ="350"/>

### Example 2:
- Problem:
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex1-pro.png"/>
- Solution: 
<img src="https://github.com/aboelkassem/Solid-Principles/blob/master/Screenshots/ex1-slou.png"/>
