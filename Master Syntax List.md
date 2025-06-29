# C# Player's Guide Master List of Syntax

This covers the major formatting and programming guidelines outlined in RB Whitaker's C# Player's Guide (Fifth Edition)

# Quick Reference

`class` SETUP: `[accessibility level] class [ClassName] { }`

`constructor` SETUP: `[accessibility level] ClassName([optional parameters]) { }`

`property` SETUP: `[accessibility level] [type] ClassName { get{} set{} }`

# Levels 01-14: Basics

## Comments
![comments](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/comments.png)

Comment
```cs
//
```

Multi-Line Comment
```cs
/*
*/
```

## Varibles
![variable](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/variable.png)

Declare Variable
```cs
int number;
```

Initialize Variable
```cs
number = 1;
```

Declare & Initialize Variable
```cs
int number = 1;
```

Declare multiple variables simultaneously
```cs
int a, b, c;
```

Assign multiple variables simultaneously
```cs
a = b = c = 10;
```

Digit separation 
```cs
int a = 123_456_789; // (underscore is ignored by the compiler it can appear anywhere)
```

## C# Type Specifics
![types](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/types.png)

Char assignment
```cs
char aLetter = 'a';
```

Integer and conversion to literals 
- Everything smaller than an int type is automatically literal
```cs
ulong aVeryBigNumber = 1_000_000_000_000U; // U signifies it is unsigned and must be uint or ulong
aVeryBigNumber = 1_000_000_000_000L; // L signifies it is the long literal and must be long or ulong
aVeryBigNumber = 1_000_000_000_000UL; // UL signifies it must be unsigned and long, therefore, a ulong
```

Floating-point and conversion to literals (double is literal)
```cs
double number1 = 3.5623;
float number2 = 3.5623f;
decimal number3 = 3.5623m;
```

Scientific Notation
```cs
double avogadrosNumber = 6.022e23; // e stands for "exponent"
```

Convert Class and Parse Methods
```
ToByte    Byte
ToInt16   short
ToInt32   int
ToInt64   long

ToSByte   sbyte
ToUInt16  ushort
ToUInt32  uint
ToUInt64  ulong

ToSingle  float
ToDecimal decimal
ToDouble  double

ToChar    char
ToString  string
ToBoolean bool
```

## Math
![math](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/math.png)

https://csharpplayersguide.com/articles/operators-table.html

Defined Min and Max Values
```cs
int aBigNumber = int.MaxValue; // Max value that the type int can currently represent
short aBigNegativeNumber = short.MinValue; // Min value that the type short can currently represent
```

Positive and Negative Infinity
```cs
double infinity = double.PositiveInfinity;
double negInfinity = double.NegativeInfinity;
```

Not a number (NaN)
```cs
double notAnyRealNumber = double.NaN; // Used when a computation results in an impossible value
```

Unary Operators
```cs
int a = 3;
int b = -a; // results in -3
int c = +a; // no change, results in 3
```

Remainder or Modulus Operator
```cs
int leftOverApples = 23 % 3; // results in 2
```

Updating Variables
```cs
int a = 0;
a += 5; // a = a + 5
a -= 2; // a = a - 2
a *= 4; // a = a * 4
a /= 2; // a = a / 2
a %= 2; // a = a % 2
```

Postfix Increment and Decrement Operators
```cs
int a = 0;
a++; // a += 1
a--; // a -= 1
```

Prefix Increment and Decrement Operators
```cs
int x;

x = 5;
int y = ++x; // y is equal to 6

x = 5;
int z = x++; // z is equal to 5
```

Casting (going from a wide type scope to a narrow type scope)
```cs
int anInt = 3;
byte aByte = (byte)anInt; // explicit conversion, programmer is telling the compiler, force this to move to a byte
```

Casting Math operations for small types 
- Math operations are not defined for types smaller than int
```cs
short a = 2;
short b = 3;
short total = (short)(a + b);
```

Casting Math operations for integer to floating point 
- If we didn't cast the below code, it would assume integer division!
```cs
int amountDone = 20;
int amountToDo = 100;
double fractionDone = (double)amountDone/ amountToDo; // either side can cast, program will convert to double operation
```

Pi
```cs
double area = Math.Pi * radius * radius;
```

Tau
```cs
double area = Math.Tau;
```

Powers and Square Root
```cs
double x = 3.0;
double xSquared = Math.Pow(x, 2); // same as x^2

double y = Math.Sqrt(xSquared); // same as taking the square root of xSquared)
```

Absolute Value
```cs
int x = Math.Abs(-2); // resolves to 2
```

Trigonometry Functions
```cs
double y1 = Math.Sin(0); // all expected angles in radians, not degrees
double y2 = Math.Cos(0);
```

Min and Max of Two Numbers & Clamp
```cs
int smaller = Math.Min(2, 10); // returns 2
int larger = Math.Max(2, 10); // returns 10

health += 10;
health = Math.Calmp(health, 0, 100); // keep variable in the interval 0 to 100
```

MathF 
- Provides many methods as Math, but uses floats instead
```cs
float x = 3;
float xSquare = MathF.Pow(x, 2); // math pow expects doubles as inputs and returns doubles, MathF makes cast to float unnecessary
```

## Using Console Class
![console](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/console.png)

WriteLine
```cs
Console.Write("Hello!"); // Writes without jumping to the following line
Console.WriteLine("Goodbye!"); // Writes and jumps to the following line
```

Reading Input
```cs
Console.ReadKey(); // waits for single keypress from user "Press any key to continue..."

Console.ReadKey(true); // overload of ReadKey method, the entered key is intercepted here and does not display on-screen

Console.ReadLine(); // reads user input in string form
```

Changing Console Colors
```cs
Console.BackgroundColor = ConsoleColor.Yellow; // changes console background
Console.FOregroundColor = ConsoleColor.Black; // changes console foreground
```

Clear screen, change window title, & beep method
```cs
Console.Clear();
Console.Title = "Hello, World!";
Console.Beep();
Console.Beep(440, 1000); // frequency and pitch of beep
```

