#Fundamentals

##Variables

As with every programming language you have variables which allow you to store data. To declare a variable you have to use the 	  keyword var.

|var greeting: String = "Hello World"

The above code instructs the system that you want to create a variable named greeting which is of type String and it will contain * * the text, “Hello World”.

Swift is smart enough to infer that if you are assigning a string to a variable and in fact that variable will be of type string. So * you need not explicitly specify the type as in the above example. A better and common way of writing the above example would be:

| var greeting = "Hello World" // Inferred type String

Variables can be modified once created so we could add another line and change our greeting to something else.

| var greeting = "Hello World" // Inferred type String

 greeting = "Hello Swift"

 While writing an application there are many instances where you don’t want to change a variable once it has been initialized. Apple has always had two variants of types mutable and immutable. Mutable meaning the variable can be modified and immutable that it cannot be modified. They prefer immutability by default which means that the values aren’t going to change and it makes your app faster and safer in a multi-threaded environment. To create an immutable variable you need to use the keyword let.

 If we change our greeting example to use let instead of var then the second line will give us a compiler error because we cannot modify greeting.

| let greeting = "Hello World"

 greeting = "Hello Swift" //Compiler error

Lets take another example so you understand why and when to use let.

| let languageName: String = "Swift"

| var version: Double = 1.0

| let introduced: Int = 2014

| let isAwesome: Bool = true

*The above example not only shows us the various types that are available in Swift but it also shows us that the reason to use let. Aside from the version number of the Swift language everything else remains constants. You might argue that isAwesome is debatable but I’ll let you reach that conclusion once you reach the end of this post.

Since the type is inferred we should simply write:

let languageName = "Swift" // inferred as String

var version = 1.0 // inferred as Double

let introduced = 2014 // inferred as Int

let isAwesome = true // inferred as Bool
Strings

In our above example we have been writing the String type. Lets see how we can concatenate two strings by using the + operator.

let title = "An Absolute Beginners Guide to Swift"
let review = "Is Awesome!"
let description = title + " - " + review
// description = "An Absolute Beginners Guide to Swift - Is Awesome!"
Strings have a powerful string interpolation feature where it’s easy to use variables to create strings.

let datePublished = "June 9th, 2014"

let postMeta = "Blog Post published on: \(datePublished)"

// postMeta = "Blog Post published on: June 9th, 2014"
In all the above examples, I have been using the keyword let which means you cannot modify the string once it has been created. However, if you do need to modify the string then simply use the keyword var.

Other Types

Besides strings you have Int for whole numbers. Double and Float for floating-point numbers and Bool for boolean values such as: true of false. These types are inferred just as a string so you need not explicitly specify them when creating a variable.

A Float and Double vary in precision and how large of a number you can store.

## Float:
represents a 32-bit floating-point number and the precision of Float can be as little as 6 decimal digits.
Double: represents a 64-bit floating point number and has a precision of at least 15 decimal digits.
By default when you write a floating-point number it is inferred as a Double.

var version = 1.0 // inferred as Double
You can explicitly specify a Float.

var version: Float = 1.0
Collection Types

## Array

Collections come in two varieties. Firstly, an array which is a collection of data items which can be accessed via an index beginning with 0.

var cardNames: [String] = ["Jack", "Queen", "King"]

// Swift can infer [String] so we can also write it as:

var cardNames = ["Jack", "Queen", "King"] // inferred as [String]
You can create two types of arrays: an array of a single type or an array with multiple types. Swift is keen on being safe so it prefers the former but can accommodate the later with generic types. The example above is an array of strings which means that it is a single type array.

To access an item from the array you need to use the subscript:

println(cardNames[0])
Note: we used a function above called println which will print the value “Jack” to the console and then add a new line.

## Modifying an Array

Lets create a new array that contains a todo list.

var todo = ["Write Blog","Return Call"]
Make sure that you use the keyword var so that we can modify our array.

To add another item to our todo array we use the ‘+=’ operator:

todo += "Get Grocery"
To add multiple items to our todo array we simply append an array:

todo += ["Send email", "Pickup Laundry"]
To replace an existing item in the array simply subscript that item and provide a new value:

todo[0] = "Proofread Blog Post"
To replace an entire range of items:

todo[2..<5] = ["Pickup Laundry","Get Grocery", "Cook Dinner"]
Dictionary

The other collection type is a Dictionary which is similar to a Hash Table in other programming languages. A dictionary allows you to store key-value pairs and access the value by providing the key.

For example, we can specify our cards by providing their keys and subsequent values.

