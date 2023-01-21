# Playgrounds

The playgrounds from the original repo are sometimes problematic. This folder contains some alternative code that can be run in an online playground or in a playground you create. 

The purpose is to make it easier to follow the playground's lessons with fewer problems.

In XCode choose: File > New > Playground

Or try one of these websites: 

- https://online.swiftplayground.run
- https://swiftfiddle.com
- https://www.jdoodle.com/execute-swift-online/

You'll enter the code from the examples, run your code, and looks for the results. All of the tools above do this differently but mostly you will run the code by clicking a Run or execute button that probably looks like this: >. 

## Variables and values 

A variable is a name for a value that you need your program to remember. 

Variable names must begin with a letter, can only contain letters and numbers, (most) special characters (like *, /, +, =<, etc. you can use _, and $)

Naming your variables is very important! Giving them good descriptive names will help you understand the code that you write and avoid errors! 

## var and let

Just like the languages you speak have rules programming languages have rules. The first time you mention a variable you have to declare it with one of the keywords `var` or `let`. Try it for yourself. This is like starting a sentence with an uppercase letter. 

Add the following in your code editor. 

```Swift
var score = 0
let name = "your name here"
```

Notice I declared `score` with the keyword `var` and the `name` variable with `let`.

Use `var` the value stored in a variable will change. For example, if you were making a game the score would change. 

Use `let` when a variable won't change. For example, your name doesn't change. 

To display the value of a variable use `print()`. This is a function. Functions always end with the `()`. Try this: 

```Swift
print(score)
print(name)
```

The `=` is an operator. Other operators are `-`, `*`, `+`, and `/`. We use these to form expressions. An expression is like a sentence of code. 

The `=` is the assignment operator. It assigns the value on the right to the variable on the left. Here you assigned 0 to score and "your name here" to name. 

Your programs will often change the values of variables over time. To do this use the `=` operator. 

Add this: 

```Swift
var score = 0
let name = "your name here"
print(score)
print(name)
score = 50
print(score)
```

You should see this output: 

```
0
your name here
50
```

The first time you printed score the value was 0. On line 5 you assigned a new value to score. On line 6 you printed score again and the current value of 50 was displayed. 

Important! The code you write is executed line by line in order. 

```Swift
// Doesn't work! 
print(score)
var score = -100
```

The code above doesn't work because it is using the variable `score` before it has been declared and assigned a value!

# What about let?

Often you will use variables that won't change their value. In these cases use `let`. 

Try this: 

```Swift
name = "joe"
```

Running the code above generates an error. 

```
error: cannot assign to value: 'name' is a 'let' constant
name = "joe"
^~~~
note: change 'let' to 'var' to make it mutable
let name = "your name here"
^~~
var
```

The error message uses the term "mutable" to describe a variable that can be changed and immutable or constant for something that doesn't change. 

Why make variables that don't change? They are more efficient! The computer does less work and uses less memory when it knows a value can not be "mutated."

It also prevents errors if you know that a value should not be changed, you can declare it with `let` and you'll get an error if a line of code tries to change it! 

## Types 

Computers store values but these values have a type. Generally, there are three value types strings, numbers, and everything else! 

### Strings 

Strings are literal values. A string is a list of characters. An example would be `name` above: "Your name here". A string begins and ends with `"` and `"`. Everything between the quotation marks is the value. 

Use strings for literal values like names or things. 

### Numbers

Numbers are... numbers. There is a large variety of numbers for computer reasons. You can divide these Floating point numbers and integers. 

Integers are always whole numbers, for example, 0, -55, 99, 2023. Use these when a fraction is not acceptable! For example, 2023.4 doesn't make any sense. You can't put 3.5 apples into your shopping cart. 

Floating point numbers have a decimal, for example, 1.0, 5.4003, 3.1456. Use these when accuracy is important. You might use a float for money, geolocation, temperatures, etc. 

There are a few different floating point number types. The two most common are Float and Double. 

## Types and type safety

Swift is a typed language. This means you can't assign a different type to a variable other than the original type it was declared with. 

For example: 

```Swift
score = "You lose"
```

```
jdoodle.swift:10:9: error: cannot assign value of type 'String' to type 'Int'
score = "You lose"
 ^~~~~~~~~~
```

**error: cannot assign value of type 'String'** Kinda says it all! 

### Declaring a type

When you declared your variables above like this: 

```Swift
var score = 0
let name = "your name here"
```

When you declare a variable you usually also declare the type. This is like: 

```Swift
var score: Int = 0
let name: String = "your name here"
```

Notice I used a colon after the name and followed with another word for the type: Int (for Integer) and String.

But you didn't use the type the first time? Swift will infer the type when it can. So if you assign a string to a variable when it is declared then Swift assumes that the type must be a string. 

```Swift
let name = "your name here" // name is type string
var score = 0 // score is type Int
```

**Be a better programmer today! When ever you see a variable ask yourself what type is this?**

## Comments 

Sometimes you'll want to add notes to your code. This is called a comment. Anything you write in a Swift file will be treated as if it were code unless you use a comment. 

```Swift 
// A constant begins with let
let name = "Your name here"
```

A comment begins with `//` and anything following is not treated as code! 

You can use comments on the same line with code if you like

```Swift 
let name = "Your name here" // name is a string
var score = 0 // score is an Int
```

## Operators and math

Operators are like the punctuation of programming. There are lots of operators it will take a while to learn them all. We will start with the math operators:

- `+` addition
- `-` subtraction
- `*` multiplication
- `/` division

And we already looked at the assignment operator:

- `=` assignment operator

Imagine you are making a fitness tracker. Turns out it takes 20 steps to burn 1 calorie. Your job is to write a program that calculates the number of calories burned and prints the results. 

