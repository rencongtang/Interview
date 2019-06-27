# OOP interviews
## 1. What is OOP?
OOP stands for the Object Oriented Programming. The programs are considered as a collection of Objects. Each object is an instance of class.

## 2. 4 basic concepts of OOP
* Abstraction
* Encapsulation
* Inheritance
* Polymorphism

## 3. What is Abstraction?
Object with abstraction means the *internal implement details* are hidden.
For example, if you want to have personal information about a patient, you don't need some unnecessary information like pet's name. You fetch information from a pool of information, this approach called abstraction. 

However, the information can be used for different applications, the patient information can also be used for job application and government database. The information can also be slightly modified. Hence it become master data (the basic of further data for different applications). This is the advantage of Abstraction.

## 4. What is Polymorphism?

The word Polymorphism means multi forms, the child class gets the overwrite fields(also be called variables) and functions. That means this function or field can be used in the different situations by class inheritance. The child class object can be assigned to any class reference in its parent hierarchy and itself.

Here is a simple example, in the summer, it makes room cool down and in winter, it makes the room cold
```
Student student = new Student()
Person person = new Student()
``` 

So the conclusion like this, with polymorphism, the subclass can change only the method if there is an override, but will not change any other fields in the super class.
But we need to notice that if there is a static method, the method can not be changed. And if we force to change AirCondition class (summer) to SummerAC class, all the fields and methods will be SummerAC's

Extra Information:

Here are 2 kinds of Polymorphisms:


### Dynamic Polymorphism (it is different in C#)

This is also mentioned as *Run-Time polymorphism, Dynamic binding, Run-Time binding, Late binding and Method overriding*.

Let's think about the override of a method. When an object is assigned to a class reference and when a method of the object is called, the method execute depend on the object rather than the reference class (if the reference class is a parent class). But the properties are following reference.

### For java
Here is an example to explain:
```
class AirCondition()
{
    int temperature = 30;
    public void ChangeTemp()
    {
        Print("I have no idea what to do")
    }
}

class SummerAC: AirCondition()
{
    int temperature = 40;
    public void ChangeTemp()
    {
        Print("room is cooler");
    }
}

AirCondition ac = new AirCondition();
AirCondition another_ac = new SummerAC();
SummerAC summer_ac = new SummerAC();

// Here you can see even we use AirCondition as reference, but the execute used object (SummerAC) method
Print(another_ac.ChangeTemp); // output is "room is cooler"

AirCondition summer = new SummerAC()
// will print room is cooler  
summer.ChangeTemp();
// it's still 30, and will not be changed
Print(summer.temperature )
AirCondition ac = new AirCondition()
// Will print I have no idea what to do
sc.ChangeTemp();
```
### For C#, you need to mention virtual and override before method

```
class AirCondition()
{
    int temperature = 30;
    public virtual void ChangeTemp()
    {
        Print("I have no idea what to do")
    }
}

class SummerAC: AirCondition()
{
    int temperature = 40;
    public void ChangeTemp()
    {
        Print("room is cooler");
    }
}

class SummerAC_Override: AirCondition()
{
   int temperature = 40;
    public override void ChangeTemp()
    {
        Print("room is cooler");
    }
}

AirCondition ac = new AirCondition();
AirCondition another_ac = new SummerAC();
AirCondition another_ac_override();
SummerAC summer_ac = new SummerAC();

// Here you can see even we use AirCondition as reference, but the execute used object (SummerAC) method
Print(another_ac.ChangeTemp()); // output is "I have no idea what to do"
Print(another_ac_override.ChangeTemp()); // output is "room is cooler"
```


### Static Polymorphism
This is also mentioned as * Compile-Time polymorphism, Static binding, Compile-Time binding, Early binding and Method overloading. * 

Everything you need to know it is overloading. Same method name but different parameter and return type can also be different.

## 5. What is Encapsulation?

This is an attribute of an object, it contains all the hidden data inside an object. The hidden data can be restricted to the members of the class.
There are 4 levels of encapsulation access modifiers:
* Public 
* Private
* Protect: subclasses can also access the data
* Internal: classes inside this package can access 

## 6. Inheritance:
Class can share the structure and behavior to it's subclasses. 

## 7. Explain what is static and what can it do
At first, we need to agree that the RAM for computers are limited, we need to save it as much as possible.
### Static value
A static value will make this value only take a part of RAM space. If there is something needs to use this value or function, it will never need extra spaces. But if this value is not a static, every time it will occupy a space when you use it.
Let's make an example to make it cleaner
In a restaurant, there is only one salt pot, every time if someone wants to add salt in his soup, he only need to call it. It same as the program, every time the program needs a static value, it only need to call it in RAM.
But without static, that means the program needs to generate a number of customers with salt, if there is no body, there is also not salt pot. But each person with the salt pot will also make the waste of resource.