Escape Sequences
```cs
Console.WriteLine("\""); // instructs compiler to interpret " as a literal "
Console.WriteLine("C:\\Users\\RB\\Desktop\\MyFile.txt"); // To escape \, add an additional \\
Console.WriteLine(@"C:\Users\RB\Desktop\MyFile.txt"); // verbatim string literal, treat everything exactly as it looks
Console.WriteLine($"My favorite number is {myFavoriteNumber}."); // Use $ for string interpolation, you can combine $ and @
```

Alignment
- Adding prefix and postfix whitespace
```cs
string name1 = "Steve";

// pads before variable
Console.WriteLine($"#1: {name1,20}");

// Output:
// #1:               Steve

// pads after variable
Console.WriteLine($"{name1,-20} - 1");

// Output:
// Steve                - 1

```

Formatting
```cs
Console.WriteLine($"{Math.PI:0.000}"); // 0 indicates required number even if it isn't necessary
Console.WriteLine($"{42:#.##}); // Displays "42"
Console.WriteLine($"{42.1234:#:##}); // Displays "42.12"
Console.WriteLine($"{.444:0.0%}"); // Displays "44.4%"
```

### Decision Making
![decision](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/decision.png)

If Statement 
- Only runs if the conditional statement is true
- If statements can be nested
```cs
if (score == 100)
  Console.WriteLine("A+! Perfect score!");
  
// or in block statement form

if (score == 100)
{
  Console.WriteLine("A+! Perfect score!");
}
```

Important note on block statements
- Block statements receive their own variables, variables within a block cannot be used outside of the block

```cs
int score == 100;

if (score == 100)
{
  char grade = 'A';
}

Console.WriteLine(grade); // COMPILER ERROR
```

Else & Else if
- Counterpart to if statement, else specifies alternative if the if statement is false, else if allows additional checks

```cs
int score == 100;

if (score == 100)
  Console.WriteLine("A+! Perfect score!");
else
  Console.WriteLine("Try again.");
  
// else if example

if (score == 100)
  Console.WriteLine("A+! Perfect score!");
else if (score == 99)
  Console.WriteLine("Missed by THAT much.");
else
  Console.WriteLine("Try again.");
```

Relational Operators

```
==  equal to
!=  not equal to
<   less than
>   greater than
<=  less than or equal to
>=  greater than or equal to
```

Bool in decision making
- Bool can be used to resolve condition checks without if or else
- For example, `levelComplete` below is always resolving to true or false using the check `score` >= `pointsNeededToPass`, no if needed

```cs
bool levelComplete = score >= pointsNeededToPass;

if (levelComplete)
  Console.WriteLine("You've beaten the level!");
```

Logical Operators
- Not operator: `!`
- And operator: `&&`
- Or operator: `||`
- C# lazily evaluates, meaning, if it knows the whole expression's answer after evaluating only the first part(s), it won't bother evaluating the second part

```cs
bool levelComplete = score >= pointsNeededToPass;

if(!levelComplete) // if levelComplete is NOT true
  Console.WriteLine("This level is not over yet!");

int shields = 50;
int armor = 20;

// && operator

if (shields <= 0 && armor <= 0) 
  Console.WriteLine("You're dead.");
  
// || operator

if (shields > 0 || armor > 0)
  Console.WriteLine("You're still alive! Keep going!");
```

## Switches
- Alternative to multi-part if statements

![switch](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/switch.png)

Switch in Statement form
- Use `case` keyword followed by a value to check against (in this instance, the int `1`)
- This works exactly the same as a multi-line `if` and `else if` statement
```cs
switch (choice)
{
  case 1:
    Console.WriteLine("Case 1");
    break;
  case 2:
    Console.WriteLine("Case 2");
    break;
  case 3:
    Console.WriteLine("Case 3");
    break;
  default:
    Console.WriteLine("Default case");
    break;
}
```

Multiple cases can be assigned to the same switch arm
```cs
case 1:
case 2:
  Console.WriteLine("That's a good choice!");
  break;
```

Switch in Expression form
- Target (in this instance, choice) comes BEFORE `switch` keyword rather than after in statement form
- Breaks and case labels are no longer needed
- Cases now separated by commas
- Default is now replaced by `_` wildcard
- In this example, `response` is being assigned by the `choice` variable. So whatever `choice` gives to `response` will be switched into the corresponding below option. Remember, `choice` is its own variable. 

```cs
string response;

response = choice switch
{
  1 => "Choice number one",
  2 => "Choice number two",
  3 => "Choice number three",
  _ => "Default option."
};
```

## Looping

![loop](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/loop.png)

While Loop
- If loop is `false` initially, loop will not run at all
- Loop's condition is ONLY evaluated at the start of each cycle
- Entirely possible to build infinite loops

```cs
while ( condition)
{
  // This code is repeated as long as the condition is true
}

// displays numbers 1 through 5

int x = 1;
while (x <= 5)
{
  Console.WriteLine(x);
  x++;
}
```

Do/While Loop
- Evaluates condition at the END of the loop instead of the beginning
- This ensures loop runs at least once

```cs
int playersNumber;

do
{
  Console.Write("Enter a number between 0 and 10: ");
  string playerResponse = Console.ReadLine();
  playersNumber = Convert.ToInt32(playerResponse);
}
while (playersNumber < 0 || playersNumber > 10);
```

For Loop
- Lets you pack loop management into a single line
- Like a while loop, if condition is `false` initially, the `for` loop will not run at all
```cs
for (initialization statement; condition to evaluate; updating action)
{
  // ...
}

// displays numbers 1 through 5

for (int x = 1; x <= 5; x++)
  Console.WriteLine(x);
```

Break & Continue
- `Break` forces loop to terminate immediately without reevaluating loop condition
- `Break` enables you to leave the loop even if the condition is still true
- `Continue` will cause the loop to stop running the current pass through the loop, but will advance to the next pass, recheck the condition, and keep looping if the condition holds. 

```cs
while (true)
{
  Console.Write("Think of a number and type it here: ");
  string input = Console.ReadLine();
  
  if (input == "quit" || input == "exit")
    break;
  
  int number = Convert.ToInt32(input);
  
  if (number == 12)
  {
    Console.WriteLine("I don't like that number. Pick another one.");
    Continue;
  }
  Console.WriteLine($"I like {number}. It's the one before {number + 1}!");
}
```

## Arrays
![array](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/array.png)

- There are no limits on what types can be used in array `double[]`,`[bool[]`, or `char[]`, etc.
- You can even make arrays of arrays