var cards = ["Jack" : 11, "Queen" : 12, "King" : 13]

Above we have specified the card names as the keys and their corresponding numerical value. Keys are not restricted to the String type, they can be of any type and so can the values.

## Modifying a Dictionary

What if we wanted to add an “ace” to our cards dictionary? All we have to do is use the key as a subscript and assign it a value. Note: cards is defined as a var which means it can be modified.

cards["ace"] = 15
We made a mistake and want to change the value of “ace”. Once again just use the key as the subscript and assign it a new value.

cards["ace"] = 1
To retrieve a value from the dictionary

println(cards["ace"])
Control Flow

## Looping

What it good is a collection if you cannot loop over it? Swift provides while, do-while,for and for-in loops. Lets take a look at each one of them.

The easiest one of them is the while loop which states while something is true execute a block of code. It stops execution when that condition turns to false.

while !complete
{
|	println("Downloading...")
}
Note: the exclamation mark before the variable complete denotes not and is read as “not complete”.

Likewise, you have the do-while loop which ensures that your block of code is executed at least once.

var message = "Starting to download"
do {
|	println(message)
|	message = "Downloading.."
} while !complete 

Subsequent calls to the println statement will print “Downloading..”

You have the regular for loop where you can specify a number and increment that number to a certain value:

for var i = 1; i < cardNames.count; ++i
{
	| println(cardNames[i])
}
Or you can simply use the for-in variant where it creates a temporary variable and assigns it a value while iterating over the array.

for cardName in cardNames
{
|	println(cardName)
}
The above code will print out all the card names in the array. We can also use a range. A range of values is denoted by two dots or three dots.

## For example:

1…10 – is a range of numbers from 1 to 10. The three dots are known as a closed range because the upper limit is inclusive.
1..<10 – is a range of numbers from 1 to 9. The two dots with a lesser-than sign is known as a half-closed range because the upper limit is non-inclusive.

Lets print out the 2 times table using for-in with a range:

for number in 1...10 
{
|	println("\(number) times 2 is \(number*2)")
}

We can also iterate over the cards dictionary to print out both the key and the value:

for (cardName, cardValue) in cards
{
|	println("\(cardName) = \(cardValue)")
}

## If Statements

To control the flow of our code we of course have an if statement.

if cardValue == 11 {
		println("Jack")
} else if cardValue == 12 {
		println("Queen")
} else {
		println("Not found")
}

Note: The if syntax can have parenthesis but they are optional. However, the braces {} are mandatory unlike other languages.

## Switch Statement

The switch statement in Swift is very versatile and has a lot of features. Some basic rules about the switch statement:

It doesn’t require a break statement after each case statement
The switch is not limited to integer values. You can match against any values such as: String, Int, Double or any object for that matter.
The switch statement must match against every value possible if not you must have a default case which makes your code safer. If you don’t provide a case for every value or a default then you will get a compiler error saying: “switch must be exhaustive”.
switch cardValue {
	case 11:
		println("Jack")
	case 12: 
		println("Queen")
	default:
		println("Not found")
}

Lets say you have a distance variable and you are trying to print a message based on distance. You can use multiple values for each case statement:

## switch distance {
	case 0:
		println("not a valid distance")
	case 1,2,3,4,5:
		println("near")
	case 6,7,8,9,10:
		println("far")
	default:
		println("too far")
}

There are times when even multiple values are limiting. For those instances you can use ranges. What if any distance greater than 10 and less than 100 was considered far?

switch distance {
	case 0:
		println("not a valid distance")

	case 1..10:
		println("near")

	case 10..100 :
		println("far")

	default:
		println("too far")

}
Can you guess what the above code will print?

## Functions

Finally, we have been using println in a lot of our examples which is an example of how to use a function. But how can you create your own function?

It is simple, you have to use the keyword func and provide it with a name.

func printCard() {
	println("Queen")
}
What good is a function if it always going to just print “Queen” as the card name. What if we want to pass it a parameter so it can print any card name?

func printCard(cardName: String) {
	println(cardName)
}
Of course, we are not restricted to just one parameter. We can pass in multiple parameters:

func printCard(cardName: String, cardValue: Int) {
	println("\(cardName) = \(cardValue)")
}

What if we simply wanted our function to build a string and return the value instead of printing it? Then we can specify a return it which is specified at the end of the function declaration followed by an array ->.

func buildCard(cardName: String, cardValue: Int) -> String {
	return "\(cardName) = \(cardValue)"
}
Above we are saying that we are creating a function named buildCard which takes in two parameters and returns a String.