And here is a code exam to make you understand it better:
```
class Customer()
{
    static public string salt;
    public string pepper;

    public static void main(String[] args)
    {
        // If I want to use a pepper pot 
        Customer c1 = new Customer();
        c1.pepper = "pepper";
        Customer c2 = new Customer();
        c2.pepper = "pepper";

        // If I want to use a salt
        Customer.salt = "salt";

    }
}
```

### Static method
If a method be declared by static, this method can be directly used, otherwise you need to initialize an object at first
An example like this:
```
public class Test()
{
    public static void method1(){}
    public void method2(){}
    public static void main(String[] args)
    {
        // I can directly use method1
        method1();
        // But I need to initial an object to use method2
        Test x = new Test();
        x.method2();
    }
}

```
### Static Class
A static class cannot be instantiated, you can directly call the function inside it without instantiated. The most popular static class is Math in .net
As other static examples, a static constructor will be only called once

And a static class should: 

* Contains only static members.

* Cannot be instantiated.

* Is sealed.

* Cannot contain Instance Constructors.

## 8. What is the difference between Abstract and Interface

### What is abstract class
This class at first cannot be instantiated. A static class may have static fields and static methods. When the abstract class is inherited, the subclass usually provides implementations for all the abstract methods in its parent class. If not, the subclass must be declared abstract.

You can use abstract class for these usage:

* You want to share code among several closely related classes
* You expect that classes that extend the abstract class have many common methods and fields or require access modifiers other than public(*protected and private*)
* You want to declare non-static and non-finial fields. This enables you to define methods that can access and modify the state of the object. 

### What is Interface 
Interface contains only the declarations of the methods, properties and events. What we should notice is these functions should not be implemented. We define what kind of operation an object can perform. These operations are defined by the class that implement the interface.

You can use interface for these usage:
* You expect that unrelated classes would implement your interface. For example, the interfaces Comparable and Cloneable are implemented by many unrelated classes.
* You want to specify the behavior of a particular data type, but not concerned about who implements its behavior.
* You want to take advantage of multiple inheritances.

### What is the difference 
* Method: Interface can not have implementations. Abstract class can have instance methods that implements a default behavior.
* Variables: in Java interface is default final(can only initialed once). 
* Members if interface are public by default.
* In java a class can only extend one interface, but can extend multiple abstract classes.
* Abstract class can be invoked if a main() method exists. BTW: both interface and abstract classes cannot be instantiated.
* Interfaces are slow because it requires extra indirection.

## 9. What is the difference between out and ref (C#)

### Ref
Same as out, ref passes arguments by reference. It means any changes made to this argument in the method will be reflected in the variable when control returns to the calling method. The ref parameter does not pass the property.
```
class GFG { 
  
    // Main Method 
    public static void Main() 
    { 
  
        // Assign string value 
        string str = "Geek"; // Need to initial in the beginning
  
        // Pass as a reference parameter 
        SetValue(ref str); // Hello!!Geek
  
        // Display the given string 
        Console.WriteLine(str); //GeekforGeeks
    } 
  
    static void SetValue(ref string str1) 
    { 
  
        // Check parameter value 
        if (str1 == "Geek") { 
            Console.WriteLine("Hello!!Geek"); 
        } 
  
        // Assign the new value 
        // of the parameter 
        str1 = "GeeksforGeeks"; 
    } 
} 

```

### Out
*Out* is a C# keyword for *passing the arguments* to methods as a *reference type*. It us generally used when a method returns multiple values. The out parameter does not pass the property. 

Here is an example:
```
class GFG{
    static public void Main()
    {
        int G; 
        sum(out G);
        Console.WriteLine("the sum of the value is: {0}", G); // the sum if the value is: 2;
    }

    public static void Sum(out int G)
    {
        G = 1; //Initial 
        G += G;
    }
}

```

### Difference
|Ref|Out|
|----------------------------|----------------------------|
|Parameter should be initialed outside the function(Initial parameter outside function)|Not necessary to initial|
|Not necessary to initialize the value of a parameter before returning to the calling method|Need to initial parameter before returning to calling method(Initial parameter inside function)|
|Useful when method need to change value of passed parameter|When wants to return multiple values|
|Data pass in bi-directional|Data only pass in unidirectional|