Declare an array
```cs
int [] scores;
```

Construct a new array to hold items
- `new` keyword creates new things
- Once array value is constructed, it cannot change size
- We could use `new` again to recreate the array, updating `scores` with a new, longer array

```cs
int[] scores = new int[10]; // creates an array of 10 each with a value of 0

scores = new int[20]; // recreate array with new, longer array
```

Refer or assign a specific item within array
```cs
scores[0] = 99; // Number in brackets [0] is known as the index, in C# index starts at 0
```

Index can be any int expression, not just a literal
```cs
scores[someSpot + 1];
```

Retrieve array's length
```cs
Console.WriteLine(scores.Length);

// Example of creating an array and filling each index with a value of 1

int length = Convert.ToInt32(Console.ReadLine()0;
int[] array = new int[length];

for(int index = 0; index < array.Length; index++)
  array[index] = 1;
```

Index in reverse instead of forward
```cs
int lastScore = scores[^1]; // goes to the 2nd to last in array, rather than the 2nd
```

Grabbing Index Range
```cs
int[] firstThreeScores = scores[0..3]; // grabs the first three in scores and copies it to firstThreeScores

int[] theMiddle = scores[1..^1]; // grabs the second score to the second to last score

int theEnd = scores[2..]; // creates a copy from the entire array except for index 0 and index 1
```

Alternate Array Creation Methods
```cs
// Useful if you know what values you want your array to initially hold
int[] scores = new int[10] { 100, 95, 92, 87, 55, 50, 48, 40, 35, 10 }; 

// You can skip listing the length if you initialize like above
int[] scores = new int[] { 100, 95, 92, 87, 55, 50, 48, 40, 35, 10 };

// You can even skip listing the additional int if it's clear enough for the compiler to determine
int[] scores = new [] { 100, 95, 92, 87, 55, 50, 48, 40, 35, 10 };
```

Foreach loop
- Arrays and loops pair together because doing something with each item usually requires a loop
- Useful to simplify a for loop syntax
- `in` keyword separates the variable from the array to iterate over

```cs
int[] scores = new int[10];

for(int index = 0; index < scores.Length; index++)
{
  int score = scores[index];
  Console.WriteLine(score);
}

// Following foreach code is the same as the previous code

int[] scores = new int[10];

foreach (int score in scores)
  Console.WriteLine(score);
```

Array of Arrays
```cs
int[][] matrix = new int[3][];
matrix[0] = new int[] { 1, 2 };
matrix[1] = new int[] { 3, 4 };
matrix[2] = new int[] { 5, 6 };

// array setup:
[1  2]
[3  4]
[5  6]

// alternate setup

int[,] matrix = new int[3, 2] { { 1 , 2 }, { 3, 4 }, { 5, 6 } }; // comma in index indicates it has more than one dimension
Console.WriteLine(matrix[0, 1]); // result: 2

// example of looping through a multi-dimensional array

int[,] matrix = new int[4,5];

for (int row = 0; row < matrix.GetLength(0); row++) //GetLength(0) would return 4
{
  for (int column = 0; column < matrix.GetLength(1); column++) //Get.Length(1) would return 5
    Console.Write(matrix[row, column] + " ");
  
  Console.WriteLine();
}
```

## Methods
![methods](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/methods.png)

- Methods let you name and reuse a chunk of code
- Methods can be overloaded
- Recursion is when a method calls on itself
- The `main method` is the entry point for our program
- Using `static` in front of your method is a way to protect against using variables in the main method. The compiler will result in an error if a variable in the main method is used in your method.
- In C#, you cannot return more than one thign at a time



Defining a new method
- `void` means the method does not produce a result

```cs
void CountToTen()
{
  for (int current = 1; current == 10; current++)
    Console.WriteLine(current);
}
```

Calling a method

```cs
CountToTen(); // calls the method below

void CountToTen()
{
  for (int current = 1; current == 10; current++)
    Console.WriteLine(current);
}
```

Passing data to a method
```cs
void Count(int numberToCountTo)
{
  for (int current = 1; current <= numberToCountTo; current++)
    Console.WriteLine(current);
}

// using multiple parameters

void CountBetween(int start, int end)
{
  for (int current = start; current <= end; current++)
    Console.WriteLine(current);
}
```

Returning a value from a method
- Instead of returning `void` we need to communicate to the compiler what to return
- First, indicate the data type that will be return `int ReadNumber()`
- Second, state what value is returned `return number;`

```cs
int ReadNumber()
{
  string input = Console.ReadLine();
  int number = Conveert.ToInt32(input);
  return number;
}
```

Methods with Expressions
- Some methods are simple and can be represented with a single expression 
- Instead of curly brances and a return statement, the arrow operator is used like in `switch`
- You can only use an expression body if the whole method can be represented in a single expression

```cs
int DoubleAndAddOne(int value)
{
  return value * 2 + 1;
}

// the below method expression is the same as above

int DoubleAndAddOne(int value) => value * 2 + 1;
```

# Levels 15-32: Programming - Tying together data and methods
## - **Object-Oriented Principle #1:** Encapsulation
- Combining data (fields) and the operations on that data (methods) into a well-defined unit (a class is one example)
## - **Object-Oriented Principle #2:** Information Hiding
- Only the object itself should directly access its data
## - **Object-Oriented Principle #3:** Abstraction 
- The outside world does not need to know each object or class's inner workings and can deal with it as an abstract concept. Abstraction allows the inner workings to change without affecting the outside world.
## - **Object-Oriented Principle #4:** Inheritance
- Basing one class on another, retaining the orginal class's functionality while extending the new class with additional capabilities

## Enumerations 
- A custom type that lists a set of allowed values
- Choices are one of a small list of possible options
- Underneath it all, enumerations are integers at heart in their underlying type

![enumeration](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/enumeration.png)

Defining a new enumeration

```cs
enum Season { Winter, Spring, Summer, Fall }

// or, with this formatting is the same

enum Season
{
  Winter,
  Spring,
  Summer,
  Fall
}
```

Assing a variable to an enumeration

```cs
Season current = Season.Summer;
```

ConsoleColor uses enumeration

```cs
Console.BackgroundColor = ConsoleColor.Yellow; // { Black, Yellow, Red, ... }
```

