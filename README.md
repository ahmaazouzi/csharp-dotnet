# C# and .NET
- My notes as a newcomer to the C# language and the .NET platform. At this moment, I don't know anything about language except for the most rudimentary syntax. I am kinda shocked by how the capitalization of methods in C# and I am sure it will take me forever to get used to this.
- As far as the language goes, I will focus on how it differs from Java.
- I will break these notes into the following sections:
	- [C#, the Language](casharp.md)
	- [.NET, an Overview](dotnet.md)
	- [Collections and Other Utilities](collutilities.md)
	- [LINQ](linq.md)
	- [Concurrency: Multithreading, Asychronicity, etc.](concurrency.md)

## An Overview of C# and .NET
- C# is an **object-oriented** language. It supports all the good old features of Java's objects.
- One aspect where C# kinda beats Java is the unified type system. Everything is an object in C# whether it be a primitive like an integer or a custom type. You don't need to wrap the `int` type as you'd do in Java.
- C#, too, has support for functional programming in the form of lambdas and immutable types.
- C# is statically type, meaning it enforces type safety at compile time. It also enforces type safety in runtime.
- C# is strongly typed! You can't just add a float to a integer unless you explicitly do some form of casting. 
- C# can also be a dynamic language just like Python, hhmmm!!?
- The **Common Language Runtime** provides automatic **memory management**. A garbage collector takes care of and freeing memory. You can use pointers, although you might never use them and using them is restricted. 
- CLR? is that the equivalent of JVM?!
- **.NET** consists of the CLR and a bunch of libraries that include core libraries and other applied libraries, whatever that means.
- C# is a **managed language** that gets compiled into **managed code** which gets executed by the CLR. The code executed by the CLR is in the form of either an executable file (.exe) or a library (.ddl).
- The CLR converts the intermediate language (which I think is equivalent to bytecode) into native machine code though aJIT (just in time compilation) mechanism.
- With *.NET Native*, you can compile code directly into native code.








