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
- You write a your C# code in a C# file that's suffixed with a **`.cs`** extension. You compile with the **`csc`** command in a Unix environment. Your code gets compiled to an ***assembly***.  An assembly can be either an *application* or a *library*. An application has an **`extension`**, while a library has a **`.dll`** ending. The difference is that a library doesn't have an entry point (namely, a Main method).

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

## Inheritance:
## The `object` Type:
## Structs:
## Access Modifiers:
## Interfaces:
## Enums:
## Nested Types:
## Generics:

# Advanced C#:
## Delegates:
## Events:
## Lambda Expressions:
## Anonymous Methods:
## Exceptions:
## Anonymous Types:
## Dynamic Binding:
## Attributes:
## Caller Info Attributes:
## Unsafe Code and Pointers:
## Preprocessor Directives:
## XML Documentation:

















