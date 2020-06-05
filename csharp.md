# C#, the Language:
## Basics:
### Hello, Jahan!
```cs
using System;

class Something {
	static void Main(){
		Console.WriteLine("Hello, World!");
	}
}
```
- **`Main`** is the entry point of execution to a program. I am still confused about why they Capitalize methods. They call it PascaleCasing, but I think it's just bad design.
- Our **`Main`** method doesn't take any parameters, but it can take an array of strings as a paramter as in **`Main(string[] args) { ... }`**. 
- Methods are only one type of ***functions***. There are other types of functions such as constructors, *events, properties, events, indexers, finalizers*. It's claimed that the **`*`** operator is also a function!! Interesting.
- Classes or types are organized into ***namespaces***. I would say a namespace is equivalent to a Java package. You can define multiple packages in the same file. C# has less of the weird restrictions of Java. A namespace can be defined just like a class is. You name the namespace, open curly braced and voilà. You can even have multiple namespace in the same sourcefile. This is COOOOOL!:
```cs
using System;

namespace Test {
	class Something {
		static void Main(){
			Mama.Wawa.wawa();
			FooBar.Foo.foo();
			FooBar.Bar.bar();
		}
	}
}

namespace FooBar {
	class Foo {
		public static void foo(){
			Console.WriteLine("FOO");
		}
	}

	class Bar {
	public static void bar(){
		Console.WriteLine("BAR");
		}
	}
}

namespace Mama{
	class Wawa {
		public static void wawa(){
			Console.WriteLine("WAWA!");
		}
	}
}
```
- I am using Sublime Text 3 to test code and so far I haven't been getting a lot of errors, almost none! That wasn't the case with Java where I almost always had to use the eclipse to avoid too many syntax errors.

### Compile:
- You write a your C# code in a C# file that's suffixed with a **`.cs`** extension. You compile with the **`csc`** command in a Unix environment. Your code gets compiled to an ***assembly***.  An assembly can be either an *application* or a *library*. An application has an **`.exe`** extension, while a library has a **`.dll`** ending. The difference is that a library doesn't have an entry point (namely, a Main method).

## Syntax:
- An **identifier** is a name you give to a variable, a class, method.. etc. As in other languages, the identifier must be a whole word (made of Unicode characters) that starts with a letter or an underscore. They are case-sensitive as well.
- Finally I see what's with the case conventions: *parameters, local variables and private fields should be cmalCased*, while other identifiers like methods, class names, namespaces ..etc. are to be *PascaleCased*.
- C# has a few dozen **keywords**, most of which are reserved!! Why would you use a keyword as an identifier even if it weren't reserved?!!! All keywords are in lower case. You have a **`string`** keyword. 
- To avoid clashes with reserved words, you qualify your name with a **`@`** as in the following example:
```cs
string @string = "string";
```
- This is useful when using libraries written in other .NET languages which use different keywords.
- **Contextual keywords** can sometimes be used as identifiers based on the context where they are used. These include: **`add`**, **`join`**, **`remove`**, **`on`**, **`where`**, **`when`**, **`select`**, **`set`**... etc. 
- **Literals** are literals. Examples include 23, "foo" and 'b'.
- A **punctuator** is.. is a vague word. Some other platforms use that for all the non-alphanumeric symbols, but in the context of C# it's used to denote symbols that demarcate blocks and parts of a program such as curly braces and semicolons.
- Comments are similar to Java's. You have options for a one line, multiline and a documentation comment.

## Types:
- A **type** defines a blueprint for a value.
- A **variable** defines a memory location that can can contain different values of the same type or compatible types.
- Every value in C# is an instance of some type.
- There are 2 types of types (I know):
	+ **Predefined types** are built-in types that are supported by the compiler. You don't the **`new`** operator to create an instance of one. Keywords such as **`string`**,**`bool`** and **`int`** are some of the common predefined types.
	+ **Custom types** are the ones you define on your own. Their names are not keywords.
- A type can have two types of members:
	+ **Data members** are data fields.
	+ **Function members** which include: methods and constructors.
