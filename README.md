# OOAE-Notes


Singleton

It is a creational design pattern. (A process of object creation)

Only one instance from each server needs to be created.
If more than one object is created, a problem will occur.

Problem;
When a user writes code on the file, it will get overwritten from a previous user.

Intent;
Having an object in between will allow different users to access different files without their
files being overwritten. This will create a global point of access for users.

Motivation;
It is important for some classes to have exactly one instance. Although, there can be many printers in a 
system, there should be only one printer spooler. How do we ensure that a class has only one instance and 
that the instance is easily accessible?

1) Declaring a private constructor

e.g.
Student student1 = new Student();

The new function is used to trigger the constructor.
Constructors need to be made public in order to trigger different objects.

Structure of a Singleton Pattern

-static instance : Singleton
This is the Singleton Instance

+static getInstance(): Singleton
This returns the unique instance

#Singleton() <<constructor>>
This is a protected constructor (if it has sub-classes)
If no sub-classes are present, it can be a private constructor.


public class Singleton()
{
    private static Singleton uniqueInstance;
// A Static variable is created to hold one instance of the Singleton Class.

	private Singleton () {}
// A private constructor is declared, therefore only one Singleton can instantiate this class.
	
	public Singleton getInstance()
	{
//The getInstance() method gives a way to instantiate the class and also to return an instance of it.

	if (uniqueInstance == null) 
	{
	uniqueInstance = new Singleton();
	}

		return uniqueInstance;
	}

}


Implementation;

Synchronized 
// By adding this keyword to getInstance, we force every thread to wait its turn before it can enter
the method. That is, no two threads may enter the method at the same time.

e.g.
public static synchronized Singleton getInstance ()
{
	if (uniqueInstance == null) 
	{
	uniqueInstance = new Singleton();
	}

		return uniqueInstance;
	}

}

Advantage;
This solves the issues in multi-threading by using double locking.

Drawback;
Performance is decreased when synchronized is used to instantiate.


Eagerly Created Instance;

public class Singleton
{
	private static Singleton uniqueInstance = new Singleton();
//Creates an instance of Singleton in a static intializer. This code makes the thread safe.
	
	private Singleton () {}

	public static Singleton getInstance();
	{
	return uniqueInstance;
	}
}


Coupleton is when the Singleton code is modified to return more than one instance.