To best way to do this is to put all of the values in variables, calculate the answer, and put it in a variable! 

Define the following variables: 

- name - name of the user
- stepsPerDay - number of steps today
- stepsPerCalorie - 20
- caloriesPerStep - 1 / stepsPerCalorie
- caloriesForDay - stepsPerDay * caloriesPerStep

You write the code yourself and print the `name` and `caloriesForDay`. Then check your code against mine below. 

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

Here is the first solution. This solution works but the answer is incorrect! 

```Swift
let name = "Joe"
var stepsPerDay = 10000
let stepsPerCalorie = 20
let caloriesPerStep = 1 / stepsPerCalorie
let caloriesForDay = stepsPerDay * caloriesPerStep

print(name) 
print(caloriesForDay) // Prints 0
```

This is not the correct answer but the code is working without error! What happened was it should print 500 but printed 0. 

Here I let Swift infer the types and Swift inferred that all of the numbers are type Int! 

```Swift 
let caloriesPerStep = 1 / stepsPerCalorie
```

Line 4 takes 1 (an integer) and divides by 20 (an integer) and the result is an integer 0. 

```Swift
let caloriesForDay = stepsPerDay * caloriesPerStep
```

Line 5 calculates the calories per day as 10000 * 0 and you get 0 as the answer. 

Fix this by declaring all of your values as Doubles. 

```Swift
let name = "Joe"
var stepsPerDay: Double = 10000
let stepsPerCalorie: Double = 20
let caloriesPerStep: Double = 1 / stepsPerCalorie
let caloriesForDay: Double = stepsPerDay * caloriesPerStep

print(name) 
print(caloriesForDay) // Prints 500.0
```

Wouldn't it be more accurate to use an integer for stepsPerDay since we don't count fractions of a step? Sounds reasonable. Give it a try. 

```Swift
var stepsPerDay: Int = 10000
```

This causes an error: 

```
Cannot convert value of type 'Int' to expected argument type 'Double'
```

Important! You can't do math with different types! 

Swift sees: 

```Swift
let caloriesForDay: Double = stepsPerDay * caloriesPerStep
```

as: 

```Swift
let caloriesForDay = Int * Double
```

You're not allowed to multiply an integer and a Double. 

You can fix this by "casting" your integer as a double like this: 

```Swift
let caloriesForDay = Double(stepsPerDay) * caloriesPerStep
```

Try that yourself. Make `stepsPerCalorie` type Int on line 3. On line 4 cast `stepsPerCalori` as a Double when you calculate `caloriesPerStep. 

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

Your program should look something like this:

```Swift
let name = "Joe"
var stepsPerDay: Int = 10000
let stepsPerCalorie: Int = 20
let caloriesPerStep: Double = 1 / Double(stepsPerCalorie)
let caloriesForDay: Double = Double(stepsPerDay) * caloriesPerStep

print(name)
print(caloriesForDay)
```

Go back to the top and read all of this again! The concepts here are core to all of the code that you will be writing in the future! 

## More about Strings

Your program is working well but the output would look better as "Great work <name> you burned <caloriesForDay> today!"

To do this you need to combine the values of your variables into a single string that you can print. This is called concatenation. 

Try this: 

```Swift 
let message: String = "Great job \(name) you burned \(caloriesForDay) today!"

print(message)
```

Notice that `message` is a string and the value assigned is wrapped in "". Where you want to print the value of a variable you have wrapped the variable in `\(variableName)`. 

```Swift
let name = "Joe"
let stepsPerDay: Int = 10000
let stepsPerCalorie: Int = 20
let caloriesPerStep: Double = 1 / Double(stepsPerCalorie)
let caloriesForDay: Double = Double(stepsPerDay) * caloriesPerStep
let message: String = "Great job \(name) you burned \(caloriesForDay) today!"

print(message)
```

Prints: Great job Joe you burned 500.0 today!

Without the `\()` imagine: `"Great job name you burned caloriesForDay today!"` the message printed would look like this: 

Great job name your burned caloriesForDay today!

## Challenge 

Imagine you need to calculate the number calories bunred over the lest three days. Here are the step counts for each day. 

- Wednesday steps 1216
- Thursday steps 8082
- Friday steps 7686

You need to print a message displaying the number of calories burned and the day of the week. Something like: 

```
Great job <name> you burned: 
60.8 calories Wednesday
404.1 calories Thursday
384.4 calories Friday
```

## Conclusion

Great work. The ideas here are core programming concepts! You will use them every time you sit down to write code!

You should review the ideas again! 

- Variables 
	- names must begin with a letter 
	- followed by letters and numbers
	- You should always use descriptive nams for the variables you define. 
- Declaring variables
	- The first time a variable is appears in your program you must declare it with `var` or `let`
	- Use `var` if you intend to change the value in the future.
	- Use `let` if the value should not change. We call this a constant
	- Declare a variable with using the colon: `var x: Double = 0`
	- Or Let Swift infer the type
	- Cast a variable as another type. In the example here you case an Int as a Double with `Double()`
- A variable stores a value
- Values are always typed
	- Here we looked at numbers and strings
	- Stings are any characters in the `""`
	- Numbers can be integers type `Int`
	- Or floating point numbers type `Float` or `Double`
	- A variable's type can not be changed once it has been declared.
- Operators
	- The `=` operator is the assignment operator. Use this to assign a value to a variable. 
	- use the standard math operators the same way you would use them in algebra! 
	- Math operators only apply if the values are the same type! Otherwise you get an error! 
- `print()` is a function use to print values to the console. 
- Combine string with variable values using `\()`