- Predefined types are barely different from custom types. Every object in C# has a **`toString()`** method.
- A predefined type is instantiated simply with a literal value. A custom type needs the **`new`** operator to be instantiated. When, `new` is used to instantiate an object, the constructor is called.
- **Instance members** operate on the instances of a type. **Static members** operate on the type itself. You can even have **static classes**. These only contain static members.
- Just like in Java, types can be **converted** **implicitly** between compatible types. when you assign a value of type **`int`** to a type **`long`**, the integer is implicitly converted by the compiler into a long integer. You can also **explicitly** convert a type to another with **casting**.
- The possibility of an explicit type conversion taking place depends on the possibility of information loss and the likelihood of the conversion taking place. Otherwise, you have to do an explicit conversion. Converting a float into an int can't be done explicitly because
- C# types can also be divided in the following 4 categories: **value types**, **reference types**, **generic types** and **pointer types**. we will talk about generic types and pointer types later. For now:
	+ **Value types** include most built-in types (numeric types, **`bool`**, **`char`**). They also include custom **`enum`** and **`struct`** types. C# stores these as values.
	+ **Reference types** include class, interface, array and delegate types (including the **`string`** type). These store references to the objects they point to.
- Reference types be assigned a **`null`**. Value types can't!! See?! This is bad! In Java all objects are nullable and primitives are not! In C# you need to know what's a reference and what's a value type. 
- Memorywise, reference objects eat up memory of the object itself plus memory for the reference itself.
- The following tables shows the complete taxonomy of predefined types concerning whether they are value or reference types:

<table>
	<tr>
		<th rowspan="15">Value<br>types</th>
	</tr>
	<tr>
		<th rowspan="12">Numeric</th>
	</tr>
	<tr>
		<th rowspan="4">Signed<br>Integer</th>
		<td>sbyte</td>
	</tr>
	<tr>
		<td>short</td>
	</tr>
	<tr>			
		<td>int</td>
	</tr>
	<tr>			
		<td>long</td>
	</tr>
	<tr>
		<th rowspan="4">Unsigned<br>Integer</th>
		<td>byte</td>
	</tr>
	<tr>
		<td>ushort</td>
	</tr>
	<tr>			
		<td>uint</td>
	</tr>
	<tr>			
		<td>ulong</td>
	</tr>
	<tr>
		<th rowspan="3">Real<br>Number</th>
		<td>float</td>
	</tr>
	<tr>
		<td>double</td>
	</tr>
	<tr>			
		<td>decimal</td>
	</tr>
	<tr >
		<th colspan="2" >Logical</th>
		<td>bool</td>
	</tr>
	<tr >
		<th colspan="2">Character</th>
		<td>char</td>
	</tr>
	<tr>
		<th rowspan="3">Reference<br>types</th>
	</tr>
	<tr>
		<th colspan="2">Object</th>
		<td>object</td>
	</tr>
	<tr>
		<th colspan="2">String</th>
		<td>string</td>
	</tr>
</table> 

- Primitives in C# are still similar to those in Java in they are performed. They are compiled directly to machine code instructions.

## Numeric Types:
- The following table summarizes most of what one needs to know about numerical types in C#

| C# Type | System Type| Suffix | Size | Range |
| --- | --- | --- | --- | --- |
| `sbyte` | `SByte` |  | 8 bits | -2<sup>7</sup> to 2<sup>7</sup>-1 |
| `short` | `Int16` |  | 16 bits | -2<sup>15</sup> to 2<sup>15</sup>-1 |
| `int` | `Int32` |  | 32 bits | -2<sup>31</sup> to 2<sup>31</sup>-1 |
| `long` | `Int64` | L | 64 bits | -2<sup>63</sup> to 2<sup>63</sup>-1 |
| `byte` | `Byte` |  | 8 bits | 0 to 2<sup>8</sup>-1 |
| `ushort` | `UInt16` |  | 16 bits | 0 to 2<sup>16</sup>-1 |
| `uint` | `UInt32` | U | 32 bits | 0 to 2<sup>32</sup>-1 |
| `ulong` | `UInt64` | UL | 64 bits | 0 to 2<sup>64</sup>-1 |
| `float` | `Single` | F | 32 bits | ±(~10<sup>-45</sup> to 10<sup>38</sup>) |
| `double` | `Double` | D | 64 bits | ±(~10<sup>-324</sup> to 10<sup>308</sup>) |
| `decimal` | `Decimal` | M | 128 bits | ±(~10<sup>-28</sup> to 10<sup>28</sup>) |

### Numeric Literals:
- You can represent an integral type using either a decimal or a hexadecimal notation. The hexadecimal notation is prefixed with a **`0x`** as in **`int x = 0x20F`**.
- Floating types can use a decimal or exponential notation:
```cs
double tenth = 0.1;
double thousand = 1E3;
```
- The default integral type is `int` (integer) and for a floating type, it is `double`. The compiler automatically infers these types from literals.
- Most of the suffixes you see in the table above are useless except for **`D`**  and**`F`**. You use these to distinguish **`flot`** and **`decimal`** types from the default **`double`** type. In fact, these two suffixes are absolutely necessary to use values of float and decimal types:
```cs
float f = 2.5 // Won't compile
decimal d = 2.5 // Won't compile

float f = 2.5F // Will compile
decimal d = 2.5d // will compile
```