Change underlying value on enumeration's underlying type

```cs
enum Season { Winter = 3, Spring = 6, Summer = 9, Fall = 12 }

// Any not assigned number is automatically given the one after the member before it, for example Spring is 2, Summer is 3, etc
enum Season { Winter = 1, Spring, Summer, Fall }

```

Given enumerations are underlying integers, you can cast between ints and enumerations

```cs
int number = (int)Season.Fall; // if Fall = 12, this would resolve to 12
Season now = (Season)2; // if Spring is 2, this would resolve to Spring
```

## Tuples
- Combine multiple elements into a single bundle
- Just another type for all practical purposes
- Can be used as parameter types or return values

![tuple](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/tuple.png)

Forming a simple new tuple
- Rather simple, instead of `int score` you would list your requisite variable types in parentheses on both sides
- Doing it simply like this leaves a lot to be desired

```cs
(string, int, int) score = ("R2-D2", 12420, 15);
```

Accessing a simple tuple

```cs
Console.WriteLine($"Name:{score.Item1} Level:{score.Item3} Score:{score.Item2}"); // suboptimal (which is which?), we can rename
```

Adding names to tuples and accessing those names

```cs
(string Name, int Points, int Level) score = ("R2-D2", 12420, 15); // any unnamed item have `ItemN` name scheme as shown above
Console.WriteLine($"Name:{score.Name} Level:{score.Level} Score:{score.Points}");
```

Passing in a tuple to a method example
- Like all method passed values, tuples DO NOT have to match the same name as the main method
- Names are ephemeral in methods and not a part of the main method tuple

```cs
void DisplayScore((string Name, int Points, int Level) score)
{
  Console.WriteLine($"Name:{score.Name} Level:{score.Level} Score:{score.Points}");
}
```

Method Returning a Tuple Array

```cs
(string Name, int Points, int Level)[] CreateHighScores()
{
  return new (string, int, int)[3]
  {
    ("R2-D2", 12420, 15),
    ("C-3PO", 8543, 9),
    ("GONK", -1, 1)
  };
}
```

Deconstructed Tuples
- Tuples can iterate across like-typed variables

```cs
var score = (Name: "R2-D2", Points: 12420, Level: 15);

string playerName = score.Name; // will assign one portion of the tuple to this new string

string bacon;
int eggs;
int ham;

(name, points, level) = score; // will assign all these variables to the respective tuple value in order
Console.WriteLine($"{bacon} reached level {ham} with {eggs} points.");
```

Swapping content values
- Tuple deconstruction can also be used to swap the contents of two discrete variables in one line

```cs
double x = 4;
double y = 2;
(x, y) = (y, x);
```

Ignoring Tuple Element with Discards
- Sometimes you don't need to copy all elements in a tuple array, you can simply discard that unnecessary tuple value

```cs
(string name, int points, _) = score; // score's 3rd tuple value is simply dropped instead of being assigned
```

## Classes
- SETUP: `[accessibility level] class [ClassName] { }`
- Classes are **the most powerful way to define new types**
- Classes bundle data (fields and variables) and operations on that data (methods)
- Classes are reference types
- An object is a thing in your software responsible for a slice of the entire program, containing data and methods - these define what information the object must remember the capabilities it can perform at request. 
- Think of a class as a blueprint or pattern for objects that belong to the class
- Constructors are an important "default check" for classes

![class](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/class.png)

A simple class
- Variables in a class are not local variables or parameters, they are another category of variables called `fields` or `instance variables`

```cs
class Score
{
  public string name;
  public int points;
  public int level;
}
```

A simple class with a method

```cs
class Score
{
  public string name;
  public int points;
  public int level;
  
  public bool EarnedStar() => (points / level) > 1000;
}
```

**Object-Oriented Principle #1:** Encapsulation - Combining data (fields) and the oeprations on that data (methods) into a well-defined unit (a class is one example)

Using your new class like any other type (`int`, `string`, `long`, `bool`, etc)
- With a class defined, it can be used like any other type
- We can declare a variable whose type is `Score` and assign it through a `new` instance

```cs
Score best = new Score(); // Score() is referring to a special method called a constructor
```

Invoking methods after our instance of our new class `Score` has been created
- Methods are accessed through an instance of the `Score` class (or your class you created obviously), in this case that instance is `best`
- You assign new values to each instancce, as these fields belong to the instance, so we must access them through a reference to an instance, in this case that instance is `best`

```cs
Score best = new Score();

best.name = "R2-D2"
best.points = 12420;
best.level = 15;

if (best.EarnedStar())
  Console.WriteLine("You earned a star!");
```

Creating more than one instance of a class
- When we do this, each instance has its own data
- Each instance is independent of other instances
- `a` is independent from `b` their variables are not shared

```cs
Score a = new Score();
a.name = "R2-D2";
a.points = 12420;
a.level = 15;

Score b = new Score();
b.name = "C-3PO";
b.points = 8543;
b.level = 8;

if (a.EarnedStar())
  Console.WriteLine($"{a.name} earned a star!");
if (b.EarnedStar())
  Console.WriteLine(${b.name} earned a star!");
```

Constructors
- SIMPLE SETUP: `public ClassName([optional parameters]) { }`
- Special methods that run when an object comes to life to ensure it begins in a good state
- Constructors are similar to other methods with two caveats:
  1. Must use the same name as the class
  2. They cannot list a return type
- A constructor's job is to get new instances into a legitimate starting state
- Specifics of getting it into a legitimate starting state vary from class to class
- Assigning initial values to each field is common

```cs
class Score
{
  public string name;
  public int points;
  public int level;
  
  public Score() // here's our constructor
  {
    name = "Unknown";
    points = 0;
    level = 1;
  }
  
  public bool EarnedStar() => (points / level) > 1000;
}
```

Constructors with Parameters
- Constructors are allowed to have parameters just like other methods
- It's common for constructors to use parameters to let the outside world provide initial values for some fields
- Using `n`, `p`, and `l` avoids sharing names with `name`, `points`, and `level`. A local variable or parameter is allowed to have the same name as a field, but when they share names, this can cause issues
- The constructor below has three parameters, letting the calling code provide initial values for each field

