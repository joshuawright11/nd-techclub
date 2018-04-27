UIViewController
====
In iOS apps each screen is represented by a view controller (VC). Each view controller is a class that subclasses UIViewController.

There are 2 main types of view controllers:
- *basic `UIViewController`s*: used to display just about anything
- *`UITableViewController`s*: used to display lists of data

To make a screen make a new viewcontroller in the Storyboard file, make a new file that is a subclass of UIViewController, and then set the subclass name in the Storyboard view's class

Moving Between VCs
====
To transition between VCs (transitioning between screens) you can use one of 3 ways:
1. *"Segues" in Storyboard*: Create a segue in the storyboard linking two VCs. Give the segue an identifier. Then in your code call `performSegue(withIdentifier: "myIdentifierName")` to transition to the new VC.
2. `present(vc: UIViewController)` and `dismiss()` inside a viewcontroller class. Pass a `UIViewController` instance to present in order to present the new VC over the old one. Call dismiss() inside of a viewController to dismiss it, revealing whatever UIViewController is under it.
3. `UINavigationController` If your VC is wrapped in a UINavigationController (Drag Nav into storyboard, cntrl drag to the VC you want to wrap) instead of calling present() and dismiss() you can call `navigationController.push(vc: UIViewController)` and `navigationController.pop()` to have the same effects as `present` and `dismiss` respectively. Instead of presenting over the current VC however, it will slide the newVC over from the left, inside the `UINavigationController`.