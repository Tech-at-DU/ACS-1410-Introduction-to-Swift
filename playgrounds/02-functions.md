# Swift Functions

Functions are blocks of code that you define for use later. Functions are a core programming building block! 

## Defining functions 

Functions in Swift are defined with the keyword `func`. 

A function has a code block. All of the code in the code block is executed when the function is invoked. Maybe this needs an example to add the following to a playground or into one of the online playgrounds. 

```Swift 
func sayHello() {
 print("Hello World")
}
```

Run your playground and you will notice nothing happens. 

The code between `{` and `}` is called a block. This code block is run when the function is invoked. Invoke a function like this: 

```Swift
func sayHello() {
 print("Hello World")
}

sayHello() // prints Hello World
```

You can invoke a function as many times as you like, try this. 

```Swift 
sayHello() // prints Hello World
sayHello() // prints Hello World
sayHello() // prints Hello World
sayHello() // prints Hello World
sayHello() // prints Hello World
```

You can run the code in a function as many times as you like. 

## Parameters and arguments

Functions allow us to pass values into the function to customize its behavior. This makes functions very useful.

Parameters are variables that you define along with your function and arguments are the values that are assigned to parameter variables when you invoke a function. 

```Swift 
func greet(name: String) {
 print("Hello \(name) glad to meet you!")
}

greet(name: "Joe")
greet(name: "Wendy")
greet(name: "Frango")
```

Output:

```
Hello, Joe glad to meet you!
Hello, Wendy glad to meet you!
Hello, Frango glad to meet you!
```

Look at the `greet` function. Notice that inside the parentheses you defined a parameter variable: `name` as type `String`.

You set the value of this variable outside of the function with a string, this is the argument. 

## Scope

The scope is a term that describes where a variable can be accessed within your program. The variable `name` in this example is only accessible inside the `greet` function and doesn't exist outside of it. 

```Swift
func greet(name: String) {
 print("Hello \(name) glad to meet you!")
}

print(name) // Error: Cannot find 'name' in scope
```

Trying to access it outside causes an error. 

This makes sense since `name` is assigned a value when you call the function. Without calling the function `name` will not get a value. Also, `name` doesn't exist anymore after the function ends. 

## Return 

Functions can also return a value. 

```Swift 
func area(width: Int, length: Int) -> Int {
 let totalArea = width * length
 return totalArea
}

area(width: 12, length: 8)
```

The return type follows the `()` with `->`. In the example, the return type is `Int`. If your function doesn't return an `Int` you'll see an error. 

Try the code above. Notice that it works but you don't see anything in the console. When a function returns a value your program has to do something with that returned value. You can assign it to a variable or pass it as a parameter to another function. 

Try this: 

```Swift 
func area(width: Int, length: Int) -> Int {
 let totalArea = width * length
 return totalArea
}

let kitchen = area(width: 12, length: 8)
print("Kitchen area = \(kitchen)")
print("Bathroom area = \(area(width: 5, length: 6))")
```

Try the example above. Notice the kitchen area is calculated by calling the `area()` function. The value returned is assigned to `kitchen` and the type is inferred as `Int`!

In the second example, the bathroom area is calculated and the return value is concatenated inside the string! 

## Calorie calculator function 

Time to improve the calorie calculator. If you were going to create an app that calculated your daily calories burned from the number of steps you would write a function to do the calculation! 

Try this:

```Swift
func showCalories(name: String, steps: Int) {
 let stepsPerCalorie: Int = 20
 let caloriesPerStep: Double = 1 / Double(stepsPerCalorie)
 let caloriesForDay: Double = Double(steps) * caloriesPerStep
 let message: String = "Great job \(name) you burned \(caloriesForDay) today!"
 print(message)
}

showCalories(name: "Mitchell", steps: 8332)
showCalories(name: "Mitchell", steps: 1216)
showCalories(name: "Mitchell", steps: 8082)
showCalories(name: "Mitchell", steps: 7686)
```

The output looks like this: 

```
Great job Mitchell you burned 416.6 today!
Great job Mitchell you burned 60.800000000000004 today!
Great job Mitchell you burned 404.1 today!
Great job Mitchell you burned 384.3 today!
```

What is happening here? I wrote a function that accepts two parameters: name: String and steps: Int. 

The function declares some "local" variables: stepsPerCalorie: Int, caloriesPerStep: Double, caloriesForDay: Double, and message: String. 

Then it prints the results. 

Important! variables declared inside of a function are "scoped" to the function. We call them "local" variables. They only exist within that function and are discarded after the function completes. I declared all of these variables with `let` making them constants. This is good and works because they are not mutated!

The output of line 2 "Great job Mitchell you burned 60.800000000000004 today!" looks a little strange. The computer is telling me:

```
1216 * 1 / 20 = 60.800000000000004
```

This seems a little strange but it's exactly correct, for binary numbers! 

You'll see this happen with floating-point numbers in software. Computers calculate numbers with base 2 instead of base 10. 