```cs
class Score
{
  public string name;
  public int points;
  public int level;
  
  public Score(string n, int p, int l) 
  {
    name = n;
    points = p;
    level = l;
  }
  
  public bool EarnedStar() => (points / level) > 1000;
}
```

Asking for a new `Score` instance, but with new parameters

```cs
Score score = new Score("R2-D2", 12420, 15);
```

Multiple Constructors with Parameters
- A class can have as many constructors as needed
- Each constructor must differ in number or types of parameters
- With two constructors, the outside world can pick which constructor it wants to use

```cs
Score a = new Score(); // outside world has chosen Constructor 1 here
Score b = new Score("R2-D2", 12420, 15); // outside world has chosen Constructor 2 here

class Score
{
  public string name;
  public int points;
  public int level;
  
  public Score() // Constructor 1
  {
    name = "Unknown";
    points = 0;
    level = 1;
  }
  
  public Score(string n, int p, int l) // Constructor 2
  {
    name = n;
    points = p;
    level = l;
  }
  
  public bool EarnedStar() => (points / level) > 1000;
}
```

Skipping defining constructors
- In some instances, you may only need a simple constructor by defining the initial fields
- Or, you may just want to have the fields have a "guaranteed" set value for each
- Any additional constructor can override these if needed

```cs
class Score
{
  public string name = "Unknown";
  public int points = 0;
  public int level = 1;
  
  public Score() // this constructor overrides the initial set value of "Unknown"
  {
    name = "Mystery";
  }
  
  public bool EarnedStar() => (points / level) > 1000;
}
```

Underscore trick
- Use this to keep consistent naming in field level variables separate from parameter variables
- Also allows us a clear way to differentiate fields from local variables and parameters
- This is the de facto standard for naming fields

```cs
class Score
{
  public string _name;
  public int _points;
  public int _level;
  
  public Score(string name, int points, int level)
  {
    _name = name;
    _points = points;
    _level = level;
  }
}
```

Constructors calling other constructors
- Sometimes you may want to use code in one constructor from another
- In the "outside world" of the class, you can't call a constructor without using the keyword `new`, if you do this, you'd be creating a second object while creating the first, ie, not intended
- Use the `this` keyword to build off one constructor to another

```cs
class Score
{
  public string _name;
  public int _points;
  public int _level;
  
  public Score() : this("Unknown", 0, 1) // passes through the constructor below first using the this keyword
  {
  }
  
  public Score(string name, int points, int level)
  {
    _name = name;
    _points = points;
    _level = level;
  }
}
```

## Information Hiding
- Details can and should be hidden from the outside world when possible
- Class members (fields and methods) should be marked as `public` or `private`
- Data should be `private` in nearly all cases
- Three levels: `public`, `private`, and `internal`
- The default state is `private`
- This is a concept, not necessarily directly a built-in C# "tool" (other than the `public` and `private` keywords which are explained in-depth in this section). Properties take this concept and push it to the next level, giving field-like access but still protecting data in a class. 

![info](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/info.png)

**Object-Oriented Principle #2:** Information Hiding - Only the object itself should directly access its data

Why private options are important
- In this example, even though `area` is hidden on our constructor parameter, the outside world can still change area, as shown above, even though we want area to be a discrete calculation that isn't settable by the outside world

```cs
Rectangle example = new Rectangle(2, 3);
example._area = 200000;
Console.WriteLine(rectangle._area);

class Rectangle
{
  public float _width;
  public float _height;
  public float _area;
  
  public Rectangle(float width, float height)
  {
    _width = width;
    _height = height;
    _area = width * height;
  }
}
```

Private Accessibility
- Makes fields and methods **only** accessible in the class itself 
- Known as an *accessibility modifier* 
- The outside world cannot interfere with private fields and methods
- This example is hyper private, the code above the class will not compile because `_area` is private, not accessible outside of the class

```cs
Rectangle rectangle = new Rectangle(2, 3);
Console.WriteLine(rectangle._area); // Does not compile

class Rectangle
{
  private float _width;
  private float _height;
  private float _area;
  
  public Rectangle(float width; float height) // remember the outside world can't "see" these local constructor fields
  {
    _width = width;
    _height = height;
    _area = width * height;
  }
}
```

Allowing Controlled Access Through Methods: Getting Fields
- Using methods, the outside world can access and retrieve variables, for example if we add `Get` methods for each field to our `Rectangle` class

```cs
public float GetWidth() => _width; // fields stay private, but outside world can still dip in
public float GetHeight() => _height;
public float GetArea() => _area;
```

Allowing Controlled Access Through Methods: Setting fields
- Same story as getting data, we can also *set* data through publically accessible methods

```cs
public void SetWidth(float value)
{
  _width = value;
  _area = _width * _height;
}

public void SetHeight(float value)
{
  _height = value;
  _area = _width * _height;
}
```

**Object-Oriented Principle #3:** Abstraction - The outside world does not need to know each object or class's inner workings and can deal with it as an abstract concept. Abstraction allows the inner workings to change without affecting the outside world.

## Properties
- SETUP: `[accessibility level] [type] ClassName { get{} set{} }`
- Pairs a getter and setter under a shared name with field-like access
- Has the benefit of both information hiding and abstraction 
- Properties are another type of member we can put into a class (like constructors)

![prop](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/prop.png)

Setting a simple property
- The first class code example shows how we would make public getters and setters without properties
- The second class code example shows how a property greatly simplifies this process
- `value` is a special variable, even though we didn't define a `value` parameter, it automatically exists in a property `set`

```cs
// Public getters and setters without properties 

public class Rectangle
{
  private float _width;
  
  public float GetWidth() => _width;
  
  public void SetWidth(float value) => _width = value;
}

// Swapping this out for a property

public class Rectangle
{
  private float _width;

  public float Width // this is combining that GetWidth and SetWidth into one
  {
    get => _width;
    set => _width = value;
  }
}
```

Setting a simple property with a block body
- Same principle just using a block body rather than an expression (works the same as methods in the sense that returns that need more than one line to resolve, need a bigger space to write out)

```cs
public float Width
{
  get
  {
    return _width;
  }
  set
  {
    _width = value; // value is a special variable
  }
}
```

Properties can be `get` or `set` only

```cs
public float Area
{
  get => _width * _height;
}

// if it is get only, and it can be reduced to an expression, it can be even further simplified

public float Area => _width * _height;
```

