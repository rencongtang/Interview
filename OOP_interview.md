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

## Explain what is static and what can it do
At first, we need to agree that the RAM for computers are limited, we need to save it as much as possible
### Static value
A static value will make this value only take a part of RAM space. If there is something needs to use this value or function, it will never need extra spaces. But if this value is not a static, every time it will occupy a space
Let's make an example to make it cleaner
In a restaurant, there is only one salt pot, every time if someone wants to add salt in his soup, he only need to call it. It same as the program, every time the program needs a static value, it only need to call it in RAM
But without static, that means the program needs to generate a number of customers with salt, if there is no body, there is also not salt pot. But each person with the salt pot will also make the waste of resource.
And here is a code exam to make you understand it better:
```
class Customer()
{
    static public string salt;
    public string pepper;

    public static void main(String[] args)
    {
        //If I want to use a 

    }
}
```

### Static method
If a method be declared by static, this method can be directly used, otherwise you need to initialize an object at first
An example like this:
```
public class XX()
{
    public static void method1(){}
    public void method2(){}
    public static void main(String[] args)
    {
        // I can directly use method1
        method1();
        // But I need to initial an object to use method2
        XX x = new XX();
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

## What is Encapsulation?
This is an attribute of an object, it contains all the hidden data inside an object. The hidden data can be restricted to the members of the class
There are 4 levels of encapsulation:
* Public 
* Private
* Protect: subclasses can also access the data
* Internal: classes inside this package can access 

## Inheritance:
Class can share the structure and behavior to it's subclasses. 

## Manipulation
In C# like string Manipulation(I have no idea why this question)

## What is abstract class
This class at first cannot be instantiated. It can be inherited and it only contains abstract method.

## What is Interface 
Interface contains only the declarations of the methods, properties and events. What we should notice is these functions should not be implemented.