You are not surprised when `10 / 3 = 3.3333333...". The same thing is happening here. 

How do we fix it? You can use the `round()` function. Try this: 

```Swift 
func showCalories(name: String, steps: Int) {
 ...
 let caloriesForDay: Double = Double(steps) * caloriesPerStep
 let calories: Double = round(caloriesForDay)
 let message: String = "Great job \(name) you burned \(calories) today!"
 ...
}
```

Here you defined a new variable `calorie` which will hold the rounded value to display. You passed `caloriesForDay` as an argument to this function and it returned the rounded value. Last you used the new value in the message string. 

The `round()` function works just like the functions you wrote, but it's built into the language. There are many built-in functions! They all take arguments of type and return a value of a type. 

**Be a better programmer today! Do this: When you see a function or write a function ask yourself what arguments does it take? and what does it return? Be an even better programmer by identifying the types!**

## Challenge 

The function above works but needs some improvement. The output looks like this: 

```
Great job <name> you burned <calories> today!
```

It would be better if it read: 

```
Great job <name> you took <steps> steps and burned <calories> today!
```

Modify the function to do this. 

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

Solution:

```Swift
let message: String = "Great job \(name) you took \(steps) steps and burned \(calories) today!"
```

## Challenge 

We lost the day of the week. The application we are building would be more useful to people if it also displayed the day of the week with the steps and calories. 

The function above it displays: 

```
Great job <name> you took <steps> steps and burned <calories> on <day>
```

To do this you can add a new parameter `showCalories` that accepts the day of the week as a string. You can use the day string in the message. 

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

Solution: 

```Swift
func showCalories(name: String, steps: Int, day: String) {
 ...
 let message: String = "Great job \(name) you took \(steps) steps and burned \(calories) on \(day)"
 ...
}

showCalories(name: "Mitchell", steps: 8332, day: "Tuesday")
...
```

## Programming with Functions

When writing functions it is better to write shorter functions that do one thing. Longer functions that do many things are not as useful and harder to understand and debug. 

The `showCalories` function does three things currently: 

- calculates the number of calories from the steps 
- creates a message string
- displays the message

It would be better for you to create two new functions. One to calculate the number of calories, and another to generate the message string. You will keep the original function and it will be responsible for displaying the message. 

Write a new function `calculateCaloriesFrom`. This function takes in steps: Int and returns caloriesForSteps: Double. 

```Swift
func calculateCaloriesFrom(steps: Int) -> Double {
 let stepsPerCalorie: Int = 20
 let caloriesPerStep: Double = 1 / Double(stepsPerCalorie)
 let caloriesForSteps: Double = Double(steps) * caloriesPerStep
 return caloriesForSteps
}
```

This was all code from the previous function. You can remove that code and call this function from `showCalories`. 

```Swift
func showCalories(name: String, steps: Int, day: String) {
 let caloriesForDay: Double = calculateCaloriesFrom(steps: steps)
 let calories: Double = round(caloriesForDay)
 let message: String = "Great job \(name) you took \(steps) steps and burned \(calories) on \(day)"
 print(message)
}
```

The value of `caloriesForDay` is now set by the value returned from `calculateCaloriesFrom` on line 1. This is a common pattern in programming! It's the same thing that happened when you used `round`!

Write a new function `getCaloriesMessage` that takes the parameters name, steps, calories, and day, and returns a string. The string should be the same as the message string defined earlier. 

Then call the new `getCaloriesMessage` function in `showCalories` and assign the return value to the `message` variable. 

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-


Solution:

```Swift
func calculateCaloriesFrom(steps: Int) -> Double {
 let stepsPerCalorie: Int = 20
 let caloriesPerStep: Double = 1 / Double(stepsPerCalorie)
 let caloriesForSteps: Double = Double(steps) * caloriesPerStep
 return caloriesForSteps
}

func getCaloriesMessage(name: String, steps: Int, calories: Double, day: String) -> String {
 return "Great job \(name) you took \(steps) steps and burned \(calories) on \(day)"
}

func showCalories(name: String, steps: Int, day: String) {
 let caloriesForDay: Double = calculateCaloriesFrom(steps: steps)
 let calories: Double = round(caloriesForDay)
 let message: String = getCaloriesMessage(name: name, steps: steps, calories: calories, day: day)
 print(message)
}

showCalories(name: "Mitchell", steps: 8332, day: "Tuesday")
showCalories(name: "Mitchell", steps: 1216, day: "Wednesday")
showCalories(name: "Mitchell", steps: 8082, day: "Thursday")
showCalories(name: "Mitchell", steps: 7686, day: "Friday")
```

## Conclusion 

Functions are a core part of programming. One of the most important features you will use after variables. Let's review what was covered here. You should this whole page again the ideas are that important! 

Here is what was covered in this lesson. 

- Functions are the building blocks that make up the programs you will write! 
- Functions are named like variables. 
- A function in Swift begins with the word `func`
- The name is followed by the `()` as in `func myFunc()`
- Then comes the `{}` for example `func myFunc() { }`
- A function contains code in a block `{ ... code here ... }`
- The code in the code block is run when we invoke the function with its name `myFunc()`
- Parameters are variables that are defined in a function
 - put parameters in the `()`
 - include the type when defining a parameter
 - for example `func myFunc(name: String)`
- A function can return a value.
 - The return type follows the `()` with `->` 
 - Return a value at the end of your function with the word `return`
 - for example: `func myFunc(name: String) -> { return "Hello \(name)" }`