Full Example with outside world field access

```cs
Rectangle r = new Rectangle(2, 3);
r.Width = 5; // access to the class properties enables nearly identical to accessing public class fields
Console.WriteLine($"A {r.Width}x{r.Height} rectangle has an area of {r.Area}.");

public class Rectangle
{
  private float _width;
  private float _height;
  
  public Rectangle(float width, float height)
  {
    _width = width; 
    _height = height;
  }
  
  public float Width
  {
    get => _width; // this is the returning expression in this property, same as the get return _width; above
    set => _width = value; // this gets called on by the outside world above, and set to 5
  }
  
  public float Height
  {
    get => _height; // this is the returning expression in this property
    set => _height = value; // these setters could be made private and NOT settable outside the class
    // private set => _height = value; if we used this, instead of the line above, code would not 
    // compile if we tried to set height in the outside world
  }
  
  public float Area => _width * _height; // again, this can be reduced to an expression get
}
```

Auto-Implemented Properties
- Because simple property setting is so common, we can use auto-properties to setup our properties for us, without additional values
- The first code block example below shows the "long way" the same as it's shown above, the second block shows the auto property shortcut
- With auto property shortcut, you don't need to pass the keyword `value` or even give the backing field `_name`. You just end the getter and setter with a semicolon, the compiler will generate a backing field for this property and create a basic getter and setter around it.
- Again, notice in Block 2 that the entire CLASS no longer needs that backing field. There is no `private string _name;` necessary

```cs
// Block 1 - showing properties as has been done above

public class Player
{
  private string _name;
  
  public string Name
  {
    get => _name;
    set => _name = value;
  }
}

// Block 2 - showing properties with the auto shortcut

public class Player
{
  public string Name { get; set; } // no need to give the value keyword for set or define the backing field
}
```

Auto-Implemented Properties with initializing value
- Because we no longer have that backing field `_name`, we can't initialize to a default value. 
- This is solvable by simply throwing a value to the right of the auto property

```cs
public class Player
{
  public string Name { get; set; } = "Player";
}
```

Full Example with Auto Properties

```cs
public class Rectangle 
{
  public float Width { get; set; } // auto property
  public float Height { get; set; } // auto property
  public float Area => Width * Height; // property expression
  
  public Rectangle(float width, float height) // constructor
  {
    Width = width;
    Height = height;
  }
}
```

Auto-Implemented Properties Get-Only (read-only property)
- Auto properties can be get-only but they cannot be set-only, there is no scenario where a set-only auto property is useful, that would just be black hole of data.
- When a property is get-only, it can still be assigned values, but only from within a constructor
- Get-only properties are sometimes referred to as read-only properties, it cannot be changed once the object is created (inside or outside the class)
- Also known as immutability

```cs
public class Player
{
  public string Name { get; } = "Player 1"; // "Player 1" is the default defined name
  
  public Player(string name) // in this read-only instance, this is the only place the name can be set
  {
    Name = name;
  }
}
```

Read-Only Regular Properties
- In the same way, it may be useful to make normal properties read-only after construction, we can do this with regular properties not just auto-properties
- adding `readonly` makes it so it can only be assigned in one of two places
  1. As an initializer (ie `private string name = "Here!";`)
  2. In a constructor

```cs
public class Player
{
  private readonly string _name; // readonly goes between the accessibility and type
  
  public Player(string name)
  {
    _name = name;
  }
}
```

