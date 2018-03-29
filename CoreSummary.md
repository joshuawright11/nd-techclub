# Concepts

## Control

1. `for` Loops
A `for` loop takes an object of type `Array` and iterates over every element in it. Each time the block of code is run, 
the variable will be set to a different value of the array, in order. 

```swift

let array = [0, 1, 2, 3, 4]

// Will print every item of the above array
for item in array {
    // At this point `item` is equal to an element in the array. This loop repeats itself until the block has been
    // run with every element in the array as `item`.
    print("The item is: \(item)")
}
```

2. `while` loops

A while loop takes a boolean (`Bool`) and repeats itself until the boolean is `false`

```swift
var myBool = true

// This loop will run forever since in this case, `myBool` is always `true`.
// To stop it from running you would need to set `myBool = false` somewhere.
while myBool {
    // Do something here
}
```

3. `if`/`else` statements

An if/else statement has 3 parts:
1. `if`: required
2. `else if`: optional
3. `else`: optional

The `if` and the `else if` statments each take a boolean. If the boolean is `true`, and no other 
parts of the if statement before it have been executed, the statement will run. Only 1 part of an 
if statment will ever run; the first `if`/`else if` to evaluate to `true`, or the `else` if it exists and 
nothing else is `true`.

```swift
let thisIsTrue = true
let thisIsFalse = false

if thisIsFalse {
    // this won't execute because it's boolean is false
} else if thisIsTrue {
    // this will run because its boolean is true
} else if thisIsTrue {
    // this will NOT run because even though its boolean is true,
    // a previous statement has been executed
} else {
    // this will not run: a previous statement was executed
}
```

## Basics

1. variables

variables are like containers for holding your data. A variable has a 'type' (String, Bool, Int, etc) and a value (1, "hello", false, etc).
The value of the variable must be the same type as the variable.

A variable is declared with the `var` or `let` keyword like so:

```swift
// myVar is type `Int` with a value of `0`
var myVar = 0

// Variables declared with the `var` keyword can have their values changed too (as long as the type is the same):
myVar = 3
```

2. functions
A fuction is a reusable block of code. It has 3 parts: 
I. The name
II. (optional) The parameters (as many as you want allowed)
III. (optional) The return type (only one allowed)

### The name
The name of the function is what you use to call it. You call it by putting two parenthases after it with any necessary parameters:

```swift
// A function with no parameters or return type
func myGreatFunction() {
    // stuff here
}

myGreatFunction()
```

### The Parameters

A function parameter is a value that you pass to the function so that it has access to that value during its execution. Any values you pass
to the function are available as variables inside the function. You declare what the types of the parameters are when you define the function. 
When you call the function, you pass it values of the required type.

```swift
func myGreatParameters(first: Int, second: String) {
    // do stuff here, the function will have access to two variables (`first` and `second`) when it executes.
    // these will be equal to whatever values you passed it when you called it.
}

// Since the function requires 2 parameters (see above) you must pass it two values of the correct type.
myGreatParameters(first: 0, second: "Hello I'm a String")
```

### The Return Type

The return type of a function is what value the function results in when it is called. Many functions don't result in a value at all
and so there is no need to store its result. For some functions it might make sense to return a value so that it can be used. That value
can be stored in a variable just like any other value.

Use a `-> TypeName` to declare what type the function will return

Use the `return` keyword to return a value from a function

```swift
// A function with two parameters and a return type (all `Int`s)
func addNums(num1: Int, num2: Int) -> Int { // The return type is added at the end
    return num1 + num2
}
```

## Types

1. `String`: a piece of text
```swift
// Declared with "" (quotes)
var myString = "hello from swift!"
```
2. `Int`: a whole number (positive or negative)
```swift
var myInt = 12
```
3. `Bool`: a type that has 2 values (`true` and `false`)
```swift
var myInt = 12
```
4. `Array`: a type that is a list of another type. 
```swift
// To signify an array use square brackets around the element type (`[Int]` for `Array` of `Int`s)
var myArrayOfInts: [Int] = [0, 1, 2, 5, 8]

// To access an item in an array use the same square brackets with the number of the item you want to get:
var thirdItem = myArrayOfInts[2] // index `2` grabs the 3rd item since counting in programming always starts at 0

// To add an item to the end of an array use the `.append(item: Element)` function
myArrayOfInts.append(10)
// `myArrayOfInts` is now `[0, 1, 2, 5, 8, 10]`
```
5. Custom objects
You can also create your own custom types using Objects. You define the type with a class and create a value with the class's
initializer. More on that in the next section.

## Objects

1. class vs object

An object is a custom type. You describe your type by creating a class. 

```swift
class MyType {
}

// A variable holding a value of type MyType
let myVariable = MyType()
```

2. vars/funcs

A class can have variables and functions inside of it, which means that each value of your custom type will have those
variables and functions inside of it. To access a variable or function inside of a value, us a `.` followed by the variable
or function's name.

```swift
class MyType2 {
    var number: Int = 0
    func printHello() {
        print("hello")
    }
}

// A variable holding a value of type MyType
let myVariable = MyType2()

print(myVariable.number) // will print "4"

myVariable.printHello() // will print "hello"
```

3. protocols
4. initializing