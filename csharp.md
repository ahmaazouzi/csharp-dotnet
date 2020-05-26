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
| `float` | `Single` | F | 32 bits | + or - (~10<sup>-45</sup> to 10<sup>38</sup>) |
| `double` | `Double` | D | 64 bits | + or - (~10<sup>-324</sup> to 10<sup>308</sup>) |
| `decimal` | `Decimal` | M | 128 bits | + or - (~10<sup>-28</sup> to 10<sup>28</sup>) |

## Numeric Types:
## Booleans:
## Strings and Characters:
## Array:
## Variables and Parameters:
## Expressions and Operators:
## Null Operators:
## Statements:
## Namespaces:









