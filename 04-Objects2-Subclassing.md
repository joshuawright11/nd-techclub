*March 1st, 2018*

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
