# F#
### Overview
The F# language was designed in 2005 by Don Syme, an Australian computer scientist and a Principal Researcher at Microsoft Research, Cambridge, U.K. The language has been influenced by C# and Erlang, but it’s mostly based on OCaml.

It’s a functional-first language, meaning it still supports OOP, but the syntax favors a functional style of coding. Since it’s been created in Microsoft labs, the language is also part of the .NET framework, it has access to all its libraries, etc. and it’s been available in Visual Studio since 2010.

For some, it is believed that the current evolution in programming is happening towards the usage of functional languages with this new style of coding. So, learning this style of programming is crucial, as it’s an important way to keep up to date with the technology and with today’s requirements. Also, functional programming improves the programming style in general. It enhances the programmer’s view on how code could be written and implemented.

Since the F# language is part of the .NET family, it comes in as a very helpful tool for already .NET programmers that want to use and implement the functional style coding in their projects or at their companies. It is also an open-source + a cross-platform language, this would attract many developers to consider this language.

### Features
Some of the features of the language, that I’ve gathered so far and found interesting, are:
- It can access all the libraries in the .NET framework (using the “open” keyword).
- The F# modules (similar to a static class in concept) that you create are accessible to your .NET applications. So we have these very helpful interconnections.
- F# is very powerful in complex and heavy applications, where multithreading can be used with almost no problems encountered, this is because this language follows the immutability idea(variables are immutable by default) which helps threads to communicate with each other safely.
- Has Type Inference: the language automatically detects the type of data (although can be specified manually).
- It reduces the use of parentheses and curly brackets and uses whitespace instead (similar to Python).
- F# has a pipe operator |> : it passes the results of one function to the following function creating this chain of arguments.

### Code Examples!
To compile our first F# program, all we have to do is install Microsoft Visual Studio (Mac/Linux/Windows). Inside Visual Studio, we create a new project and select F# from the language menu. We choose “Console App (.NET Core)” as a template and click on next.
There will be a generated **.fs** file where we can paste the following code to have the program print out “Hello, World!”
```fsharp
// import the System namespace (.NET framework)
open System

// all functions are defined above the main function
// this function prints "Hell, World!"
let printGreeting =
    printfn "Hello, World!"

// main function, similar to static public void Main in C#
// this is where the execution of the program starts
[<EntryPoint>]
let main argv =
    // code executes here
    // we'll call the previous function
    printGreeting
    // return 0, it's an accepted convention for 'the program executed successfully'
    0
```
Now, a little more advanced example using inheritance and the OOP side of the language
```fsharp
open System

// define a parent class
type ParentClass(param1) =
// member means attribute or feature of this class/type
   member this.Param1 = param1

// define a child class
type ChildClass(param1, param2) =
   inherit ParentClass(param1)
   member this.Param2 = param2

// this function takes paramteres (param1, param2)
// it initiates a child object
// and prints the parameters that were passed
let childObject param1 param2 =
    new ChildClass(param1,param2)
    printfn "param1: %O" param1
    printfn "param2: %O" param2
    
[<EntryPoint>]
let main argv =
// call the function with parameters (5,6)
    childObject 5 6
    0
```
The last example shows how recursion can be used in F#. This example displays how the pipe operator may be used as well.
```fsharp
open System

// declare it's a recursive function with "rec" keyword
let rec factorial n =
    match n with // switch statement
    | 0 | 1 -> 1 // if 0 or 1, return 1
    | _ -> n * factorial(n-1) // otherwise n * recursive call to the function
    
[<EntryPoint>]
let main argv =
// pipe operator usage, a chain of 3 functions
// take the output of the factorial function and multiply it by two
// finally, print the result
    (factorial 4) |> (fun x -> x*2) |> (fun x -> printf"Result: %i" x)
    0
```