### Numeric Conversions:
- As pointed earlier. An implicit conversion can only take place when the integral number is converted into a larger width-bit integral type. Otherwise, the conversion must be explicit using a cast.
- Converting a **`float`** to a **`double`** can also be implicit. The reverse must be explicitly done.
- Integral types can be implicitly converted to to float-point types, but the reverse must be done explicitly. The decimal parts are truncated without rounding. If you want to perform rounding, use **`System.Convert`**.
- Implicit conversion of a large integral type to a floating type preserves magnitude but might result in the loss of precision. There is only so much a floating type's mantissa can hold.
- Integral types can be implicitly converted into the **`decimal`** type. All other conversions from and to the decimal type are required to be explicit.

### Arithmetic Operators:
- Integral divisions result in truncating the remainder with a rounding toward zero.
- By defaults, integral types can result in an overflow without giving any warnings. To get that warning you'd use the **`checked`** operator as in:
```cs
sbyte y = 127;
y++;
Console.WriteLine(y); // result is -128. Probably not the desired result

sbyte x = 127;
Console.WriteLine(checked(++x)); // Throws a runtime error because of the overflow
```
- You can apply checking for overflow in a whole program using the **`/checked+`** option during compilation as in:
```
csc /checked+ lalo.cs
```
- Programs compiled with overflow checking as a default, you can use the **`unchecked`** operator for the particular expressions and statements you don't want the underflow to be checked for as in: **`int x = int.MaxValue;`**.
- Expressions evaluated at compile time are always checked by default.

### Integral peculiarities:
- This is weird: 8-bit and 16-bit don't have their arithmetic operators. C# converts these to integers and then apply whatever operations you choose for them. The following example shows issues with such a set up:
```cs
short x = 9;
short y = 1;

short z = x + y; // This results in a compile time error
short w = (short) x + y; // The cast fixed the problem
```

### Floating Peculiarities:
- Floating-point types have some special values such as **NaN**, **∞**, **-∞**, and **-0**. The following table shows these:

| Value | Double Constant | Float Constant |
| --- | --- | --- |
| Nan | **`double.NaN`** | **`float.NaN`** |
| +∞ | **`double.PositiveInfinity`** | **`float.PositiveInfinity`** |
| -∞ | **`double.NegativeInfinity`** | **`float.NegativeInfinity`** |
| -0 | **`-0.0`** | **`-0.0F`** |

- Dividing zero by a non-zero results in an infinity, positive or negative based on the operands.
- Dividing a zero by a zero results in a NaN.
- A NaN is not equal to any number including another NaN if an **`==`** operator is used. Checking the equality of two NaNs with the **`.equal()`** method results in a true, though!

## Booleans:
- A boolean takes only one bit to store, but the smallest unit the runtime can work with is one byte, so we use a byte for it. The runtime offers the **`BitArray`** class for storing boolean values are single bits. 
- C#, like almost every other language has a ternary operator **`(x > y) ? x : y`**

## Strings and Characters:
- C# characters (**`char`** / **`System.Char`**) are Unicode characters made of bytes. A character can also be input using its 4-digit hex Unicode code preceded by a **`\u`** or **`\x`** as in **`'\x132D'`** and **`'\u132D'`**.
- I believe that characters are enclosed within single quotes just like in other C-like languages.
- While strings (**`string`** / **`System.String`**) are reference type, their equality operator **`==`** acts as if its operands are of value type.
- C# strings can be ***verbatim***, meaning they contain what you type in them and escape characters are useless in these. These are specified by prepending a **`@`** to the string as in:
```cs
Console.WriteLine(@"\n I am sick of this thing!\t");
// Outputs => "\n I am sick of this thing!\t"
```
- The string concatenation operator **`+`** is inefficient if used many times. A more efficient way can be done with the string builder **`System.Text.StringBuilder`**.
- **String interpolation** refers to using strings as some kind of templates where you inject expressions. They are similar to Javascript's template literals: 
```cs
Console.WriteLine($"I want {15 * 3} books!!!");
```

