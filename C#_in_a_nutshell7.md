* (The this Reference): The `this` reference is valid only within nonstatic members of a class or struct.


* (Properties) (Expression-bodied properties (C# 6, C# 7)): 
```csharp
public decimal Worth
{
	get => currentPrice * sharesOwned;
	set => sharesOwned = value / currentPrice;
}
```


* (Properties) (Automatic properties):
  The compiler auto generates a private `backing` field of a compiler-generated name that cannot be referred to. The `set` accessor can be marked `private` or `protected`.
```csharp
public class Stock
{
	public decimal CurrentPrice { get; set;}
	
	public decimal PrevPrice {get; private set;}
}
```


* (Properties) (Property Initializers (C# 6)):
  Like read-only fields, read-only automatic properties can also be assigned in the type's constructor.
```csharp
public int Maximum { get; } = 999;
```






