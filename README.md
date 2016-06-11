# Array Methods

![Drawing](http://www.achievement.org/achievers/ang0/large/ang0-003.jpg)

> We delight in the beauty of the butterfly, but rarely admit the changes it has gone through to achieve that beauty.

## Learning Objectives - The student should be able to..

- `append()` - add element to the end of the array.
- `insert(_:atIndex:)` - insert an element at the specified index.
- `removeAtIndex()` - remove an element at the specified index.
- _Subscript Syntax_ to change elements at a specified index and access the element at a specified index to store in a variable.

```swift
var numbers = [5, 2, 3]
numbers[0] = 1

let thirdNumber = numbers[2]
// 3
```

- `count` - Returns the number of elements in the array.
- `isEmpty` - Returns true if the array is empty.

## What the student can do at this point

- Create variables and constants
- Is familiar with type annotations, type inference and string interpolation.
- Can create functions with return types.
- Is familiar with the String, Int, Double, and Bool type.
- Can perform arithmetic operations on Int and Double.
- Understands if and else clause statements.
- Can create and use Arrays.
- Can iterate over an Array using a for-in loop.
- Can iterate over an Array calling enumerate().

## Outline / Notes

- The student will not have read about structs or classes (yet) so I don't want to go too deep in an explanation of computed properties and instance methods but I think we might need to give them a short definition as they will be using them fully in this reading.
- I think it's important for them to know that they must use var here in that we need the array to be mutable in order to add anything to it. Show them a screenshot of the error they would receive if they tried using append where toys would be declared with let.

```swift
 var toys = ["Woody", "Buzz Lightyear", "Mr. Potato Head", "Slinky Dog"]
 toys.append("Rex")

 // ["Woody", "Buzz Lightyear", "Mr. Potato Head", "Slinky Dog", "Rex"]
```

- Speaking about the `insert(_:atIndex:)` method. I think it's important for them to see and recognize that calling the method like I did below inserting an element at index 0 will NOT replace the element that is currently there, it will insert it at that specific index and shift everything to the right.

```swift
 toys.insert("Tom Hanks", atIndex: 0)

 // ["Tom Hanks", "Woody", "Buzz Lightyear", "Mr. Potato Head", "Slinky Dog", "Rex"]
```

- They can then remove an element at a specified index consideirng now that Tom Hanks is not a character in the film, he is the voice of Woody.... so we need to remove him.

```swift
 toys.removeAtIndex(0)

 // ["Woody", "Buzz Lightyear", "Mr. Potato Head", "Slinky Dog", "Rex"]
```

- If instead they wanted to change an element at a specific index, they would so so as follows:

```swift
 var names = ["James", "Sarah", "Bran", "Sansa"]

 names[0] = "Jim"

 // ["Jim", "Sarah", "Bran", "Sansa"]
```

- I think it's important for them to see the error they would receive IF they tried updating a value at a certain index that is out of bounds. Or if they try accessing an element that could be out of bounds. They might then wonder HOW they can in fact make sure they are within bounds and we COULD show them this but I'm very very reluctant in explaining to them exactly what is going on here as the next lesson will introduce optionals (which is usually the hardest thing for them to grasp). **OPINION WANTED**: Do you think we should at the very least show them something like this?:

```swift
 if let index = names.indexOf("Jim") {
    names.removeAtIndex(index)
 }

 // ["Sarah", "Bran", "Sansa"]
```

- Referring to `count`, they should be exposed to the following where it is explained thoroughly what is going on:

```swift
let rainbowColors = ["Red", "Orange", "Yellow", "Green", "Blue", "Indigo", "Violet"]

 let numberOfColors = rainbowColors.count
 // 7

 print("There are \(numberOfColors) colors in the rainbow.")
 // prints "There are 7 colors in the rainbow.

 if rainbowColors.count > 5 {
    print("There are more than 5 colors in a rainbow.")
 }
 //prints "There are more than 5 colors in a rainbow."
```

- Referring to `isEmpty` - I like the idea of stepping them through the following two examples:

![deliLine](http://i.imgur.com/ivgaSon.png?1)

```swift
 var deliLine = [
    "Albert Einstein",
    "Isaac Newton",
    "Galileo Galilei",
    "Marie Curie"
 ]

 if deliLine.isEmpty {
    print("The deli line is empty")
 } else {
    print("There are people waiting to eat!")
 }

 // prints "There are people waiting to eat!"
```

![Moons](http://i.imgur.com/reNsnn6.png?1)

```swift
 let moonsOfJupiter = [
    "Europa",
    "Ganymedge",
    "Io",
    "Callisto"
]

 if !moonsOfJupiter.isEmpty {
    for moon in moonsOfJupiter {
        print("\(moon) is a moon orbiting Jupiter.")
    }
 }

 // Europa is a moon orbiting Jupiter.
 // Ganymede is a moon orbiting Jupiter.
 // Io is a moon orbiting Jupiter.
 // Callisto is a moon orbiting Jupiter.
```

---

In the last lesson you briefly saw a 'method', which can be thought of as a pre-written function that helps you accomplish common tasks. They are contextual, in that a method that works on an array may not work for a String for example.

The method you saw in the last example was `.append()` to add a value to the end of an array. This could be done in alternative ways, all of which would involve far more code and calculation, I think you'll agree that `.append()` is far more convenient. There are many other methods for arrays, and in this lesson we'll look at some others.

## Enumeration

Before going any further, there's one other array concept to introduce.

Say you have a list of instruction steps, if steps need to be added, removed, or changed at a particular index in the array, then you need to know what the index of the value is. When you have a simple list of unchanging values, then maybe this is simple, but with a larger list processed in a loop, there is another way, you can use the `.enumerate` method to have not only teh value of the current loop index, but the index position itself.

```swift
var toMakeTea = [
    "Boil Water",
    "Add tea bag to cup",
    "Wait ten minutes",
    "Add Milk",
    "Drink"
]

for (index, step) in toMakeTea.enumerate() {
    print("\(index + 1). \(step)")
}

// 1. Boil Water
// 2. Add tea bag to cup
// 3. Wait ten minutes
// 4. Add Milk
// 5. Drink
```

In this example you first create an array of the steps to make tea (and yes, there are intentional mistakes!) and add a couple of extra things to the `for in` loop. First inside the brackets you add variables to hold the index and value variables, the names of these are arbitary, `index` is of course a useful name, but it could be called whatever you want. At the end of the array name you want to iterate through, add the `.enumerate()` method. Now inside the loop you have access to the value in the current iteration as well as it's index in teh array. In this example '1' is added to the index value as unlike computers, humans don't count from 0!

## Add Items to an Array

You saw this method in the last lesson, but let's quickly look at it again. You missed an important step in the list above, telling people to enjoy their tea, so add it to the end of the array:

```swift
toMakeTea.append("Enjoy!")
print(toMakeTea)
// ["Boil Water", "Add tea bag to cup", "Wait ten minutes", "Add Milk", "Drink", "Enjoy!"]
```

The `.append()` method adds a new value (which has to also be the same type as every other value) to the end of the array.

You have also forgotten an important step at the begining of the list, adding water to the kettle, so let's add it:

```swift
toMakeTea.insert("Add water to kettle", atIndex: 0)
print(toMakeTea)
// ["Add water to kettle", "Boil Water", "Add tea bag to cup", "Wait ten minutes", "Add Milk", "Drink", "Enjoy!"]
```

[View this lesson on Learn.co](https://learn.co/lessons/ArrayMethods)
