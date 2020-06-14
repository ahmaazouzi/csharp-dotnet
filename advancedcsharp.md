# Advanced C#:
## Delegates:
- A delegate is a "an object that knows how to call a method". It defines the return type and parameter types of of some method. Tee instances of the delegate can call methods that have the same return type and parameter types as the delegate.
- Some liken them to C's function pointers and Javascript's callback functions.
```cs
using System;
using c = System.Console;

class Test {
	delegate int Arythmetiker(int x);

	static void Main(){ 
		Arythmetiker a = Square;
		c.WriteLine(a(4));
		a = Add;
		c.WriteLine(a(4));
		a = Expo;
		c.WriteLine(a(4));
	}

	static Choose(int z, delegate op){
		c.WriteLine(op(z));
	}

	static int Square(int x) => x * x;
	static int Add(int x) => x + x;
	static int Expo(int x) => (int) Math.Pow(x,x);
}
```
- In the examples above, **`Arythmetiker a = Square;`** is shorthand for **`Arythmetiker a = new Arythmetiker(Square);`**
- This allows for passing functions as arguments. the caller is decoupled from the target method. I've encountered situations in Java where this is the exact construct that would result in very elegant and maintainable solutions:
```cs
using System;
using c = System.Console;

class Test {
	delegate int Arythmetiker(int x);

	static void Main(){ 
		Choose(Add, 4);
		Choose(Expo, 4);
		Choose(Square, 4);
	}

	static void Choose(Arythmetiker op, int z){
		c.WriteLine(op(z));
	}

	static int Square(int x) => x * x;
	static int Add(int x) => x + x;
	static int Expo(int x) => (int) Math.Pow(x,x);
}
```
- When using methods without brackets and arguments such as `Square` or `Add` in our examples above, these are called **`method groups`**.

### Multicast Delegates:
- I find this quite gimmicky, although you might argue it can also be elegant. Basically, you can create different target methods for the same delegate and then switch between the different methods using **`+=`** or **`-=`**. Not interested!

### General Delegate Syntax/Semantics:
- Methods assigned to a delegate object can be either static or instances.
- A delegate type can have generic parameters and return type: **`delegate T Arythmetiker(T x);`**.
- Thanks to delegate generics, we can use use only two delegates to represent to replace any delegates of any return types or number of arguments. These are the `Func` (for methods that return something) and `Action` (void methods) delegates. The following snippet shows the possibilities you can have with these:
```cs
delegate TResult Func <out TResult> ();
delegate TResult Func <in T, out TResult>(T arg);
delegate TResult Func <in T1, in T2, out TResult>(T1 arg1, T2 arg2); // Up to 16 arguments
delegate void Action ();
delegate void Action<in T>(T arg);
delegate void Action<in T1, in T2>(T1 arg1, T2 arg2); // Up to T16
```
- `T` and `TResult` in the last example are the same type.
- Delegates are somehow similar to Java's functional interfaces. An interface can do anything that a delegate can. Using a whole interface to for a single method might seem chunky and verbose. A delegate will do when all you need is one method. 

## Events:
- Skipping this because the explanation is terrible!!!

## Lambda Expressions:
- As I expected, especially after trying to decipher the clumsy events section, lambdas in C# are based on delegates. Instead of the Java's functional interface, you'd use a delegate in C#:
```cs
delegate int Arythmetiker(int x);
Arythmetiker Add = x => x + x;
```
- Lambdas are commonly used with the `Func` and `Action` delegates as in:
```cs
Func<int, int> Add = x => x + x; 
c.WriteLine(Add(44));
```
- I gotta admit that lambdas, at least, with Func or Action are superior to Java's.
- The compiler can infer the type of parameters, but there are situations when you need to provide them explicitly.
- lambdas can capture outer variables. The lifetime of a captured variable is extended to match that of the delegate. This is the famous or infamous ***closure***.
- The following example shows the power of a lambda. A function is returning a function which captured a delegates local variable:
```cs
using System;

class Lam{
	static Func<int> Natural(){
  		int seed = 0;
  		return () => seed++;
  	}

	static void Main(){
  		Func<int> natural = Natural();
  		Console.WriteLine (natural());
  		Console.WriteLine (natural());
	}
}
```

## Anonymous Methods:
- What's the point if lambdas can do this already and why trying hard to making things much more complicated than they should be!?

## Exceptions:
-

## Anonymous Types:
-

## Dynamic Binding:
-

## Attributes:
-

## Caller Info Attributes:
-

## Preprocessor Directives:
-

## XML Documentation:
-
