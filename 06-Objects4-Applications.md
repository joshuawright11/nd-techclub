Applications of Objects
====

Essentially everything you could ever want to do in a program is done using an 
object. Once you understand how objects work and how to use them in your 
program, you just need to learn the various objects that are relevant to what
you are trying to accomplish. 

Bundles of objects that you can use are called `Libraries` or `Frameworks`. Think
of these as a toolbox full of objects that can help you accomplish specfic tasks.
For example Apple has a framework called `CoreData` that is a bunch of objects 
you can use to help store data locally on your device. There is also a framework
called `UIKit` that gives you a bunch of objects to help you manage the UI 
(User Interface) of your app. Learning how to use these common objects and 
frameworks is what a good developer does.

You can also make your own objects to help manage the "State" of your program. 
By state I mean the current data that your app holds. (For example if you had
an app that counted how many times you pressed a button, the 'state' of the 
app would most likely be an Int variable that kept track of how many times the 
user pressed the button). State is often referred to as `Model`.

Logic + Model
====
Usually you can think of programs as being made up of two pieces: `Logic` and `Model`

The Logic is the part of the app that "does stuff". It responds to user input and 
modifies the Model accordingly. It also displays information about the model to 
the User.

Using objects to do Logic and represent Model
====
Objects can be used to keep track of the Model of the app, as well as perform 
actions in the app Logic.

Build a program to keep track of your homework assignments. Similar to Chopshop,
this app will be an infinite while loop that lets the user enter commands.

Use an object to represent 2 things:
- The parsing piece of the app
- The data model of the app

Also use the Apple object `DateFormatter` to help print out nice dates.