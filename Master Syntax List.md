# C# Player's Guide Master List of Syntax

This covers the major formatting and programming guidelines outlined in RB Whitaker's C# Player's Guide (Fifth Edition)

## Basics

### Comments

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
int a = 123_456_789; //(underscore is ignored by the compiler it can appear anywhere)
```

### C# Type Specifics

Char assignment
```cs
char aLetter = 'a';
```

Integer and conversion to literals (everything smaller than an int type is automatically literal)
```cs
ulong aVeryBigNumber = 1_000_000_000_000U; //U signifies it is unsigned and must be uint or ulong
aVeryBigNumber = 1_000_000_000_000L; //L signifies it is the long literal and must be long or ulong
aVeryBigNumber = 1_000_000_000_000UL; //UL signifies it must be unsigned and long, therefore, a ulong
```

Floating-point and conversion to literals (double is literal)
```cs
double number1 = 3.5623;
float number2 = 3.5623f;
decimal number3 = 3.5623m;
```

Scientific Notation
```cs
double avogadrosNumber = 6.022e23; //e stands for "exponent"
```