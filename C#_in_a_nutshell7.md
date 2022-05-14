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














