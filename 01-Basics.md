*February 8th, 2018*

Programming
=====
- Computer/Phone runs the program line by line
- 'Comments' are used to tell the computer to ignore lines of code (useful for keeping notes in the code)
- in Swift comments are created with // for single line comments or /* stuff here */ for multi-line comments

Swift
=====
- The language we have been working with. Created by Apple and primarily used for making iPhone/Mac apps.
- **'Statically typed'**
    - this means each variable has a type that cannot be changed once set
    - the type is set when the variable is first created (with let or var) using 2 ways:
    - 'implicit': `let stringVar = "Hello"` The computer knows stringVar is of type `String`
    - 'explicit': you define the type. let stringVar: String = "Hello". In this case you don't need to define it, but it can be useful elsewhere.
    - some minor exceptions to a variable staying 1 type: an `Int` (Integer number) can be assigned to a variable of type `Double`. The computer knows how to turn (cast) an `Int` into a `Double` (just add a .0; 4 is the same as 4.0)

Variables
=====
In Swift declare a variable 2 ways:
    - `let`: this variable cannot be changed (mutated)
    - `var`: this variable can be mutated

**There are 2 types of variables**
1. Primitive types (the smallest, most basic types. In general these are in all languages.):
    - `String`: a piece of text. Must have `""` around it. e.g. "Hello, my name is Josh!"
    - `Int`: a whole number (Integer). e.g. 4
    - `Double`: A decimal number e.g. 4.0, 4.1, 43242.23748374782
    - `Bool`: A 'boolean' value. A boolean value is a value that is either `true` or `false`

2. Objects (Not in all languages, but in almost all modern languages) a programming language that uses 'Objects' is called an 
"Object-oriented" language.
    - custom defined objects
    - can be written by you or be already built into the language you are using.
    - to write a custom type or 'Object' you use a `class` as a blueprint

Code examples:

```swift

// Comments:

// Single line comment
/*
Multi
Line 
Comment

Everything between the two symbols is ignored when running the program

*/

/* Variables: */
let immutableVariable = "You can't change me because I was created with a let."
immutableVariable = "Hello world" // This line will throw an error because `let` variables can't be changed

var mutableVariable = "You can change me"
mutableVariable = "New value" // Will work fine because variable was declared as a `var`

/* Statically typed: */
var stringVariable = "Hello world"
var doubleVariable = 12.0
var boolVariable: Bool = false // The `: Bool` is unnecessary, but can sometimes be useful for readability

print(stringVariable) // will print "Hello world"
print(doubleVariable) // will print 12.0

stringVariable = 12 // will throw an error because stringVariable has type `String` and 12 is an `Int`
doubleVariable = 10 // will NOT throw an error because while 10 is an `Int` the computer is able to 'cast' it to a Double

print(doubleVariable) // will print 10.0 since the `Int` 10 was cast to a Double
```
