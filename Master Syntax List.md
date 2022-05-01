# C# Player's Guide Master List of Syntax

This covers the major formatting and programming guidelines outlined in RB Whitaker's C# Player's Guide (Fifth Edition)

## Levels 01-14: Basics
![basics](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/basics.png)

- Comments
- Variables
- C# Type Specifics
- Math

### Comments
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

### Varibles
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

### C# Type Specifics
![types](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/types.png)

Char assignment
```cs
char aLetter = 'a';
```

Integer and conversion to literals (everything smaller than an int type is automatically literal)
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

### Math
![math](https://github.com/matthew0241/CPlayersGuide/blob/main/Assets/math.png)

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

Casting Math operations for small types (math operations are not defined for types smaller than int)
```cs
short a = 2;
short b = 3;
short total = (short)(a + b);
```

Casting Math operations for integer to floating point (if we didn't cast the below code, it would assume integer division!)
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

MathF (provides many methods as Math, but uses floats instead)
```cs
float x = 3;
float xSquare = MathF.Pow(x, 2); // math pow expects doubles as inputs and returns doubles, MathF makes cast to float unnecessary
```

### Using Console Class

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
