* (The this Reference): The `this` reference is valid only within nonstatic members of a class or struct.  
<br>

* (Properties) (Expression-bodied properties (C# 6, C# 7)):
```csharp
public decimal Worth
{
	get => currentPrice * sharesOwned;
	set => sharesOwned = value / currentPrice;
}
```  
<br>

* (Properties) (Automatic properties):
  The compiler auto generates a private `backing` field of a compiler-generated name that cannot be referred to. The `set` accessor can be marked `private` or `protected`.
```csharp
public class Stock
{
	public decimal CurrentPrice { get; set;}
	
	public decimal PrevPrice {get; private set;}
}
```  
<br>

* (Properties) (Property Initializers (C# 6)):
  Like read-only fields, read-only automatic properties can also be assigned in the type's constructor.
```csharp
public int Maximum { get; } = 999;
```  
<br>

* (Properties)(Implementing an indexer): To write an indexer, define a property called `this`, specifying the arguments in square brackets.
```csharp
class Sentence
{
	string[] words = "The quick brown fox".split();
	
	public string this [int wordNum]
	{
		get { return words[wordNum]; }
		set { words[wordNum] = value; }
	}
}
```  
<br>

* (Classes)(Constants): A Constant can be any of the built-in numeric types, bool, char, string, or an enum type.  
<br>

* (Classes)(Constants): Constants vs static readonly. Constants are evaluated at compile time while static readonly is only evaluated at runtime. This prevents the need for recompilation if other assemblies reference it.  
<br>

* (Classes)(Static Constructors): A static constructor executes once per type, rather than once per instance. It must be parameterless, same name as type and only one definition.
```csharp
class Test
{
	static Test() { Console.WriteLine("Type Initialized"); }
}
```  
<br>

* (Classes)(Static Constructors)(Static Constructors and field initialization order): Static field initializers run just before the static constructor is called. If a type has no static constructor, field initializers will execute just prior to the type being used -- or anytime earlier at the whim of the runtime. Static field initializers run in the order in which the fields are declared.  
<br>

* (Classes)(Static Classes): A class can be marked `static` indicating that it must be composed solely of static members and cannot be subclassed.  
<br>

* (Classes)(Finalizers): Finalizers are class-only methods that execute before the garbage collector reclaims the memory for an unreferenced object.
```csharp
class Class1
{
	~Class1()
	{
		...
	}
}
```  
<br>

* (Classes)(Partial Types and Methods): Partial types allow a type definition to be split -- typically across multiple files.  
<br>

* (Classes)(The nameof Operator (C# 6): The `nameof` operator returns the name of any symbol(type, member, variable, and so on) as a string.
```csharp
int count = 123;
string name = nameof (count); // name is "count".

string name = nameof (StringBuilder.Length); // name is "Length".
```  
<br>

* (Inheritance): A class can inherit from only a single class, but can itself be inherited by many classes.  
<br>

* (Inheritance)(Casting and Reference Conversions): Upcasting and downcasting between compatible reference types performs reference conversions: a new reference is (logically) created that points to the *same* object. An upcast always succeeds; a downcast succeeeds only if the object is suitably typed.  
<br>

* (Inheritance)(Casting and Reference Conversions): A downcast requires an explicit cast because it can potentially fail at runtime.  
<br>

* (Inheritance)(Casting and Reference Conversions)(The as operator): The `as` operator performs a downcast that evalutates to `null` (rather than throwing an exception) if the downcast fails
```csharp
Asset a = new Asset();
Stock s = a as Stock;
```  
<br> 

* (Inheritance)(Casting and Reference Conversions)(The as operator): The `as` operator cannot perform *custom conversions* and it cannot do numeric conversions.
```csharp
long x = 3 as long;
```  
<br>

* (Inheritance)(Casting and Reference Conversions)(The is operator): The `is` operator tests whether a reference conversion would succeed; in other words, whether an object derives from a specified class (or implements an interface).
```sharp
if (a is stock)
	Console.WriteLine(((Stock)a).SharesOwned);
```  
<br>

* (Inheritance)(Casting and Reference Conversions)(The is operator and pattern variables (C# 7)): From C# 7, you can introduce a variable while using the `is` operator:
```csharp
	if (a is Stock s) {
		Console.WriteLine(s.SharesOwned);
	}
```  
<br>

* (Inheritance)(Virtual Function Members): A function marked as `virtual` can be overriden by subclasses wanting to provide a specialized implementations. A subclass overrides a virtual method by applying the `override` modifier.  
<br>

* (Inheritance)(Hiding Inherited Members): The `new` modifier suppresses the compiler warning that would otherwise result from re-declaring a similar member. This is done if you want to hide a base class member deliberately.
```csharp
public class A { public int counter = 1;}
public class B : A { public new int counter = 2;}
```  
<br>

* (Inheritance)(Hiding Inherited Members)(new versus override): `override` calls sub-class implementation when casted to base-class while `new` calls base-class implementation when casted to base-class.  
<br>

* (Inheritance)(Sealing Functions and Classes): An overridden function member may *seal* its implementation with the sealed keyword to prevent it from being overriden by further subclasses. A class can also be sealed, which implicitly seals all the virtual functions.  
<br>

* (Inheritance)(The base Keyword): The `base` keyword is similar to the `this` keyword. It serves two essential purposes:
	* Accessing an overriden function member from the subclass.
	* Calling a base-class constructor
  
<br>

* (Inheritance)(Constructors and Inheritance): The base class's constructors are *accessible* to the derived class, but are never automatically *inherited*. A sub-class must hence "redefine" any constructors it wants to expose.
```csharp
public class Subclass : Baseclass
{
	public Subclass (int x) : base (x) { }
}
```  
<br>

* (Inheritance)(Implicit calling of the parameterless base-class constructor): If a constructor in a subclass omits the `base` keyword, the base type's `parameterless` constructor is implicitly called:
```csharp
public class BaseClass
{
	public int x;
	public BaseClass() { X = 1;}
}
public class Subclass: BaseClass
{
	public SubClass() { Console.WriteLine(X); } // 1
}
```  
<br>

* (Inheritance)(Constructor and field initialization order):
	* From subclass to base class:
		* Fields are initialized.
		* Arguments to base-class constructor calls are evaluated.
	* From base class to subclass
		* Constructor bodies execute.
```csharp
public class B
{
	int x = 1; // Exec 3rd
	public B(int x)
	{
		... // Exec 4th
	}
}

public class D : B
{
	int y = 1; // Exec 1st
	public D(int x)
		: base (x + 1) // Exec 2nd
	{
		... // Exec 5th
	}
}
```  
<br>

* (The object Type): `object` is the ultimate base class for all types. Any type can be upcast to object.  
<br>

* (The object Type)(Boxing and Unboxing): Boxing is the act of converting a value-type to a reference-type instance. The reference type may be either `object` or an interface. Unboxing does the reverse. Unboxing requires an explicit cast, the cast type must match the object type exactly.
```csharp
	object obj = 9;
	long x = (long) obj; // InvalidCastException
	
	object obj = 3.5; // inferred as type double
	int x = (int) (double) obj; // x is now 3
```  
<br>

* (The object Type)(Copying semantics  of boxing and unboxing): Boxing *copies* the value-type instance into the new object, and unboxing *copies* the contents of the object back into a value-type instance. 
```csharp
int i = 3;
object boxed = i;
i = 5;
Console.WriteLine(boxed); // 3
```  
<br>


	










