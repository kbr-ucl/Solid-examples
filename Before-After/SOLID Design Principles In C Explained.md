## [SOLID Principles Explained Using C#](https://www.scholarhat.com/tutorial/designpatterns/solid-design-principles-explained)

**SOLID principles** are essential concepts in object-oriented programming and design, particularly in [C#](https://www.scholarhat.com/tutorial/csharp). These principles help developers create better manageable, intelligible, and flexible software systems. By following **SOLID principles**, you may improve code quality while lowering the risk of introducing errors.

In this [Design Patterns tutorial](https://www.scholarhat.com/tutorial/designpatterns/), we will discuss the **SOLID Principles in C#**, which include the following: **What are the SOLID Principles?** And **when should they be used?** We'll also go over instances of each SOLID principle in C#. So, let us begin by examining **what SOLID Principles are.**

## Why Do We Need to Learn SOLID Design Principles?

-   As developers, we frequently begin designing applications with our previous expertise and knowledge.
-   However, in time, these apps may grow prone to bugs.
-   Each change request or new feature could involve changes to the app's appearance.
-   Even simple activities may demand tremendous effort and an overall understanding of the system.
-   It is critical to understand that change requests and new features are inherent in software development; they cannot be denied.
-   The actual issue is with the application's design. Poor design might make the system more complex and challenging to maintain and update.

To address the issues raised above and to help students, beginners, and professional software developers learn how to create robust software using **SOLID principles in C#**, I've chosen to launch a series of articles on SOLID creation Principles. These articles will offer real-world examples to help readers understand the material and learn quickly.

## What are the main reasons for most unsuccessful applications?

**The following are the fundamental causes for most Unsuccessful applications:**

-   **Overloading Classes with Functionalities:** We frequently add too many functionalities to a class, even if they are not linked. This creates large and ungainly courses that are difficult to manage.
-   **Tight Coupling Between Software Components:** When classes are closely connected and rely significantly on one another, changes to one class can have a cascading effect, affecting other classes and making the system fragile and challenging to adjust.

## How to Avoid Unsuccessful Application Development Problems?

**To achieve successful application development, we must consider the following critical factors:**

-   **Use the Appropriate Architecture:** Choose the appropriate architectural pattern (e.g., MVC, Layered, 3-tier, MVP) that best meets the project's requirements. This decision has far-reaching implications for the application's scalability, maintainability, and structure.
-   **Follow Design concepts:** Stick to recognized design concepts like SOLID and ONION. These principles lay the groundwork for building clean, maintainable, and scalable code.
-   **Choose the Right Design Patterns:** Use the design patterns that are suited to the project's requirements. These include creational patterns (e.g., factory, singleton), structural patterns (e.g., adapter, composite), behavioral patterns (e.g., observer, strategy), dependency injection, and repository patterns. Correct application of these patterns can solve common design issues and improve code quality.

## What are solid principles?

-   The **SOLID design principles** serve as the framework for dealing with common software design difficulties that arise in daily development.
-   These concepts have been demonstrated to be effective in developing software that is clear, versatile, and maintained.

**Let’s discuss each principle with code examples.**

### 1\. Single Responsibility Principle (SRP)

-   In C#, the **Single Responsibility Principle (SRP**) suggests that a class should only have one cause to change, i.e., one task or responsibility.
-   This idea makes code more maintainable, intelligible, and versatile by requiring that each class handle a single functionality or problem.

#### Example

**Before applying for SRP**

```java
public class UserService { public void RegisterUser(User user) { // Logic to register user } public void SendWelcomeEmail(User user) { // Logic to send a welcome email } }
```

#### Explanation

In this case, UserService is responsible for both enrolling users and delivering emails, which are two distinct tasks.

**After Applying SRP**

```java
public class UserService { private readonly EmailService _emailService; public UserService(EmailService emailService) { _emailService = emailService; } public void RegisterUser(User user) { // Logic to register user _emailService.SendWelcomeEmail(user); } } public class EmailService { public void SendWelcomeEmail(User user) { // Logic to send a welcome email } }
```

#### Explanation

In this code, the UserService class handles user registration and delegated email sending to the EmailService class, following the **Single Responsibility Principle (SRP)**. This separation of responsibilities ensures that UserService concentrates entirely on user-related duties, whereas EmailService handles email operations.

[![](https://dotnettrickscloud.blob.core.windows.net/uploads/adsImages/softwarearchitecttraining-ads20240516084159.png)](https://www.scholarhat.com/training/software-architecture-design-training?utm_source=scholarhat&utm_medium=banner&utm_campaign=https://www.scholarhat.com/tutorial/designpatterns/solid-design-principles-explained)

### 2\. Open Closed Principle (OCP)

-   The **Open/Closed Principle (OCP)** of C# specifies that a class should be available for extension but closed for modification.
-   This means that you should be able to add new functionality or behavior to a class without changing the old code, which is often accomplished through interfaces, abstract classes, and inheritance.
-   OCP helps to construct maintainable and scalable systems by limiting changes to current code when new features are implemented.

#### Example

**Before applying for OCP**

```csharp
public class Account { public decimal Interest { get; set; } public decimal Balance { get; set; } // members and function declaration public decimal CalcInterest(string accType) { if (accType == "Regular") // savings { Interest = (Balance * 4) / 100; if (Balance < 1000) Interest -= (Balance * 2) / 100; if (Balance < 50000) Interest += (Balance * 4) / 100; } else if (accType == "Salary") // salary savings { Interest = (Balance * 5) / 100; } else if (accType == "Corporate") // Corporate { Interest = (Balance * 3) / 100; } return Interest; } }
```

#### Explanation

Before using the **Open/Closed Principle (OCP)**, the CalcInterest function of the Account class calculates interest using conditional logic based on account type. This approach necessitates updating the method whenever a new account type or interest calculation rule is implemented, making the class less adaptable and more difficult to maintain.

**After applying OCP**

```csharp
interface IAccount { // members and function declaration, properties decimal Balance { get; set; } decimal CalcInterest(); } //regular savings account public class RegularSavingAccount : IAccount { public decimal Balance { get; set; } = 0; public decimal CalcInterest() { decimal Interest = (Balance * 4) / 100; if (Balance < 1000) Interest -= (Balance * 2) / 100; if (Balance < 50000) Interest += (Balance * 4) / 100; return Interest; } } //Salary savings account public class SalarySavingAccount : IAccount { public decimal Balance { get; set; } = 0; public decimal CalcInterest() { decimal Interest = (Balance * 5) / 100; return Interest; } } //Corporate Account public class CorporateAccount : IAccount { public decimal Balance { get; set; } = 0; public decimal CalcInterest() { decimal Interest = (Balance * 3) / 100; return Interest; } }
```

#### Explanation

After implementing the **Open/Closed Principle (OCP)**, the Account class is refactored into an IAccount interface with numerous implementations for various account kinds. Each account type (RegularSavingAccount, SalarySavingAccount, and CorporateAccount) now implements the CalcInterest method individually, allowing new account types to be introduced without altering old code, hence increasing flexibility and maintenance.

### 3\. Liskov Substitution Principle (LSP)

-   The Liskov Substitution Principle (LSP) argues that objects of a superclass should be interchangeable with objects of a subclass without affecting the program's validity.
-   In other words, subclasses must increase the functionality of the parent class while maintaining its behavior, guaranteeing that derived classes can be used interchangeably with their base class without introducing unanticipated problems.
-   This idea contributes to a consistent and trustworthy interface.

#### Example

**Before applying LSP**

```csharp
namespace Demo { public class Program { static void Main(string[] args) { Triangle triangle = new Circle(); Console.WriteLine(triangle.GetColor()); } } public class Triangle { public virtual string GetShape() { return "Triangle"; } } public class Circle: Triangle { public override string GetShape() { return "Circle"; } } }
```

#### Explanation

Before using the Liskov Substitution Principle (LSP), the code mistakenly replaces a Triangle object with a Circle. The Circle class is derived from Triangle, but the GetShape method's functionality changes in a way that violates LSP because a Circle cannot be substituted for a Triangle without changing the program's intended behavior.

**After applying LSP**

```csharp
namespace Demo { class Program { static void Main(string[] args) { Shape shape = new Circle(); Console.WriteLine(shape.GetShape()); shape = new Triangle (); Console.WriteLine(shape.GetShape()); } } public abstract class Shape { public abstract string GetShape(); } public class Triangle: Shape { public override string GetShape() { return "Triangle"; } } public class Circle: Triangle { public override string GetShape() { return "Circle"; } } }
```

#### Explanation

After implementing the Liskov Substitution Principle (LSP), the Shape abstract class defines the GetShape method, which both the Triangle and Circle classes inherit. This enables the Shape reference to hold objects from either subclass without affecting the program's validity, ensuring that Triangle and Circle can be used interchangeably while retaining consistent behavior.

### 4\. Interface Segregation Principle (ISP)

-   The Interface Segregation Principle (ISP) argues that no client should be compelled to rely on methods that it does not use.
-   This entails creating small, particular interfaces rather than one huge, general-purpose interface.
-   ISP contributes to a more modular and maintainable codebase in which clients only implement the capabilities they require.

#### Example

**Before applying ISP**

```csharp
public interface IOrder
```

#### Explanation

Before using the Interface Segregation Principle (ISP), the IOrder interface mandates both the OnlineOrder and OfflineOrder classes to implement methods that they do not require. OfflineOrder is specifically necessary to use the CCProcess technique for credit card processing, which is not applicable to offline orders. This generates extra and perhaps error-prone code because OfflineOrder throws a NotImplementedException for the CCProcess method.

**After applying ISP**

```csharp
public interface IOrder { void AddToCart(); } public interface IOnlineOrder { void CCProcess(); } public class OnlineOrder : IOrder, IOnlineOrder { public void AddToCart() { //Do Add to Cart } public void CCProcess() { //process through credit card } } public class OfflineOrder : IOrder { public void AddToCart() { //Do Add to Cart } }
```

#### Explanation

After implementing the Interface Segregation Principle (ISP), the IOrder interface only has the AddToCart method, but the IOnlineOrder interface is designed for credit card processing. This allows OnlineOrder to implement both interfaces while OfflineOrder just implements IOrder, guaranteeing that each class relies on the functions it requires.

### 5\. Dependency Inversion Principle (DIP)

-   The Dependency Inversion Principle (DIP) suggests that high-level modules should not rely on low-level modules but on abstractions.
-   Furthermore, abstractions should not be dependent on details but rather the reverse.
-   This principle encourages decoupling by ensuring that code is based on interfaces or abstract classes, which improves flexibility and maintenance.

#### Example

**Before applying DIP**

```java
using System; namespace Demo { public interface IAutomobile { void Ignition(); void Stop(); } public class Jeep : IAutomobile { public void Ignition() { Console.WriteLine("Jeep start"); } public void Stop() { Console.WriteLine("Jeep stopped."); } } public class SUV : IAutomobile { public void Ignition() { Console.WriteLine("SUV start"); } public void Stop() { Console.WriteLine("SUV stopped."); } } public class AutomobileController { private Jeep _jeep; public AutomobileController(Jeep jeep) { _jeep = jeep; } public void Ignition() { _jeep.Ignition(); } public void Stop() { _jeep.Stop(); } } class Program { static void Main(string[] args) { Jeep jeep = new Jeep(); AutomobileController automobileController = new AutomobileController(jeep); automobileController.Ignition(); automobileController.Stop(); Console.Read(); } } }
```

#### Explanation

Before using the Dependency Inversion Principle (DIP), the AutomobileController class was tightly tied to the Jeep class, rendering it rigid and unable to function with other vehicle types, such as SUVs, without altering the controller itself. This direct reliance on a specific implementation violates DIP, limiting the system's extensibility and maintainability.

**After applying DIP**

```java
using System; namespace Demo { public interface IAutomobile { void Ignition(); void Stop(); } public class Jeep : IAutomobile { public void Ignition() { Console.WriteLine("Jeep start"); } public void Stop() { Console.WriteLine("Jeep stopped."); } } public class SUV : IAutomobile { public void Ignition() { Console.WriteLine("SUV start"); } public void Stop() { Console.WriteLine("SUV stopped."); } } public class AutomobileController { private readonly IAutomobile _automobile; public AutomobileController(IAutomobile automobile) { _automobile = automobile; } public void Ignition() { _automobile.Ignition(); } public void Stop() { _automobile.Stop(); } } class Program { static void Main(string[] args) { IAutomobile jeep = new Jeep(); AutomobileController automobileController = new AutomobileController(jeep); automobileController.Ignition(); automobileController.Stop(); IAutomobile suv = new SUV(); automobileController = new AutomobileController(suv); automobileController.Ignition(); automobileController.Stop(); Console.Read(); } } }
```

#### Explanation

After applying the **Dependency Inversion Principle (DIP)**, the AutomobileController class depends on the IAutomobile interface rather than a specific implementation like Jeep. This allows the controller to work with any IAutomobile implementation, such as Jeep or SUV, making the system more flexible, extensible, and easier to maintain.

##### Summary

The **SOLID principles** of Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, and Dependency Inversion are critical for developing stable and scalable [C#](https://www.scholarhat.com/tutorial/csharp) systems. They help developers build software with clear roles, expandability without modification, interchangeable components, focused interfaces, and decoupled dependencies, resulting in resilient and flexible codebases. Also, consider our [.NET design patterns training](https://www.scholarhat.com/course/dot-net-design-patterns-course) for a better understanding of other design patterns concepts.

## FAQs

### Q1. What is the purpose of SOLID principles in C#?

The SOLID principles in C# seek to improve code maintainability, scalability, and flexibility by encouraging good design practices and decreasing dependencies.

### Q2. What is the SOLID principle in MVC?

MVC follows the "S" of the SOLID principles by separating responsibilities. The model includes state information. The view includes items that interact with the user. The controller ensures that the sequence of steps is followed correctly.

### Q3. What are the SOLID principles every developer must know?

Every developer should be familiar with the SOLID concepts of single responsibility, open/closed, Liskov substitution, interface segregation, and dependency inversion.

### Q4. What is the distinction between SOLID principles and design patterns in C#?

Design patterns are proven solutions for recurring situations. Design principles are recommendations that might assist you in structuring and constructing your software. That's all. You do not have to use every pattern and concept that exists.