## Arrays:
- There is a variety of ways you can declare and initialize a variable in C#:
```cs
int[] nums = new int[3];
int[] integers = new int[] {1,2, 3};
int[] numbers = {1, 2, 3};
```
- An array's length can be accessed through the **`Length`** property.
- For 2D arrays, you can either have a rectangular arrays, whose two sides are equal in size, or jagged (the inner arrays variable lengths). A rectangular array looks as follows:
```cs
int[,] matrix = new int[,] {
	{0,1,2},
	{3,4,5},
	{6,7,8}
};
```
- A jagged matrix is initialized as follows:
```cs
int[][] matrix = new int[][] {
	new int[] {0,1,2},
	new int[] {3,4,5},
	new int[] {6,7,8,9}
};
```
- C# does also have the infamous **`indexOutOfRangeException`** runtime error!

## Variables and Parameters:
- A variable can be a *local variable, parameter, field* or *array element*.

### Heap and Stack:
- Variables live in two regions in memory called the ***stack*** and ***heap***. In each one of these regions, variables have different behaviors.
- Function parameters and local variables live in the stack. When a function is entered, its parameters and local variables are added tot stack and the stack grows. When the function is exited, its parameters and local variables are removed and the stack shrinks.
- Reference type instances live in the **heap**. When objects are created, they are added to the heap and when no long referenced, the garbage collector clean them away. The garbage collector does the cleaning periodically. Objects that are still referenced are not touched by the collector. 
- Instances declared as fields of classes or array elements live in the heap. 
- The heap also stores static fields. Static fields don't get garbage collected, however. They live live as long as the application itself.
- Each type has a default of some short (integers, for example have 0 as their default value). You must initialized variable you declare before you can use them, but some cases such variables can have their default values even if you don't initialize them. Class **fields are initialized automatically to their types default values**. You can obtain the default value of any variable using the **`default`** keyword as in:
```cs
int x = default(int);
```
- The default values for common types are as follow:

| TYPE | DEFAULT VALUE |
| --- | --- |
| Rference Types | `null` |
| Numeric Types | `0` |
| `char` | `\0` |
| `bool` | `false` |

### Parameters:
- Paramters are passed by value by default. Value types get copied into functions. For reference types, copies of references to the objects are obtained by the function. Making a change in the function is reflected in the object. Basically, an independent copy of a reference to an object is created when such as a parameter is passed into a function. 
- With the **`ref`** modifier, you can make a parameter act as if it's passed by reference, as if you're passing a C pointer to your function. The **`ref`** modifier should placed in both the function definition and the call to that function. The following examples shows how it works:
```cs
using System;

class Test {
	static void Lala(ref int a){
		a = a * 2;
	}

	static void Main(){
		int x = 44;
		Lala(ref x);
		Console.WriteLine(x); // Outputs 88
	}
}
```
- A parameter can be passed by value or by reference regardless of whether the parameter is a of a type or reference value. 
- There is another modifier called **`out`** that almost works like **`ref`**, but I kinda find it a little useless.
- Passing an argument by reference merely aliases the storage location of an existing variable instead of creating a new one. That might be good for memory but would create nightmares when a lot of functions can change their parameters and result in some bad bugs!
- You can add the **`params`** modifier to the last parameter of a method allowing the method to accept any number of arguments of the type of that parameter. Params following this modifier are placed in an array:
```cs
using System;

class Test {
	static void mama(string potato, char a, params int[] ints){
		Console.WriteLine(potato);
		Console.WriteLine(a);
		Console.WriteLine("");
		for (int i = 0; i < ints.Length; i++)
			Console.WriteLine($"Param no: {i}");
	}

	static void Main(){
		mama("potato", 'p', 1,2,3,4,5);
	}
}
```
- **Named parameters** are another gimmicky useless addition that only adds confusion.
- **Optional parameters** are the exact same ones as their counterparts in Javascript. In a function's definition you provide a fallback value if no argument is given as in **`void Foo(int x = 55)`**. If Foo is called with no arguments, x's value becomes 55.

### Var:
- The **`var`** keyword is similar to how it works in Javascript. You don't need to supply a type label. However, C# remains a statically typed language. You can't change the type of a variable declared with the keyword **`var`**:
```cs
var x = 3333;
x = "GITHUB"; // This causes a compile error
```

## Expressions and Operators:
- An expression is a block that returns a value, this can be as small as a variable or a constant (a literal).
- There void expressions, those which don't return anything or return a void value such as a print statement.
- C# has a bunch of operators. Some of them can be overloaded.

