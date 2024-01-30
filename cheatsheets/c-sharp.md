# C# Cheatsheet

This is a work in progress as I learn to code with C#.

**Code breakdown**
~~~C#
Console.WriteLine("Hello World!");
~~~

Console = class
WriteLine = method
Double-quotes = a literal string

## Concepts

**Literal Value** is a constant value that never changes. If you only wanted a single alphanumeric character printed to screen, you could create a *char* literal by surrounding one alphanumeric character in *single quotes*. 

Example: 

~~~C#
Console.WriteLine('b');
~~~

Single Quotes: Create a character literal. (used for presentation, not calculation!)
Double Quotes: Creates a string data type.

**Integer Literal** is a numeric whole number (no fractions) value in the output console. The term is *int* for short and it doesn't require other operators like the string or char.

**Floating Point Literal** is a number that contains a decimal, for example 3.14159. C# supports three data types to represent decimal numbers: float, double, decimal. 

|Float Type | Precision     |
|-----------|:-------------:|
|float      | ~6-9 digits   |
|double     | ~15-17 digits | 
|decimal    | 28-29 digits  |

Float Literal: Append the letter *F* after the number. Can be upper or lower-case. 

~~~C#
Console.WriteLine(0.25F);
~~~

**Double Literal** Just enter a decimal number.

**Decimal Literal** Append the letter m after the number. Can be upper or lower-case.

**Boolean Literals** Represent True or False. The term *bool* is short for boolean. 

~~~C#
Console.WriteLine(true);
Console.WriteLine(false);
~~~

## Data Types
Data types play a central role in C#, unlike other programming languages like JavaScript. 

*string* for presentation
*char* for presentation
*int* for calculation
*decimal* for calculation

## Declare Variables
A *literal* is a hard-coded value. It is constant and unchanged throughout the execution of the program. 

When you need to work with data that isn't hard-coded, you'll declare a *variable*.

*Variable* is a container for storing a type of value. These values can be assigned, read and changed.

A variable name is a human friendly label that the complier assigns to a memory address.

*Declare a variable*
To create a new variable, you must first declare the data type of the variable, and then give it a name.

~~~C#
string firstName;
~~~

In this case, you're creating a new variable type *string* called *firstName*. From now on, this variable can only hold string values.

### Variable name rules and conventions
- Can be alphanumeric characters and the underscore character.
- Special characters like the hash # or dollar sign $ are not allowed.
- Variable names must begin with an alphabetical letter or an underscore, not a number.
- Names are case-sensitive.
- Names must not be a C# keyword. Example: `decimal decimal` or `string string`.
- SHould use camel case. Example: string `thisIsCamelCase`.
- Should be descriptive and meaningful.
- Should be one or more words appended together, don't use contractions or abbrieviations.
- Shouldn't include the data type of the variable. You might see some advice to use a style like `string strValue;`.

### Assinging a Variable
Is also referred to as "setting the variable", or simply a "set" operation.

### Retrieveing a Variable

Example:
~~~C#
string firstName;
firstName = "James";
Console.WriteLine(firstName);
~~~

### Initialize a Variable

Example:
~~~C#
string firstName = "James";
Console.WriteLine(firstName);
~~~

### Implicitly Typed Local Variables
Is a variable created by using the *var* keyword followed by a variable initialization. Using *var* implies the data type.

Example: 
~~~C#
var message = "Hello World!";
~~~

## Format literal strings of C#

### Escape characters list
An escape character sequence is an introduction to the runtime to insert a special character that will affect the output of your string. In C#, the escape character sequence begins with a backslash `\` followed by the character your're escaping. 

| Escape character | Description      |
|------------------|------------------|
| \n               | New line         |
| \t               | Tab              |
| \b               | Backspace        |

| Escape character | Result   | Description   |
|------------------|:--------:|---------------|
|\'                | '        | Single quote  |
|\"                | "        | Double-quote  |
|\\                | \        | Backslash     |

### Escape character usage

Example: the `\n` sequence will add a new line, and a `\t` sequence will add a tab.
~~~C#
Console.WriteLine("Hello\nWorld");
~~~

### How to insert a double-quotation mark

Example: 
~~~C#
Console.WriteLine("Hello \"World\"!");
~~~

### Working with a file path**
C# reseverves the backslash for espace sequences, so will output an error if you try to write out a file path such as `"c:\source\repos"`.

To solve this issue, you can use a double backslash `\\` to display a single backslash.

Example: 
~~~C#
Console.WriteLine("c:\\source\\repos");
~~~

### Verbatim string literal
A verbatim string literal will keep all whitespace and characters without the need to escape the backslash. To create a verbatim string, use the `@` directive before the literal string.

Example: 
~~~C#
Console.WriteLine(@"    c:\source\repos
    (this is where your code goes)");
~~~

### Unicode escape characters
Use the \u escape sequence, then a four-character code respresenting some character in Unicode (UTF-16).

Example: 
~~~C#
// Kon'nichiwa World
Console.WriteLine("\u3053\u3093\u306B\u3061\u306F World!");
~~~

## String Concatenation
Use the string concatenation operator which is the + symbol.

Example: 
~~~C#
string firstName = "Bob";
string message = "Hello " + firstName;
Console.WriteLine(message);
~~~

### Avoid intermediate variables
Instead of using an extra variable to hold the new string that resulted from the concatentation operation, perform the concatenation operation as you need it.

Example (WRONG): 
~~~C#
string firstName = "Bob";
string greeting = "Hello";
string message = greeting + " " + firstName + "!";
Console.WriteLine(message);
~~~

Example (CORRECT)
~~~C#
string firstName = "Bob";
string greeting = "Hello";
Console.WriteLine(greeting + " " + firstName + "!");
~~~

## String interpolation
Used when you need to combine many literal strings and variables into a single formatted message.

This is achieved by using an *interpolation expression* that is indicated by an opening and closing curly brace symbol `{ }`. You can put any C# expression that returns a value inside the braces. The literally string becomes a template when it's prefixed by the `$` character.

Example:

Instead of this:

~~~C#
string message = greeting + " " + firstName + "!";
~~~

You can do this:

~~~C#
string message = $"{greeting} {firstName}!";
~~~

### Interpolate a literal string and a variable value
You create a literal string and prefix the string with the `$` symbol. The literal string should contain at least one set of curly braces `{}` and inside of those characters you use the name of a variable.

Example:
~~~C#
string firstName = "Bob";
string message = $"Hello {firstName}!";
Console.WriteLine(message);
~~~

### Combining multiple variables and literal strings. 
You can do this in the same line of code.

Example:
~~~C#
int version = 11;
string updateText = "Update to Windows";
string message = $"{updateText} {version}";
Console.WriteLine(message);
~~~

Output:

~~~C#
Update to Windows 11
~~~

### Avoid intermediate variables
As with *string interpolation*, you should avoid using a temporary variable to store the message.

The code used above for **Combining multiple variables and literal strings** can be simplified as shown below.

Example:

~~~C#
int version = 11;
string updateText = "Update to Windows";
Console.WriteLine($"{updateText} {version}!");
~~~

Output:

~~~C#
Update to Windows 11!
~~~

## Combine verbatim literals & string interpolation
You can use both the verbatim literal prefix symbol `@` and the string interpolation `$` symbol together. In the example below, the `$` symbol allows you to reference the `projectName` variable inside the braces, while the `@` symbol allows you to use the unescaped `\` character.

~~~C#
string projectName = "First-Project";
Console.WriteLine($@"C:\Output\{projectName}\Data");
~~~

Output:

~~~C#
C:\Output\First-Project\Data
~~~