## 10. What is manipulators?(C++)

Functions specifically designed to be used in conjunction with the insertion (<<) and extraction(>>)

## 11. What is constructor?
Have the same name as class it is a method to initial the state of an object. It gets invoked when the object is created. What we should notice is the constructor should not return any type.
The constructor in C# like:
```
public class Model
{
    public Model() {}
}
```

## 12. What is destructor?
This function is automatically called when the object is made of scope (out of scope) or destroyed. You need to use tilde (~) operator for destructor.
```
public class Model
{
    public User() 
    {
        Console.WriteLine("An instance of class created");
    }
    ~User() 
    {
        Console.WriteLine("An instance of class destroyed");
    }
}

Class Program
{
    static void Details()
    {
        User user = new User();//Created instance of class
        // use the garbage collector and automatically invoke a destructor
        GC.Collect();// instance be destroyed 
    }
}
``` 

## 13. What is inline function?
It seems this term only be used in C++. 
It is a technique used by the compilers and instructs to insert completed body of the function wherever that function is used in the program source code. (I don't know what it is talking about)

## 14. What is a virtual function?
It is a function in class which stands it can be overridden in its derived class. This function can be implemented by using a keyword called virtual and it can be given during function declaration.

```
class AirCondition()
{
    int temperature = 30;
    public virtual void ChangeTemp()
    {
        Print("I have no idea what to do")
    }
}

class SummerAC: AirCondition()
{
    int temperature = 40;
    public void ChangeTemp()
    {
        Print("room is cooler");
    }
}

class SummerAC_Override: AirCondition()
{
   int temperature = 40;
    public override void ChangeTemp()
    {
        Print("room is cooler");
    }
}

AirCondition ac = new AirCondition();
AirCondition another_ac = new SummerAC();
AirCondition another_ac_override();
SummerAC summer_ac = new SummerAC();

// Here you can see even we use AirCondition as reference, but the execute used object (SummerAC) method
Print(another_ac.ChangeTemp()); // output is "I have no idea what to do"
Print(another_ac_override.ChangeTemp()); // output is "room is cooler"
```
## 15. What is friend function
A friend function is a friend of a class that is allowed to access to Public, private or protected data in that same class. If the function is defined outside of this class, this function cannot access such information.

A friend can be declared anywhere in the class declaration and it cannot be affected by access control keywords like private, public or protect.

## 16. What is ternary operator
The ternary opera is used for condition judgement. It takes 3 arguments. The first argument is a comparison argument, the second is the result upon a true comparison and the third is the result upon false comparison.

```
condition ? value_if_true : value_if_false
```

## 17. What is the use of finalize method
This function is called by garbage collector when the garbage collection decide there are no more reference to the object. A subclass override the finalize method to dispose of system resources or to perform other cleanup.

```
ObjectDemo obj = new ObjectDemo();
//when finish use this object

obj.finalize();
```

## 18. What is the different types of arguments
### Parameter
A variable used during declaration of the function or subroutine
### Arguments
The variables passed to the function body and should match with parameter defined.

There are 2 Type of arguments:
* Call by value will get modified only inside the functions and returns the same value whatever it is passed to the function. That is because the value is copied in the function.
```
int num1 = 5;
public void ChangeValue(int i)
{
    i = 10;
}

ChangeValue(num1);
Console.WriteLine(num1); // 5
```
* Called by reference will get modified in both inside and outside the functions and it returns the same or different value.
If we define a class and it is a reference class 
```
public class User
{
    public int UserID
    {
        get;
        set;
    }
    public string Name
    {
        get;
        set;
    }
}
User obj = new User()
{
    UserID = 1, Name = "Jack"
}

public void ChangeName(User user)
{
    user.Name = "Joker";
}

ChangeName(obj);
Console.WriteLine(obj.Name); // gives Joker
```

## 19. What is super keyword?
To access the data members of parent class when both parent and child class member have the same name. You need to use the *super* key word to to access variable in parent class.

Let's have a look at an example to understand super keyword better:

```
class Superclass
{
    int num = 10;
}

class Subclass: Superclass
{
    int num = 110;
    void printNumber()
    {
        Console.WriteLine(num);
    }
}

Subclass obj = new Subclass();
obj.printNumber(); // print 110 as result.
```

And if the developer wants to get the variable from parent, they need to use the syntax like this:

```
super.variable_name
```

And let's have a look at the same example, but this time we want to pass the num from parent class

```
class Superclass
{
    int num = 10;
}

class Subclass: Superclass
{
    int num = 110;
    void printNumber()
    {
        Console.WriteLine(super.num);
    }
}

Subclass obj = new Subclass();
obj.printNumber(); // the result is 10, because it used the variable of parent class
```

## 20. What is exception handling?
It is an event during the program execution. It could be runtime exception, Error exception. These exceptions need to be handled through exception handling mechanism like this:
```
try
{
    // what you want to execute
}
catch(Exception e){

}
```

Or you need to use try-catch-finally. The purpose to use catch and finally is to obtain and use resources in a try block. The exceptional circumstances is in the catch block, and release the resources in finally block.
```
public class EHClass
{
    void ReadFile(int index)
    {
        string path = @"c:\users\public\test.txt";
        StreamReader file = new StreamReader(path);
        try
        {
            file.ReadBlock(buffer, index, buffer.Length)
        }
        catch (Exception e)
        {
            Console.WriteLine(e);
        }
        finally
        {
            // to release file 
            if(file != null)
                file.Close();
        }
    }
}
```

## 21. What are tokens?
Tokens are various program elements which are identified by the compiler. A token is the smallest element of a program that is meaningful to the compiler.

Keywords, variables, constants, special characters, operations are regarded as token.

## 22. How do you explain sealed modifiers

Sealed modifier are the access modifiers where the methods cannot inherit it. Sealed modifiers can also be applied to properties, events and methods. This modifier cannot be used for *static* members.

```
class X
{
    protected virtual void F(){}
    protected virtual void F2(){}
}

class Y:X
{
    sealed protected override void F(){}
    protected override void F2(){}
}

class Z:Y
{
    // Cannot override F because it is sealed
    // protected virtual void F(){}

    // Overriding F2 is allowed
    protected virtual void F2(){}
}

```

# 23. Explain what is base keyword

The base keyword is to access members of base class from within a derived class:
+ Call a method on the base class that has been overridden by another method.
+ Specify which base-class constructor should be called when creating instances of the derived class

A base class access is permitted only in a *constructor*, an *instance method* or an *instance property* accessor.

But the base keyword should not be used with in a static method.
The base class that is accessed is the base class specified in the class declaration. For example, if you specify class ClassB : ClassA. By using the base keyword, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.

```
public class BaseClass
{
    int num;

    public BaseClass()
    {
        Console.WriteLine("in BaseClass()");
    }

    public BaseClass(int i)
    {
        num = i;
        Console.WriteLine("in BaseClass(int i)");
    }

    public int GetNum()
    {
        return num;
    }
}

public class DerivedClass : BaseClass
{
    // This constructor will call BaseClass.BaseClass()
    public DerivedClass() : base()
    {
    }

    // This constructor will call BaseClass.BaseClass(int i)
    public DerivedClass(int i) : base(i)
    {
    }

    static void Main()
    {
        DerivedClass md = new DerivedClass();
        DerivedClass md1 = new DerivedClass(1);
    }
}
/*
Output:
in BaseClass()
in BaseClass(int i)
*/
```

```
public class Person
{
    protected string ssn = "444-55-6666";
    protected string name = "John L. Malgraine";

    public virtual void GetInfo()
    {
        Console.WriteLine("Name: {0}", name);
        Console.WriteLine("SSN: {0}", ssn);
    }
}
class Employee : Person
{
    public string id = "ABC567EFG";
    public override void GetInfo()
    {
        // Calling the base class GetInfo method:
        base.GetInfo();
        Console.WriteLine("Employee ID: {0}", id);
    }
}

class TestClass
{
    static void Main()
    {
        Employee E = new Employee();
        E.GetInfo();
    }
}
/*
Output
Name: John L. Malgraine
SSN: 444-55-6666
Employee ID: ABC567EFG
*/
```


### What's the difference between super and base?
Super is used in Java, and Base is used in C#

## 24. What is the difference between new and override?

The difference between override and new is the *override* extend the method of base class with a new definition.
However the *new* keyword hides the method of base class. This could be important for different class deliver.  

```
class BaseClass
{
    public void ShowHello()
    {
        Console.WriteLine("Hello from base");
    }
    public virtual void ShowWelcome()
    {
        Console.WriteLine("Welcome from base");
    }
}

class DerivedClass:BaseClass
{
    public new void ShowHello()
    {
        Console.WriteLine("Hello from derived");
    }

    public override void ShowWelcome()
    {
        Console.WriteLine("Welcome from derived");
    }
}

BaseClass dc = new DeliverClass();
dc.ShowHello(); // Hello from base;
dc.ShowWelcome(); // Welcome from derived 
```