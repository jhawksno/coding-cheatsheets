# Power Automate Cheat Sheet

## Functions

Functions are grouped into 10 different categories like math and logic.

1. String Functions
2. Collection Functions
3. Logical Functions
4. Conversion Functions
5. Math Functions
6. Date and time Functions
7. Referencing Functions
8. Workflow Functions
9. URI Parsing Functions
10. Manipulation Functions

**String functions**
Example: 
~~~C#
formatNumber(12.5, 'C')
~~~

The **C** represents the Currency numeric format string. 

Check out the list of available Standard Numberic Format Strings:
https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings

### Collection functions
These functions are used for arrays and strings. May be used to check if an array is empty, grab the first, or last item, etc.

Example: `length('I love Power Automate.;)`
Output: `22`

**Tip:** A space counts as one character. 

### Logical functions
These functions are used to work with conditions, compare values, and to do other logic-based evaluations. You can think of these as if statements where you want to compare if a number is greater than another number.

Example: `If(greater(12,10),'Yes','No')`

### Conversion functions
Thse functions are used to change the type of your data. You can use these functions to convert a text number into an integer, or changing the encoding of a file from base64 to binary.

The example below will change the string `"12"` into the interger `12`.

Example: `Int('12')`

### Math functions
These functions allow you to add, subtract, multipy and perform other math functions.

The example below will give a random number from 1 to 10.

Example: `rand(1,10)`

The example below will add two numbers together.

Example: `Add(12,13)`

The last example will add three numbers together.

Example: `add(add(12,13),15)`

### Date and time functions
These functions are used to return the current date and time, change the time zone and other date and time manipulations.

**Note:** In Power Automate, time functions are often based on UTC. The example below shows how to convert UTC time format to EST.

Example: `convertFormatUtc(utcNow(), 'Eastern Standard Time', 'dd-MM-yyyy hh:mm tt')`

See more custome date and time format strings here:
https://learn.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings/

### Referencing functions
These functions are used to work with the outputs of your actions and triggers. Most of the time, Power Automate will write these functions for you when you add dynamic content to your flow. 

Hover over the dynamic function to see the actual function in action.

Example: `User name` 
Hover: `triggerOutputs()['headers']['x-ms-user-name-encoded']`

### Workflow functinos
These are used to retrieve information about our flow and are closley related to the referencing functions.

Example: `Workflow().run.id`

### URI parsiing functions
These are used to dissect a URI that is passed in as a string. You can use these functions to find the host, path, query string, or other portions of the URI. 

The example below shows you how to use uriQuery to get the query string portion of the given URI.

Example: 
~~~C#
uriQuery('https://flow.microsoft.com/fakeurl?Test=Yes')
~~~

Output: 
~~~C#
Will return the string "?Test=Yes"
~~~

### Manipulation functions
These functions are used to work with specific objects in your flow. You can use them to find the first non-blank value, work with properties, or find xpath matches. These functions are typically used in JSON or XML nodes evaluations.

The example below will find the first non-nul value from a specified set of values.

Example: 
~~~C#
Coalesce(null, 'Power Automate', 'Power Apps')
~~~

Output: Will return the string `Power Automate`

### Complex Expressions

Complex expressions are when you combine more than one function to get the result you want. When you think of complex expressions, it's more than one function in an expression where you use the output of one function as an input of another. There's no special syntax, operators, or considerations.

**Tip:** You can combine dynamic content into your expressions. 