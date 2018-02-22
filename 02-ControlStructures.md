*February 15th, 2018*

Functions
====
A function is a block of reusable code than a programmer can use to easily define things they want to do multiple times.

Each function has
- parameters (what variables the function takes)
- return type (what the function returns, if anything)
``` swift

// No return type or parameters
func printHello() {
    print("Hello")
}

// No return type, one parameter
func printNum(num: Int) {
   print(num)
}

// Returns an Int, 2 Int parameters
func addNumbers(num1: Int, num2: Int) -> Int {
  return num1 + num2
}
```

Control Structures
====
Control structures are things you can put in your code to perform various logic operations. (i.e. perform a 
line of code multiple times)

There are a few but there are 2 important ones to know:
- `if` statments
- `for` loops

`if` Statements
====
An if statment is simple. It takes a Boolean (`Bool` in Swift) and performs a block of code if that boolean is `true`.
(remeber booleans are `true` or `false`).

```swift
let sampleValue = true

if sampleValue {
  print("Hello, Tech Club!") // This will always run since sampleValue is true
}
```

`if` statements can also have `else if` and `else` clauses. These are also pretty straightforward; an `else if` is just like 
an `if` and takes a boolean. However, if will run its block of code
only if the boolean is `true` AND an `if` or `else if` clause before it hasn't run. You can have as many `else if`s in an if 
statement as you like.

`else` is a catch all at the end of the statement. There can only be one `else` clause and it will run if no other clauses 
have.

Remember, for an `if` statement, only one clause will run.

*Aside*: Boolean operators. There are some operators to make more complex boolean expressions. One of them is '==' (double 
equals). This takes a left and a right object and evaluates to `true` if the left and right objects are equal to eachother.

*Aside 2*: Parentheses. Parentheses work the exact same way as they do in math. Expressions inside parenthese will be 
evaluated before other parts of the expression

(Also when I say 'expression' I just mean a statement/piece-of-code/wahtever you want to call it).  

```swift
var firstCondition = false
var secondCondition = "dog" == "cat" // This will be false since the `String`s `"dog"` and `"cat"` are not equal.
var thirdCondition = (2 + 3) == 5 // This will be true since (2 + 3) equals 5

if firstCondition {
    print("This will never happen since firstCondition is false")
} else if secondCondition {
    // This also won't get called (note that if statements don't need anything inside of them, although that would be kinda 
    // dumb)
} else if thirdCondition {
    print("yay I love math! Not. Thats why I switched from math to programming.") // This will be executed
} else {
    print("everything was false! I'm so sad :(") // This won't be executed since everything else was
}

```
`Array`s
====
Just like `Int`s, `String`s, and `Bool`s (among others), `Array`s are another basic type of object in programming. Arrays are 
just lists of other objects.

`Array`s are declared with a type and `[TypeGoesHere]` (brackets). The type represents the type of the object that the `Array` 
can hold. Remember, Swift is smart and can usually infer the type of an `Array` so you don't need to write the type unless you 
want to (just like other objects).

An array can only hold objects of its type, or types that 'inherit' from its type. (inherit means that a type is a subtype of 
another type. `Cat` 'inherits' from `Animal`)

The `Array` type also has the function `.append(...)` which lets you append an element to the array. (Remember how we defined 
our own functions for objects? Swift objects have lots of these).

```swift
var birdNameArray = ["chicken", "duck", "sparrow"] // birdNameArray is now an array of type `String`
birdNameArray.append("hawk") // now `birdNameArray` has the contents ["chicken", "duck", "sparrow", "hawk"]
birdNameArray.append(12) // This won't work, `4` is an `Int` not a `String`

// Assuming `Cat: Animal` and `Dog: Animal`

var animals: [Animal] = [] // Creates an empty array that holds `Animal`s. Note that the type needs to be explicitly defined 
                           // since the program 
                           // doesn't know whats going to be in the array without it.

animals.append(Cat(...)) // Remember that Cat(...) creates a new `Cat` instance. This will be fine since `Cat` has `Animal` as 
                         // a supertype
animals.append(Dog(...)) // This will also be fine as `Dog` inherits from `Animal`
animals.append("Hello I'm a String") // Not fine. Wrong type. Crashy crashy.

```

You can also access specific items in the array by using the syntax arrayVariable[indexToAccess] where index is an `Int`. The 
first item in the array has index `0`, the second has index `1`, etc.

**Warning**: if you try and access an index higher than the number of items in the array (commonly referred to as 'the index 
out of bounds') the program will crash. RIP 🙏🏼

```swift
var array = [true, false, true, true, true] // An array of booleans

var firstItem = array[0] // firstItem will be `true`
var thirdItem = array[2] // `true`

var tenthItem = array[9] // program will crash since 9 is out of bounds (the array only has 5 items)

```

*Aside*: Literals. Some of the more basic objects in swift (`Array`, `Int`, `String`, `Double`) are able to be represented in 
'literal' form. This is just typing out what you want the value to be:
`"Hello World", 34, 23.555, ["duck"]` to initialize the object. Most other objects and all objects you create need to be 
initialized with initializers (`Cat(name: "fifi", etc.)`).


`for` Loops
====
`for` loops are useful for performing the same operation multiple times or with multiple elements. The format is like so: `for 
variable in array { ... }` where variable is a name you give to
each element as you loop through and array is an object of the array type.

```swift
var numberArray = [1, 2, 3, 4, 5, 6, 7, 8, 123586]
for item in numberArray {
    print("item is: \(item)") // Will print out every item in the list one at a time
}
```  

Ranges
----
You can also use a special `Array`-like object called a `Range` to loop a certain amount of times.
```swift
for i in 0...100 { // this is the syntax for a `Range`, both 0 and 100 will be included. This prints all numbers 0-100
    print(i)
}
```

BONUS Control Structure: `switch` (didn't go over this in lesson)
====
The `switch` is very similar to an if statement. A switch statement takes a variable, and then gives a bunch of `case` 
statements that will run if that `case`'s value equals the original variable. In swift, all switch statements must have a 
`default` case, which is like an else at the end of an `if`; it will run its block of code if no other `case`s matched.

```swift
var someString = "Taco Bell"

switch someString {
case "dog":                  // This doesn't match the given variable and wont run. Notice there aren't `{}` in each case.
    print("its a dog!")      
case "cat":
    print("its a cat!")
case "chair":
    print("its a chair!")
case "car":
    print("its a car!")
case "something":
    print("its a something!")
case "duck":
    print("its a duck!")
default:
    print("we don't know what it is :(")    // This will run. No other case statements matched the given pattern.
}
```

You may ask, "Why use a switch statement when you can just do `if someString == "dog", else if ...`"? Well good question. 
Technically you never need to use, but sometimes switch statements are much easier to read and understand if you are comparing 
against many values. In general you want code you write to be as easy to follow and understand as possible, so that future you 
or other people using your code will have an easy time.