## Null Operators:
- To prevent the headaches associated with nulls, C# provides two operators:
	+ **The null-coalescing oprator (`??`)**. If the first operand is null, give the second one. **`string s = v ?? "No String!"`**
	+ **The null-conditional operator (`?.`)**. This is also called the ***Elvis*** operator. It calls methods and accessed members of a class/object. If the object is null, this the expression evaluates to null instead of resulting in a **`NullReferenceException`** as the following example shows:
```cs
object s = null;
string s1 = s?.ToString();
```

## Statements:
- Statements execute sequentially in the order they appear in the source code. A ***statement block*** is a series of statements enclosed within braces.

### Declaration Statements:
- These are the ones used to declare variables and constants. The initialization in a variable declaration statement is optional, but it is mandatory in constants. Constants are declared with the **`const`** keyword.
- One peculiarity that might actually be good is the fact that even if an outer variable is declared after a block, it hides the variable inside the block. "Scope extends in both directions."

### Expression Statements:
- These either change state or call something that changes state. They include: method calls, assignment expression and object instantiation. 

### Selection Statements:
- These include **if** statements with **else** clauses and **switch** statements.

### Iteration Statements:
- C# has the regular iteration statements **for**, **while** and **do while**.
- The one special iteration statement is **foreach**. It acts like Python and Javascript's **for in**:
```cs
int[] baba = {1, 2, 3, 4, 5};
foreach(int i in baba)
	Console.WriteLine(i * 3);
```
- **foreach** statements have one important limitation. You can't directly change the content of an array with this statement.

### Jump Statements:
- With the **`break`** statement you can break out of an iteration or a switch statement.
- **`continue`** allows you to skip steps in iterations.
- **`goto`** is used to create spaghetti code.
- With **`return`** you exit any method!
- **throw** throws an exception  indicating the occurrence of an error:
```cs
if (index < 0 || index >= numbers.Length)
	throw new IndexOutOfRangeException();
```

## Namespaces:
- Namespaces are a great way of organizing code and avoiding conflicts. Namespaces are independent of assemblies and have no impact on member visibility.
- Namespaces can be nested and are defined using the **`namespace`**. The following code defines some nested namespaces:
```cs
namespace Out {
	namespace Middle {
		namespace In {
			// Classes go here
		}
	}
}
```
- Nested namespaces are separated by dots. The following snippet is identical to the one above:
```cs
namespace Out.Middle.In {
	// Classes go here
}
```
- Classes/types not defined inside a namespace live in the ***global namespace***. The global namespace also includes all the top level namespaces.

### `using`:
- **`using`** is used to *import* namespaces. It allows you to use the contents of a namespace without their fully qualified names.
- **`using`** allows you to import specific types. When used with the modifier **`static`** as in **`using static System.Console;`**. This allows you to use all the public static fields and methods of that class. Now, you don't need the boring wordy **`Console.WriteLine()`**. You can do with just **`WriteLine()`**.
- You can and should use similar names of classes across multiple namespaces. It is not always easy to come up with good names.

### Namespace Rules:
- **Name Scoping** is largely obvious. Inner namespaces don't need to qualify  names defined in outer namespaces.
- **Name hiding** occurs when similar names are defined in the current and outer namespaces. The inner name hides the outer one. To avoid the clash, go ahead and fully qualify the outer name.
- **Repeated namespaces**: Namespaces can be repeated within the same namespace as long as the types inside the repeated namespaces have types with different names.

### Aliasing Namespaces:
- Namespaces can be aliased as in the following example:
```cs
using PropertyInfo2 = System.Reflection.PropertyInfo;
```

# Object Oriented C#:
## Classes:
- A class definition can be as simple as:
```cs
class Something {
}
```
- A typical may also have the following syntactic elements:
	+ Preceding the keyword **`class`**: *Attributes* (we will see these later) and *class modifiers*
	+ Following the class Name: *Generic type parameters, a base class* and *interfaces*.
	+ Inside braces: *Class members* (which includes methods, properties, constructors... etc.)

### Fields:
- They are variables that are members of classes or structs. They can have their own modifiers.
- One special modifier that a C# field can have is the **`readonly`**. This doesn't quite make it field a constant since it can be assigned only once in a constructor or a field initializor. A const is decided at compile time. A readonly field is assigned only once in run time and once assigned it can't be changed. 

