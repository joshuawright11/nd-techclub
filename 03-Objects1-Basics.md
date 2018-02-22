*February 22nd, 2018*

Objects
====
```swift
/* Defining an Object */

// Blueprint for a TodoItem object that we might use for our todo list
class TodoItem: NSObject { // Most Swift objects need to have : NSObject after their definition. Will explain someday later
    
    // Define variables of the Object here. Each todo item has a name and an isCompleted (that keeps track of if it is 
    // completed)
    //
    // A variable inside an Object is also called a 'property' of that object (here `name` is a property of `TodoItem`)
    var name: String
    var isCompleted: Bool
    
    // This is an 'initializer' and is how you create an object. Remember, a `class` is a blueprint for an object. To create
    // an object to use you need to call the initializer. This creation process is called 'instantiation' and the created 
    // object is an 'instance' of it's type.
    //
    // The format for calling an initializer (and thus creating an object) is ObjectTypeName(). In this case it would be
    // TodoItem(). This would return a TodoItem with `name` and `isCompleted` properties for you to use.
    init() {
        name = "A default name"
        isCompleted = false
    }
}

/* Creating an Object */
let myTodoItem = TodoItem() // Initializes a TodoItem using the function `init` from above
print(myTodoItem.name) // will print "A default name" since that's what we set it to in the initializer

myTodoItem.name = "New name"

print(myTodoItem.name) // will print "New name". Properties of Objects can be modified just like any variable. Objects are 
                       // essentially a variable that contains multiple other variables, as defined in the class you create.

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