Property Initializer Syntax
- Sometimes you may want to set a property right as the object is created
- You can do this via object initializer syntax
- You cannot use initializer syntax with properties that are get only
- Object initializer syntax comes after the constructor finishes, in this `class Circle`, there is no constructor explicitly outlined in our `class` (it's just null/0)

```cs
Circle circle = new Circle() { Radius = 3, X = -4 }; // the curly braces here are out property initializer
// or, because our Circle class does not have a constructor it could be written like this:
Circle circle = new Circle { Radius = 3, X = -4 }; // exactly the same just no () after Circle

public class Circle
{
  public float X { get; set; } = 0; // The x-coordinate of the circle's center.
  public float Y { get; set; } = 0 // The y-coordinate of the circle's center.
  public float Radius { get; set; } = 0;
}
```

Property Initializer Syntax in limited conditions
- You may only want to set during an inline initializer, inline initializer, and object initializer syntax but nowhere else
- Obviously the code above is using `get;` and `set;` so it can manipulate those fields anywhere
- `init` limits it to those 3 use cases alone

```cs
Circle circle = new Circle { X = 1, Y = 4, Radius = 3 };

circle.X = 2; // this statement would not compile with the init; preventing it from changing

public class Circle
{
  public float X { get; init; } = 0;
  public float Y { get; init; } = 0;
  public float Radius { get; init; } = 0;
}
```

## Static
- We have implicit inconsistency, we've used instances in classes like `Console` or `Convert` but we've never needed to call `new Console()` specifically
- The `static` keyword can be used to detach instances and tie them to the class itself (ie, Math.Sqrt())
- A `static` method doesn't need an instance of the class to be used, it's intrinsically part of the class
- `Static` can be used on fields or variables

![static](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/static.png)

Simple Static Variable Example

```cs
public class Score
{
  private static readonly int PointThreshold = 1000;
}
``` 

Static Properties
- Properties can also be static
- Below is a simple example of a property version of the previous variable

```cs
prublic class Score
{
  public static int PointThreshold { get; } = 1000;
}
```

Static Methods
- A static method is not tied to a single instance, so it cannot refer to non-static fields, properties, or methods
- The static method below determines how many scores in an array belong toa specific player

```cs
public static int CountForPlayer(string playerName, Score[] scores)
{
  int count = 0;
  foreach (Score score in scores)
    if (score.Name == playerName) count++;
  return count;
}
```

Factory Method
- Creates new instances for the outside world as an alternative to calling a constructor

```cs
public static Rectangle CreateSquare(float size) => new Rectangle(size, size);

//that method would be called like this:

Rectangle rectangle = Rectangle.CreateSquare(2);
```

Static Constructors
- If a class has static fields or properties, you may need logic to initialize them
- To initialize, you could define a static constructor

```cs
public class Score
{
  public static readonly int PointThreshold;
  public static readonly int LevelThreshold;
  
  static Score()
  {
    PointThreshold = 1000;
    LevelThreshold =4;
  }
}
```

Static Classes
- Some classes are nothing more than a collection of related utility methods, fields, or properties
- `Console`, `Convert`, and `Math`, are all examples of this. In these cases you may way to forbid creating instances of the class
- This prevents the `new` keyword from being used whatsoever

```cs
public static class Utilities
{
  public static int Helper1() => 4;
  public static double HelperProperty => 4.0;
  public static int AddNumbers(int a, int b) => a + b;
}
```

## Null References
- Null references are helpful when it is possible for there to be no data available for something
- `null` is the default value for reference types
- There are situations that can return `null` which can cause problems

![null](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/null.png)

Null or not?
- For referenced-typed variables, stop and think if `null` should be an option or not
- Annotating a variable is a relatively new feature of C# (starting in C# 9)
- If we want to allow a null, we include a `?` that means it may legitimately contain a null value, for example:

```cs
string? name = Console.ReadLine(); // Can return null
```

Checking for `null`
- You may need to check for null, if a reference variable can result in a null
- The quickest way to compare a reference against the `null` literal is a null check

```cs
string? name = Console.ReadLine();
if (name != null)
  Console.WriteLine("The name is not null.");
```

Null-conditional operators ? and ?[]
- One problem with null checking si that there may be implications down the line
- In the example below, if any part of `_scoreManager` is null, it will crash, so we would have to check at each step

```cs
prviate string? GetTopPlayerName()
{
  if (_scoreManager == null) return null;
  
  Score[]? scores = _scoreManager.GetScores();
  if (scores == null) return null;
  
  Score? topScore = scores[0];
  if(topScore == null) return null;
  
  return topScore.Name;
}
```

These excessive null checks make it difficult to read
- There is another option, null-conditional operators. The `?.` and `?[]` operators can be used in place of `.` and `[]` to simultaneously check for null and access the member:

```cs
private string? GetTopPlayerName()
{
  return _scoreManager?.GetScores()?[0]?.Name;
}
```

Both `?.` and `?[]` evaluate the part before it to see if it is null, if it is, no further evaluation happens and the whole expression evaluates to `null`
- If it is not null, evaluation will continue as though it had been normal

The Null Coalescing Operator `??`
- The null coalescing operator is a useful tool, it takes an expression that might be `null` and provides a value or expression to use as a fallback if it is

```cs
private string GetTopPlayerName() // No longer needs to allow nulls
{
  return _scoreManager?.GetScores()?[0]?.Name ?? "(not found)";
}
```

- If the code before `??` evaluates to `null` the fallback value of `"(not found)"` will be used instead
- There's also a compound assignment operator for this:

```cs
private string GetTopPlayerName()
{
  string? name = _scoreManager?.GetScores()?[0]?.Name;
  name ??= "(not found)";
  return name; // No compiler warning. ??= ensures we have a real value
}
```

The Null-Forgiving Operator: `!`
- The compiler is thorough in analyzing what can and can't be null, and giving you appropriate warnings
- On infrequent occasions, you know something about the code that the compiler simply can't infer, for example:

```cs
string message = MightReturnNullIfNegative(+10);
```

- Assuming the return type of `MightReturnNullIfNegative` is `string?`, the compiler will flag this as a situation where you are assigning a potentially null value to a variable that indicates nuil isn't allowed. But assuming the method nam eisn't a lie, we know the returned value can't be null
- To get rid of the compiler warning, we can use the null-forgiving operator `!` 
- The operator tells the compiler "I know this looks like a null problem, but it won't be. Trust me."
- With the `!` there, the warning will go away
- Use `!` sparingly, it can be dangerous

```cs
string message = MightReturnNullIfNegative(+10)!; //! at the end
```

## Inheritance
- Allows you to derive new classes based on existing ones
- The new class inherits everything excep constructors
- All classes derive from `object` by default


![inheritance](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/inheritance.png)

General Info
- Sometimes it's necessary to derive new classes based on existing ones (or simply easier to do so)
- You can define this subtype or specialization in C# using inheritance 
- Inheritance allows you to treat subtypes as more generalized whenever necessary, second it allows you to consolidate would would be duplicated or copy-and-pasted code

**Object-Oriented Principle #4:** Inheritance - Basing one class on another, retaining the orginal class's functionality while extending the new class with additional capabilities

Inheritance and the Object Class
- When inheritance is defined, the new class gets everything the old class had, the new class can add in extra stuff, and the new class can always be treated as though it were the original since it has all of those capabilities
- Every class defined automatically extends from a base class called the `object`class
- The `object` class does not have many responsibilities 
- It can call its method `ToString()` to create a string representation of any object. The default implementation displays the full name of the object's type
- It can also call its method `Equals` to indicate whether two things are considered equal or not, it returns a boolean `True` or `False`
- A derived class can only choose one base class

```cs
// ToString() Example
object thing = new object();

Console.WriteLine(thing.ToString()); //outputs "System.Object"

// Equals example
object a = new object();
object b = a;
object c = new object();
Console.WriteLine(a.Equals(b)); // returns true
Console.WriteLine(a.Equals(c)); // returns false - even though the contents of both objects are blank, a points to a different location on the heap
```

Object Class Derivation
- Because object has `ToString()` and `Equals` any class you create has `ToString` and `Equals`
- For example, this `Point` class below, can use `Equals` or `ToString()`

```cs
Point p1 = new Point(2, 4);
Point p2 = p1;
Console.WriteLine(p1.ToString()); // derived from object
Console.Write(p1.Equals(p2)); // derived from object

public class Point
{
  public float X { get; }
  public float Y { get; }
  
  public Point(float x, float y)
  {
    X = x; Y = y;
  }
}
```

- Because a derived class has all the base class's capabilities, you can use the derived class anywhere the bass class is expected
- The example below shows a variable with a type of `object` but we give it a reference to a `Point`
- Although `Point` is a different class than `object`, it can be treated as one because it is derived from `object`
- Although the example `thing` below can hold `object` classes, the variable makes no promises it has a reference to anything more specific than `object`
- The variable itself can only guarantee it has a reference to an `object`
- Placing a reference to a derived class like `Point` into a base class like `object` does not mean that information is lost forever

```cs
object thing = new Point(2, 4); // Referencing our Point class even though its type is object

Console.WriteLine(thing.ToString()); // Safe
Console.WriteLine(thing.X); // Compiler error
```

Choosing Base Classes
- Even though `object` is the default base class, it's simple to claim a different class as the base class
- For example, the `Asteroid` class below can use `GameObject` as a base class
- `Asteroid` inherits everything from the base class, it also adds `Size` and `RotationAngle` as properties, these are unique to `Asteroid`

```cs
public class GameObject
{
  public float PositionX { get; set; }
  public float PositionY { get; set; }
  public float VelocityX { get; set; }
  public float VelocityY { get; set; }
  
  public void Update()
  {
    PositionX += VelocityX;
    PositionY += VelocityY;
  }
}

public class Asteroid : Game Object // the : allows the derivation and inheritance
{
  public float Size { get; }
  public float RotationAngle { get; }
}
```

- Assume we made additional classes `Bullet` and `Ship` that also derive from `GameObject`. We could setup a new game of *Asteroids* with a collection of game objects of mixed types like the example below
- The array below stores references to `GameObject` instances, but the array contains instances of the `Asteroid`, `Bullet`, and `Ship` classes. The array is fine with this because all of them derive from `GameObject`

```cs
GameObject[] gameObjects = new GameObjects[]
{
  new Asteroid(), new Asteroid(), new Asteroid(), new Bullet(), new Ship()
};
```

- Even though we are dealing with 4 total classes (1 base class, 3 derived classes), we can still call the `Update` method on any of them since it is defined by `GameObject` all the derived classes are guaranteed to have that method

```cs
foreach (GameObject item in gameObjects)
  item.Update;
```

Constructors
- Constructors are not inherited
- But we must leverage constructors defined int he base class when making new constructors in the derived class
- In the example below, `Asteroid` wil automatically call `GameObject`'s parameterless constructor
- Calling `new Asteroid()` will enter `Asteroid`'s constructor and immediately jump to `GameObject`'s parameterless constructor to set `PositionX` and `PositionY` then return to `Asteroid`'s constructor to set `RotationAngle`
- The derived class has the "last say" on values. For example, if in your `Asteroid` parameterless constructor you gave `PositionX` a value of 3, it would have a value of 3, not `GameObject`'s assignment of 2. 

```cs
public class GameObject
{
  public GameObject()
  {
    PositionX = 2; PositionY = 4;
  }
  
  // Properties and other things here
}

public class Asteroid : GameObject
{
  public Asteroid()
  {
    RotationAngle = -1;
  }
  
  // Properties and other things here
}
```

Multiple Constructors in Inheritance
- Suppose a base class has more than one constructor or does not include a parameterless constructor, in that case, you need to expressly state which base class constructor to build upon for any new constructors in the derived class
- In the example below, there is no parameterless constructor to call, so you will need to expressly state which constructor to build upon for any new constructors in the derived class

```cs
public GameObject(float positionX, float positionY, float velocityX, float velocityY)
{
  PositionX = positionX; 
  PositionY = positionY;
  VelocityX = velocityX;
  VelocityY = velocityY;
}

public Asteroid(float positionX, float positionY, float velocityX, float velocityY) : base(positionX, positionY, velocityX, velocityY)
{
}
```

Casting and Checking for Types
- If you have a **base** type and need to get a **derived** type, you have some options.
- For example, the below sample results in a compiler error

```cs
GameObject gameObject = new Asteroid();
Asteroid asteroid = gameObject; // ERROR!
```

- The `gameObject` variable can only guarantee it has a `GameObject` class. It might reference something more specific, like an `Asteroid`. By casting, we can get the computer to treat the object as the more specialized type:

```cs
GameObject gameObject = new Asteroid();
Asteroid asteroid = (Asteroid)gameObject; // Use with caution
```

- Casting tells the compiler that you are guaranteeing it will be safe to treat this as an `Asteroid`
- The program will crash when running if you are wrong
- Generally, you should only *downcast* (going from a base class to a derived class) if you check for the correct type first
- There are three ways to perform this check

**1. The first way is with object's GetType() method and the typeof keyword:**

```cs
if (gameObject.GetType() == typeof(Asteroid)) {...}
```

- `GetType()` returns the type object associated with the isntance's class. If `gameobject` is an `Asteroid` it will return the type object representing the `Asteroid` class.
- `typeof` lets you access special objects by name so you can see if an object's type matches some specific class
- `GetType()` will only work if there's an exact match


**2. The second way is with the `as` keyword:**

```cs
GameObject gameOjbect = CreateAGameObject();
Asteroid? asteroid = gameObject as Asteroid;
```

- The `as` keyword simultaneously does a check and the conversion. If `gameObject` is an `Asteroid` or something derived from `Asteroid`, then the variable `asteroid` will contain the reference to the object, now known to be an `Asteroid`. If `gameObject` is a `Ship` or a `Bullet` then `asteroid` will be `null`, that means you want to do a null `?` check before using the variable

**3. The third way is with the `is` keyword:**

```cs
if (gameObject is Asteroid asteroid)
{
  // You can use the `asteroid` variable here
}
```

- The `is` keyword is powerful and is one way to use patterns. But it is frequently used to simply check the type and assign it to a new a variable
- If you don't need the variable that the example above creates, you can check it this way:

```cs
if (gameObject is Asteroid) { ... }
```

The Protected Access Modifier
- The 3 accessibility modifiers we've used so far are `private`, `public`, and `internal`
- The 4th accessibility modifier is the `protected` keyword
- A `protected` access modifier is accessible within the class and any derived classes, for example below
- If we maket hese setters protected instead of public, only `GameObject` and its derived classes (like `Asteroid` and `Ship`) can change those properties, the outside world cannot

```cs
public class GameObject
{
  public float PositionX { get; protected set; }
  public float PositionY { get; protected set; }
  public float VelocityX { get; protected set; }
  public float VelocityY { get; protected set; }
}
```

Sealed classes
- If you want to forbid others from deriving from a specific class, you can prevent it by adding the `sealed` modifier to the class definition
- In this case, nobody will be able to derive a new class based on `Asteroid`
- Class sealing can occasionally result in a performance boost

```cs
public sealed class Asteroid : GameObject
{
  // ...
}
```