### Methods:
- Methods within the same class must have **unique signatures**. A unique signature is a combination of the method's name and the types of its parameter.
- One line methods can be reexpressed in a more elegant way (similar to Java's lambdas and ES6 arrow functiona):
```cs
// The following two methods are identical
int Add(int a, int b){ return a + b;}
int Add(int a, int b) => a + b;
// The following two methods are identical
void printInt(int a){ Console.WriteLine(a); }
void printInt(int a) => Console.WriteLine(a);
```
- Methods within the same type can **overload** each other, meaning they can have the same name but different signatures. Be careful about the **`ref`**/**`out`** modifiers. These can also have a role in overloading methods.

### Constructors:
- Constructors can also be overloaded. A constructor can call another constructor to avoid code duplication as in:
```cs
using System;
using c = System.Console;

 public class Test {
	static void Main(){
		Cat cat1 = new Cat(1, "Sam", "Persian");
		Cat cat2 = new Cat(2);
		Cat cat3 = new Cat(3, "Meg", "Bengal");
		Cat cat7 = new Cat(7, "Burmeze");

		c.WriteLine($"{cat1.Age}, {cat1.Name}, {cat1.Breed}");
		c.WriteLine(cat2.Age);
		c.WriteLine($"{cat3.Age}, {cat3.Name}, {cat3.Breed}");
		c.WriteLine($"{cat7.Age}, {cat7.Name}");
	}
}

class Cat {
	public int Age;
	public string Breed;
	public string Name;

	public Cat(int age){
		Age = age;
	}

	public Cat(int age, string name): this(age){
		Name = name;
	}

	public Cat(int age, string name, string breed): this(age, name){
		Breed = breed;
	}
}
```
- The only odd thing so far about constructors and type creation is the fact that objects are instantiated without the use of **`this`** keyword, the way it's done in Java. 
- The compiler generates an implicit **parameterless constructor** if you don't define a constructor. If you define a constructor, no automatic parameterless constructor is generated.
- In C#, too, a static factory method is suggested as a replacement for public constructors. This comes straight from the book *Effective Java*.

### Object Initializers:
- These allow you to set the public fields of a class directly. They are terser. The following two snippets do the exact same thing.

```cs
Cat cat1 = new Cat {Age=22, Name="Baba", Breed="Egyptian"};

```
```cs
Cat cat1 = new Cat();
cat1.Age = 22;
cat1.Name = "Baba";
cat1.Breed = "Egyptian";
```

### `this`:
- The **`this`** keyword refers to the current instance. It might not be as useful in C# as it is in Java because C# capitalizes fields and keeps parameters (including constructor parameters) camelcased??!!!

### Properties:
- The weird and contrarian naming patterns keeps getting weirder!
- Properties are similar to field but they contain logic. A property has a **`get`/`set`** block. **`get`** and **`set`** act as property *accessors*. This is reminiscent of the setters/getters stuff you hear about everywhere. The following snippet shows you how 
```cs
class Cat {
	string name;
	public string Name {
		get {return name;}
		set {name = value;}
	}
}
```
- To use a property you'd do:
```cs
Cat cat = new Cat();
cat.Name = "Mickey";
Console.WriteLine(cat.Name);
```
- If a property has only a `set` accessor, it is write-only. If it only has a `get` accessor, it is read-only.
- You can also have a computed value of a property as the following example shows:
```cs
double Price {
	get {return net - discount + tax;}
}
```
- A read-only property can be expressed using an arrow function:
```cs
double Price =>  net - discount + tax
```
- **Automatic properties** allow you create properties without specifying a backing field. In our earlier examples, we first specified fields and then created properties that acted as setters/getters on them. The following examples shows you how you might not really need such a backing field:
```cs
class Cat {
	public string Name { get; set;}
}
```
- The compiler automatically generates a private field that can't be referenced. You can make the set accessor a private or protected field to make it read only yo other types.
- Properties can have initial values with property initializers:
```cs
class Cat {
	public string Name { get; set;} = "Johnny";
}
```
- You can make such a property read only.
- `set` and `get` can have their own access modifiers to control access to the property. It's common to make the property itself public, `get` public and `set` private or protected.

### Indexers:
- These are similar to properties with the exception that they access indexed arguments instead of property names. I don't know when I will ever need this, so I won't even bother.

### Static Constructors:
- A ***static constructor*** runs once per class. There can be only one static constructor per class and it must be parameterless:
```cs
class Hack {
	static Hack(){
		Console.WriteLine("Let the hacking bagin!");
	}
}
```

### Static Class:
- A static class is marked by a static modefier. It can only have static members and cannot be subclassed. `System.Console` is a static class.

### The `nameof` Operator:
- **`nameof`** returns the name of any symbol (variable, member, class, method... etc.) as a string??!! What's the point?!

## Inheritance:
- Basically, C# replaces Java's `extends` with a colon **`:`**:
```cs
class Animal{
	public string Name;
}

class Cat : Animal {
}
```

### Polymorphism:
- The polymorphic nature of object-oriented programming is obviously present in C# as well. When instantiating objects, you make them of superclass types. Referring to objects by their interfaces and superclasses makes them more flexible for maintainability. The language is smart enough to tell the concrete object it's dealing with. After all, polymorphism is the core of OOP!

### Casting and Reference Conversions:
- You can ***upcast*** a class to its base class and ***downcast*** a class to its subclass. These two types of casting result in ***reference conversions***, namely, a new reference with a different type (though related) that point to the same object is created. While an upcast always succeeds, and downcast might succeed depending on a number of conditions. 
- When you upcast a class, it loses methods it had before the upcasting.
- The **`as`** operator is language features that facilitates casting/reference conversions. It creates a downcast and if the downcast fails it creates a null instead of throwing an error:
```cs
Animal a = new Animal();
Cat c = a as Cat; 
```
- With the **`is`** operator, you can check if a reference conversion is possible as in **`if (Cat is Animal) { // Do something;}`**.

### Virtual Function Members:
- Virtual function members can be **overridden**. To override a method, property, indexer... etc., you'd mark it with **`virtual`** keyword and mark the inherited class with the **`override`** keyword. The signature, return type and accessibility of the overrider and overridden must be the same:
```cs
class Animal {
	public virtual string Sound => "No sound ...";
}

class Cat: Animal {
	public override string Sound => "Miow";
}
``` 

### Abstract Classes and Abstract Members:
- Classes declared as **`abstract`** are never instantiated. Only the concrete subclasses of an abstract class can be instantiated. Abstract classes can have abstract members. Abstract members are similar to virtual members, except in that they don't have default implementation and they must be implemented by the subclasses of the abstract class. Overriding an abstract method is also done using the `override` keyword:
```cs
class Animal {
	public virtual string Sound;
}

class Cat: Animal {
	public override string Sound => "Miow";
}
```

### Hiding Inherited Members:
- When a class and its base class define the same member, the parent member gets hidden.
- The compiler generates a warning that the base class members has been hidden. Generally, a member hiding another member inherited from some base class is made accidentally. The warning will always be generated even if creating the hiding member were deliberate. To avoid generating such a warning, you can use the **`new`** keyword as in:
```cs
class Animal {
	public string Sound => "Niet Sound!!!";
}

class Cat: Animal {
	public new string Sound => "Miow";
}
```

### Sealing Functions and Classes:
- With the **`sealed`** keyword, you can:
	+ Seal an overridden function from further overriding by functions in classes that subclass the current class. This modifier should be applied to the function itself.
	+ Apply the `sealed` keyword to the class itself, so that any class that inherit from the current class is unable to override its virtual functions.
- Sealing classes is a more common practice than sealing functions.

### The `base` Keyword:
- With the **`base`**, you can access an overridden function from the subclass. Even a hidden function can be called with `base`. You can also use it to access the constructor of the base class.
- This is basically Java's `super` keyword.

### Constructors and Inheritance:
- I can't tell why, but subclasses don't automatically inherite constructors from base classes. Subclasses must either redefine their own constructors. They can call their baseclasses constructors to redefine their own using the keyword `base`:
```cs
class Animal {
	public string Species;
	public Animal(string species="None"){
		this.Species = species;
		c.WriteLine(Species);
	}
}

class Cat: Animal {
	public Cat(string species): base (species){}
}
```
- A constructor in a subclass can call a baseclass parameterless constructor without the keyword `base`.

### Overloading and Resolution:
- 

## The `object` Type:
- The **`object`**/**`System.Object`**type is the baseclass that everything else inherits from. You can upcast anything to the object type. The book gives an example of a stack structure of the object type. This stack can store anything. Just upcast an object to type object and push it into the . When you need it, you pull it and downcast it to its original class.

### Boxing and Unboxing:
- The `object` type is a reference type. Types like `int` are of a value type. Conversion from value type to reference type is called ***boxing***. The reverse is called ***unboxing***. One of these two conversions always take place when casting between the `object` type and any value-type. Depending on the type, an explicit casting might be required.

## Structs:
- Structs seem really redundant, but whatever! These are the same as classes but they are value type objects and they don't inherit or are inherited from. They have a few other limitations such as the abscence of parameterless constructors or absence of virtual members.
- Value type is more efficient as the creation of a new value type doesn't require the instantiation of a new object in the heap.

## Access Modifiers:
- **`public`** is visible to the whole world.
- **`internal`** is visible within the current assembly or friend assemblies (I don't know what a friend assembly is). It is also the default if no access modifier is specified.
- **`private`** is only accessible within a type. It is the default of a class members.
- **`protected`** is only accessible to the type and its subclasses. 
- **`protected internal`** is a union of protected and internal. Something marked with this modifier is accessible if it is protected OR internal.

### Friend Assemblies:
- We can expose the internal members of an assembly using the **`System.Runtime.CompilerServices.InternalsVisibleTo `** assembly attribute:
```cs
[assembly: InternalsVisibleTo ("Friend")]
```

### Accessibility Capping:
- Accessibility capping happens when a type limits the accessibility of its members. Public members in an internal class are not public but are capped by their internal class: they are internal!
- Making members public is more useful than internal. If one day you want yo make your internal class public, you don't need to make its members public, they are already public. Inside an internal class, they were capped.

### Restrictions on Access Modifiers:
- Overridden functions must have the same access modifiers.
- Subclassed types must have the same accessibility or be less accessible than their base classes.

## Interfaces:
- Interfaces provide a specification rather than an implementation. While Abstracts provide partial implementations, interfaces are completely abstract. They are special in that:
	+ They are ***all implicitly abstract***.
	+ A class or a struct can implement multiple interfaces.
- Notice how structs, too, can implement interfaces. 
- Interface members can only be methods, properties or indexers.
- Interface members are all implicitly public and cant declare access modifiers.
- Interface example:
```cs
internal interface Animal {
	string Name { get; }
}

internal class Cat: Animal{
	public string name;
	public string Name {
		get { return this.name;}
		set { this.name = value;}
	}
}
```
- An object can be implicitly cast to an interface it implements, obviously.

### Extending Interfaces:
- You can create composite interfaces by making interfaces inherit from other interfaces.

### Explicit Interface Implementation:
- Since a class can multiple interfaces, there might be collusions when two classes have members that share the same name. To avoid such a problem, you need to explicitly implement some or all members that share the same name. To call an explicitly implemented member, you need to cast the implementing class to the interface where the member is specified. This resuls in not so beautiful code:
```cs
using System;

public class Test {
	static void Main(){
		BarClass bar = new BarClass();
		bar.Foo();
		((Bar2)bar).Foo();
	}
}

internal interface Bar1 {
	void Foo();
}

internal interface Bar2 {
	void Foo();
}
internal class BarClass: Bar1, Bar2 {
	public void Foo(){
		Console.WriteLine("Bar 1");
	}

	void Bar2.Foo(){
		Console.WriteLine("Bar 2");
	}
}
```

### Virtual Implementation and Reimplementation:
- Implementing the members of an interface results results in sealed members in the implementing class. To be able to implement these in classes that subclass the current class, you need to make these virtual or abstract:
```cs
using System;
using c = System.Console;

public class Test {
	static void Main(){
		Persian persian = new Persian();
		persian.Name = "Farhad";
		c.WriteLine(persian.Name);
	}
}

internal interface Animal {
	string Name { get; }
}

internal class Cat: Animal{
	public string name;
	public virtual string Name {
		get { return this.name;}
		set { this.name = value;}
	}
}

internal class Persian: Cat {
	public override string Name {
		get { return this.name;}
		set { this.name = "I am " + value;}
	}
}
```

- When an interface member is explicitly implemented, it can't be overridden or marked as `virtual`, but it must instead be *reimplemented*. Reimplementation will work regardless whether the member in the base class is declared virtual or not. Reimplementing an interface in a subclass without consulting its concrete parents is called *reimplementation hijacking*. Hijacking is bad because it breaks when you cast the subclass to its base class. Try to avoid it if you can!

## Enums:
- A little disappointing! C# enums are kinda bland and don't do much. They are groups of named constants:
```cs
public enum Degrees {Bachelor, Master, PhD};
```
- Each enum has an underlying integral value.

## Nested Types:
- Nested types are types that live in the scopes of other types.
- A nested type has these features:
	+ It has access to everything in the enclosing type, including private members. They also have access to everything the enclosing type has access to.
	+ It can have all access modifiers.
	+ Its default access modifier is private instead of internal.
	+ Accessing a nested type from outside the enclosing type is similar to Accessing a static member. You access the type and not an instance of it.
	+ All types can be nested inside a class or a struct. 

## Generics:
- Generic types declare *type parameters*



















