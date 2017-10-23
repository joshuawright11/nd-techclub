*October 11th, 2017*

Functions
====
Each function has
- parameters (what variables the function takes)
- return type (what the function returns, if anything)
``` swift

// No return type
func printNum(num: Int) {
   print(num)
}

// Returns an Int
func addNumbers(num1: Int, num2: Int) -> Int {
  return num1 + num2
}
```
A function can be defined in an object. When it does, it has access to that object's variables and functions.

```swift
class Duck: NSObject {

  var noise = "Quack"
  
  func speak() {
    // has access to noise variable since in the object
    print(noise)
  }
}
```

Subclassing
====
Each object has a "type" that is whatever class it came from. 1 is type Int, Duck() is type Duck (assuming you defined a Duck class, as above.)

Each object also has a `supertype`. Think of a class as a blueprint for an object, and a supertype gives that blueprint functionality you have already defined. If Duck's supertype is `Animal` Duck automatically gets every variable and function that `Animal` has, in addition to its own.

Define a supertype by putting it after the class name `Duck: Animal {`

```swift
// All objects in Swift should have supertype `NSObject`. Don't ask cause I forget why.
class Animal: NSObject {
  var planet = "Earth"

  func speak() {
    print("I don't know what kind of animal I am.")
  }
}

// Now Dog objects have access to everything Animal does; Animal is Dog's supertype.
// This can also be described as Dog is a subclass of Animal.
class Dog: Animal {

  // A subtype can have it's own variables
  var breed = "Poodle"

  // A subclass can also override it's superclass's methods. Note that in Swift if you do this
  // you need the `override` keyword in front of the function
  override func speak() {
    print("bark bark")
  }

}
```

Scope
====
When a variable is defined it can be accessed anywhere inside the curly braces where it was defined. 
```swift
class TacoBell {
  var numberOfTacos = 13983
  
  func buyNewTacos() {
    let newTacos = 100
    // numberOfTacos is accessible here because it is inside the curly braces ("in scope")
    numberOfTacos = numberOfTacos + newTacos
  }
  
  func stupidFunction() {
    // This will not work; new tacos is defined in the function above
    // and not in scope.
    print(newTacos)
    
    // This is fine; numberOfTacos is in scope
    print(numberOfTacos)
  }
  
}
```
self
====
Sometimes there can be conflicting variables (two separate variables with the same name).
When this happens and you try and access the varable of that name the program will give you
the one that is closest in scope (the lowest level of curly braces in relation to the access).

When inside of an Object (inside a class) you can access instance variables (variables that are 
defined in the object at the top level) using the keyword `self`. `self` just refers to whatever
object you are inside and can be used like any other variable.
```swift
class Chair: NSObject {
  var legs = 4
  
  func addLegs(legs: Int) {
    // Notice here there are two variables in scope that are named `legs`. One is the object's property
    // another is the function parameter. The function parameter is closest in scope so thats the one
    // that will be accessed if you try and use `legs`
    print(legs) // will print the funtion parameter; whatever value it is
  }
  
  func selfExample() {
    let legs = 10
    
    // use self to first access the object you are in, and then access its legs property with .legs.
    // then set that equal to `legs` which is 10 in this case because thats the closes `legs` in scope.
    self.legs = legs
  }
}
```

Aside: Camel Case
====
When defining variables and functions use camel case; capitalize the first letter of every word except the first one.
`coolVariableName` = good
`bAdVaRiAbLename` = bad

For classes do the same thing except capitalize the first letter of the first word as well.

`class GreatClass` = good
`class stupidClassName` = bad
`class YELLINGCLASS` = bad

super
====
just like the keyword `self` can access the current object, the keyword `super` can access the supertype of the current 
object. This is useful for acessing things you have overridden, such as initializers.
```swift
class SpaceShip: NSObject {
  var crewMembers: Int
  init(crewMembers: Int) {
    // If this looks confusing see scope section above
    self.crewMembers = crewMembers
  }
}

class MilleniumFalcon: SpaceShip {

  var pilotName: String

  // Han Solo, obviously
  init(pilotName: String) {
    self.pilotName = pilotName
    
    // Access the supertype's init, since crewMembers still needs to be initialized (needs a value).
    super.init(crewMembers: 1)
  }
}
```

Subclassing pt. 2
====
One of the benefits of subclassing is that you can save a lot of code writing by reusing functionality from other objects.
i.e. write most of what you need for a `Cat` and `Dog` class in an `Animal` class and then add a few specific things
to the `Cat` and `Dog` classes. You can also assign objects of different types to the same variable as long as they have a 
common superclass and that variable is that type.
```swift

class Animal {}
class Dog: Animal {}
class Cat: Animal {}


let cat = Cat() // `cat` is now of type Cat
let dog = Dog() // `dog` is now of type Dog

let cat = dog   // this will fail because types Dog and Cat are different

let animal: Animal = Cat() // The type of `animal` is Animal because we explicitly defined it to be. The program also has
                           // no problem assigning a `Cat` to an `Animal` object because `Cat` is a subtype of `Animal`
                           
animal = dog    // this will work now since dog is of type `Dog` and `Dog` is an `Animal`.

```
