*October 24, 2017*

Protocols
====
Also called 'interfaces' in other languages, protocols are a way to define a type without actually implementing it (implementing is simply
filling in methods and variables)

A `protocol` is used for defining information about a type and then can be 'implemented' by an object to conform to that type. They are 
kind of like classes except for 2 main differences:

1. A protocol doesn't have any of its functions or variables implemented (i.e. the class implementing them needs to explicitly define them
in its file. *see below*)
2. An object can implement AS MANY protocols as it wants. Try to thing of protocols as "adjectives" describing what the object can do, 
while supertypes define what the object IS. Example:
```swift


class Cat: Animal {...}
// A Cat is now of type Animal. AKA a Cat IS an Animal. This is an appropriate case for subclassing.

// A protocol is defined just like a class, except none of the functions are filled out
protocol Edible {
  // A function that cooks an object and then returns a string of what food it makes
  // ignore the `{get, set}` for now
  var foodProduct { get, set }
}

// This defines a Chicken, of type animal, who is Edible.
class Chicken: Animal, Edible {
  // Because we implement protocol `Edible` we need this variable defined in the class
  var foodProduct = "Chicken tenders"
}

class Oven: NSObject {
  func cook(food: Edible) -> String {
    return food.foodProduct
  }
}

let chicken = Chicken()
let oven = Oven()

let dinner = oven.cook(food: chicken)

print("Dinner tonight is: \(dinner)")

```

Creating Programs
====
1. Define the views
2. Define the models

