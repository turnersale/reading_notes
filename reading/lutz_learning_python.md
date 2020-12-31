# Learning Python
### Mark Lutz !-- omit in toc --
### 1449355730 !-- omit in toc --

- [Learning Python](#learning-python)
    - [Mark Lutz !-- omit in toc --](#mark-lutz----omit-in-toc---)
    - [1449355730 !-- omit in toc --](#1449355730----omit-in-toc---)
- [Preface](#preface)
- [Part 1 – Getting Started](#part-1--getting-started)
  - [Chapter 1 – A Python Q&amp;A Session](#chapter-1--a-python-qa-session)
  - [Chapter 2 – How Python Runs Programs](#chapter-2--how-python-runs-programs)
  - [Chapter 3 – How You Run Programs](#chapter-3--how-you-run-programs)
- [Part 2 - Types and Operations](#part-2---types-and-operations)
  - [Chapter 4 - Introducing Python Object Types](#chapter-4---introducing-python-object-types)
  - [Chapter 5 - Numeric Types](#chapter-5---numeric-types)
  - [Chapter 6 - Dynamic Typing Interlude](#chapter-6---dynamic-typing-interlude)
  - [Chapter 7 - String Fundamentals](#chapter-7---string-fundamentals)
  - [Chapter 8 - Lists and Dictionaries](#chapter-8---lists-and-dictionaries)
  - [Chapter 9 - Tuples, Files, and Everything Else](#chapter-9---tuples-files-and-everything-else)
- [Part 3 - Statements and Syntax](#part-3---statements-and-syntax)
  - [Chapter 10 - Introducing Python Statements](#chapter-10---introducing-python-statements)
  - [Chapter 11 - Assignments, Expressions, and Prints](#chapter-11---assignments-expressions-and-prints)
  - [Chapter 12 - _if_ Tests and Syntax Rules](#chapter-12---if-tests-and-syntax-rules)
  - [Chapter 13 - _while_ and _for_ Loops](#chapter-13---while-and-for-loops)
  - [Chapter 14 - Iterations and Comprehensions](#chapter-14---iterations-and-comprehensions)
  - [Chapter 15 - The Documentation Interlude](#chapter-15---the-documentation-interlude)
- [Part 4 - Functions and Generators](#part-4---functions-and-generators)
  - [Chapter 16 - Function Basics](#chapter-16---function-basics)
  - [Chapter 17 - Scopes](#chapter-17---scopes)
  - [Chapter 18 – Arguments](#chapter-18--arguments)
  - [Chapter 19 – Advanced Function Topics](#chapter-19--advanced-function-topics)
  - [Chapter 20 – Comprehensions and Generations](#chapter-20--comprehensions-and-generations)
  - [Chapter 21 – The Benchmarking Interlude](#chapter-21--the-benchmarking-interlude)
- [Part 5 – Modules and Packages](#part-5--modules-and-packages)
  - [Chapter 22 – Modules: The Big Picture](#chapter-22--modules-the-big-picture)
  - [Chapter 23 – Module Coding Basics](#chapter-23--module-coding-basics)
  - [Chapter 24 – Module Packages](#chapter-24--module-packages)
  - [Chapter 25 – Advanced Module Topics](#chapter-25--advanced-module-topics)
- [Part 6 – Classes and OOP](#part-6--classes-and-oop)
  - [Chapter 26 – OOP: The Big Picture](#chapter-26--oop-the-big-picture)
  - [Chapter 27 – Class Coding Basics](#chapter-27--class-coding-basics)
  - [Chapter 28 – A More Realistic Example](#chapter-28--a-more-realistic-example)
  - [Chapter 29 – Class Coding Details](#chapter-29--class-coding-details)
  - [Chapter 30 – Operator Overloading](#chapter-30--operator-overloading)
  - [Chapter 31 – Designing with Classes](#chapter-31--designing-with-classes)
  - [Chapter 32 – Advanced Class Topics](#chapter-32--advanced-class-topics)
- [Part 7 – Exceptions and Tools](#part-7--exceptions-and-tools)
  - [Chapter 33 – Exception Basics](#chapter-33--exception-basics)
  - [Chapter 34 – Exception Coding Details](#chapter-34--exception-coding-details)
  - [Chapter 35 – Exception Objects](#chapter-35--exception-objects)
  - [Chapter 36 – Designing with Exceptions](#chapter-36--designing-with-exceptions)
- [Part 8 – Advanced Tools](#part-8--advanced-tools)
  - [Chapter 37 – Unicode and Byte Strings](#chapter-37--unicode-and-byte-strings)
  - [Chapter 38 – Managed Attributes](#chapter-38--managed-attributes)
  - [Chapter 39 - Decorators](#chapter-39---decorators)
  - [Chapter 40 - Metaclasses](#chapter-40---metaclasses)
  - [Chapter 41 – All Good Things](#chapter-41--all-good-things)
- [Part 9 - Appendixes](#part-9---appendixes)

# Preface

- This book is intended to focus on the core of Python, not necessarily the application thereof, that is the domain of future reading
- _Programming Python_ is intended to serve as volume 2 of this series
- This will serve you well in all applications, but the more common and likely to be used post-reading are Django, NumPy, and App Engine
- Linear reader's will find this book similar to a semester long course
- X vs. 3.X
  - X is seen as the cutting edge sandbox, while 2.X is seen as the tried and true
  - 7 is planned to be the last revision of the 2.X branch
  - As long as you understand the divergence it is usually quite easy to learn to program in both
- The book is intended to cover both branches rather than one or the other
- Choose to install 3.X if you are a newcomer and do not need to support older Python code regularly, it has a few less libraries but is ever evolving, adapting, and expanding
- Choose 2.X for existing code bases or greater stability, but you will not receive new techniques or tools like the 3.X branch does
- This book also contains branch neutral code, as much of Python is not specific to one branch, but is shared between them
- Each part covers a certain functional area, with chapters focusing on a specific topic or aspect of that area. Each chapter then ends with quizzes and their answers, as well as larger projects with answers in Appendix D
- Practice is key, do each example and project to make sure you fully understand the material that is being discussed, there is no substitute for practice
- The book is as linear as Python allows, meaning it reduces forward references as much as possible
- _Jython_ : the Java Python language implementation
- _IronPython_ : the .NET Python language implementation
- Source code for the examples can be fetched as a zip file from: [http://oreil.ly/LearningPython-5E](http://oreil.ly/LearningPython-5E)
- A bird indicates a tip, suggestion, or general note, while a scorpion indicates a warning or caution related to nearby text

# Part 1 – Getting Started

## Chapter 1 – A Python Q&amp;A Session

- Why do people use Python?
  - Highly readable code, which makes it far more reusable and maintainable
  - Contains support for deeper functions
  - Programmer productivity is often far greater than other compiled or statically typed languages, often resulting in code that is a fifth to a third the size of languages such as C, C++, or Java
  - Highly portable, meaning it can run on any major OS with essentially a copy paste
  - Huge number of support libraries, including those like _NumPy_ (which is often compared to Matlab)
  - There is a high degree of component integration, meaning it can invoke or be called by, other languages, can operate over serial ports, networks, etc.
  - Many people think it is quite enjoyable to use, especially compared to other languages
- One sentence description: a general purpose programming language that blends procedural, functional, and object-oriented paradigms
- The downside of Python is that it can take longer to run at execution compared to a fully compiled language like C, but _PyPy_ and similar tools can assist in this regard
- Python can also create a dependency on pre-coded tools and extensions, which as a beginner is very helpful, but you will eventually outgrow
- _PyXLL_ and _DataNitro_ allow for Excel spreadsheet function and macro programming
- _PyBrain_ : neural net library
- _Milk_ : machine learning toolkit
- Data visualization tools: _Mayavi, matplotlib, VTK, VPython,_ etc.
- Data mining tools: _Orange, Pattern, Scrapy,_ etc.
- Python's class model allows for advanced OOP (object oriented programming)
  - Polymorphism, operator overloading, multiple inheritance, etc.
- Some primary aspects of Python
  - Dynamic typing: stores the kind of objects when it runs, eliminating the need for type and size declaration
  - Automatic memory management: automatically allocates objects and reclaims them when they are no longer used
  - Programming-in-the-large support: includes tools like modules, classes and exceptions and its OOP focus allows componentization and reuse
  - Built-in object types: easy to understand and use, and adapt in size dynamically
  - Built-in tools: such as concatenation, slicing, sorting, mapping, and more
  - Library utilities: offers many built in abilities that allow for deeper application specific uses
  - Third-party utilities: open source by nature so there are many pre-coded tools out there in the community that can address a myriad of issues
- Python is mixable, in that it can be "glued" to other languages or used as the glue itself

## Chapter 2 – How Python Runs Programs

- Python downloads inherently include an interpreter, which behaves as an layer between your code and the hardware it is being run on
- Most Python files have the .py extension at the end for consistency
- General steps of executing Python code
  - Byte code compilation: your source code is first compiled into byte code, which is a platform-independent translation of your original code. This is done to speed up the true execution. The result is stored as a .pyc (compiled) in a subdirectory of the active directory titled _ _pycache_ _
    - Python checks the next time your run the program to see if you have made changes, if not it will execute the last .pyc version
      - Checks the source changes and the Python version used
    - Byte code can also be run without the original source code, thus you can ship a product without the source and just the byte code
  - The Python Virtual Machine (PVM): not a separate program, just a component that iterates through the code one by one
- Execution Model Variations
  - CPython: the standard
  - Jython: targets Java integration by compiling the Python code to Java classes and then running the resulting code in the Java Virtual Machine (JVM), this allows Python to use Java classes as if they were part of Python and for Java code to run Python code as an embedded language
  - IronPython: designed to allow Python programs to integrate with Microsoft's .NET Framework for Windows, as well as Mono for Linux
  - Stackless: enhanced and reimplemented version of CPython that is designed for concurrency, this includes new micro threading and other such lightweight alternatives to Python's standard multitasking tools
  - PyPy: replaces the standard PVM with a new JIT (just in time) compiler that runs while your program executes, not beforehand, thus getting faster as it runs longer
- Frozen Binaries: bundles together the byte code from Python, along with the PVM and other requisite libraries and files, then runs them as a standard executable (.exe on Windows) that does not require a Python installation
  - Some examples: _py2exe, PyInstaller, freeze, cx_freeze_

## Chapter 3 – How You Run Programs

- The Interactive Prompt
  - Starting an Interactive Session
    - As long as the interpreter is installed, the most platform neutral method is to open you system prompt and type _python_
      - On Windows use Command Prompt
      - On Mac use Terminal
      - On Linux use shell or terminal
  - The System Path
    - See Appendix A for more details on this topic if needed
    - Python 3.3 and beyond contains a launcher for Windows which allows you to run commands with py
    - Appendix B contains more information regarding the launcher
  - Where to Run: Code Directories
    - You can run all your code in a working directory (like a folder)
    - In Windows you can create such a folder in the File Explorer or in the command line using _mkdir_
    - Linux also uses the _mkdir_ command for creating directories
    - You can store code in the Python file itself, but it is not recommended as it may not survive a move or uninstall
  - Running Code Interactively
    - Pressing enter in the command will run the lines of code you typed
    - If you want to end a session
      - CTRL+Z on Windows
      - CTRL+D on Linux/Unix
    - You can also run multiline statements in the command prompt
  - Why the Interactive Prompt?
    - Although you are unlikely to write the bulk of your code here, it is great for experimenting and testing
    - You receive immediate feedback on errors, it won't crash your code but it will give you an error and identify the culprit
  - Do not type commands other than Python commands at the prompt, as it will return an error
  - Print statements are only needed in files, the output is automatic in the command prompt
  - You needn't indent in the command prompt (at least not when beginning)
  - If the interactive prompt returns … (or …. in some editions) then it is likely that the interpreter believes you are typing a multiline statement
  - The interactive prompt treats an empty line as the termination of a multiline statement, other methods simply ignore the blanks
  - The interactive prompt can only run a single statement at a time
- System Command Lines and Files
  - Modules: stored Python code in text files (no matter how it is called, it will run the module form top to bottom every time it is called out)
    - Also sometimes called programs
  - Scripts: a top level module that is usually used to indicate the topmost execution (like an app)
  - It is likely that a command shell and a text editor is all most Python programmers will ever use or need
  - Any files you wish to import must end with the _.py_ extension
  - Once written, you can call a script in the system command shell (not the python interactive prompt)
    - Must be run in the same working directory as the script is saved in
  - If you wish, you can save the output of your script to a file for later use
  - Use file extensions and directory paths at the system prompt, but not for imports (will be addressed later)
- Unix-Style Executables Scripts: #!
  - Return to pg. 60 if needed
- Clicking File Icons
  - Return to pg. 63 if needed, all notes are IDE and system dependent
- Module Imports and Reloads
  - Program architecture: most Python programs tend to be comprised of many lower level modules that are called out in higher level scripts
  - _import module_without_extension_: calls a module inside a higher level module or script
  - _reload_: recalls an imported module, as the Python will only load the module once per file per session
  - _import_ and _reload_ are part of the standard _imp_ library, so in order to use them you should use the _from imp import reload_ to load both functions into your code
  - Called function: a function that expects parentheses around the arguments
  - Statement: a function that does not expect a set of parentheses
- The Grander Module Story: Attributes
  - Namespace: a package of variable names
  - Attributes: names inside the namespace
  - You can use _import_ to then use the entire module with its attributes by calling them with a period in between (e.E.g. ``` import my_module my_module.my_function_1 ```)
  - You can also use the _from_ statement to import a unique attribute from a module then call that attribute in your code (e.E.g. ``` from my_module import my_function_1 my_function_1 ```)_
  - _dir(module)_: creates a list of the namespace held in square brackets and separated by commas
    - Items that are preceded by and succeeded by double underscores are variable defined in Python itself and are not useful to the conversation at this point
- Using exec to Run Module Files
  - pg. 74 if needed
- The IDLE User Interface
  - pg. 75-81 if needed
- Other Launch Options
  - Embedding Calls: when Python is run by another enclosed system, usually contained in another language or as a component of a program (like a game modification tool)
  - Frozen Binary Executables: packages your bytecode and the python interpreter into a single executable, typically packaged as such just prior to shipping
  - Text Editor Launch Options: dependent on the text editor
- Examples on pg. 89

# Part 2 - Types and Operations

## Chapter 4 - Introducing Python Object Types

- The Python Conceptual Hierarchy
  - Programs are composed of modules
  - Modules contain statements
  - Statements contain expressions
  - Expressions create and process objects
- Why Use Built-in Types?
  - They make programs easy to write
  - They are components of extensions
  - Often more efficient than custom data structures
  - Standard part of the language
- Python's Core Data Types
  - Literals: expressions that generate objects
  - Program units: functions, modules, classes
  - Dynamically typed: Python stores the types for you automatically without requiring declarations
  - Strong typed: you can perform on an object only operations that are valid for its type
  - Numbers
    - Includes integers, floating point numbers, complex numbers with imaginary parts, decimals with fixed precision, rationals with numerator and denominator, and full-featured sets
    - Supports common arithmetic operations like + for addition, * for multiplication, and ** for exponentiation
    - _math_ module: provides more advanced numeric tools (as functions)
    - _random_ module: performs random number generation and random selections
  - Strings
    - Sequence: a positionally ordered collection of other objects that maintain a left-to-right order among the items they contain
    - Sequence Operations
      - Indexing: coded list from the front, the first position is 0
      - You can also index from the end of a string using negative integers
      - You can also slice a selection using _[n_1:n_2]_
        - The end position is non-inclusive (exclusive)
      - You can also concatenate using the + sign
      - Repetition can be achieved with the string (or variable that the string is assigned to) being multiplied by an integer
    - Immutability: cannot be changed in place after they are created, but we can reassign a variable if we so choose
      - Numbers, strings, and tuples are immutable, while lists, dictionaries, and sets are not
    - You can alter a string to make a list of all the characters if you use _list(variable_assigned_to_string)_
    - Type Specific Methods
      - Method: operations that are attached to and act upon a specific object which are triggered with a call expression
      - Usually looks like _object.method_
      - Examples of string methods: _.find('substring'), .replace('substring_old','substring_new'), .split('delimiter'), .upper(), .rstrip()_ (rstrip removes whitespaces at the end of a string)
      - This do not change the original object, as it is immutable, however, you can create a new object with the method as part of its definition
    - _dir(object)_: shows all the functions and methods that can be assigned to the object
    - _help(object.method)_: shows the documentation
    - Unicode strings
      - Return to pg. 108 if needed
    - Pattern matching is available in the _re_ package
  - Lists
    - No fixed size as well as mutable
    - Sequence operations
      - We can index, slice, match, repeat, etc. just like with strings
    - Type Specific Operations
      - Can contain many different types
      - Can resize on demand
      - _.pop(position)_: deletes the specified position
      - _.append(object)_: adds to the end of a list
    - Bounds Checking: although lists have no defined size, lists cannot return objects that are not in the range, nor can you modify a list to add items outside of the range (hence the append method)
    - Nesting
      - You can nest all types of objects in python, and to any arbitrary depth you wish
      - This allows for the creation of matrixes using a list as a list object (if you bracket a sub-list, then python can display on multiple lines to give a matrix type view)
    - Comprehensions
      - List comprehensions are derived from set notation and they provide a way to create new lists by running expressions over old lists
      - Comprehensions are coded in brackets and follow the convention: _[row_n optional expression for row in matrix]_
      - You can also include more complex operators, such as if statements (because the definition will repeat itself for all objects in the list)
      - This can also be used to select multiple values, as long as we wrap those values in a nested collection
      - E.g. ``` list(range(5)) ``` can be imbedded into a list, then we can select on that embedded list inside a list to grab multiple values
      - List comprehensions can also be used to create sets and dictionaries
        - E.g. ``` {sum(row) for row in M} ``` (where M is a matrix)
  - Dictionaries
    - Similar to lists in that they are mutable and are ways to store collections of objects
    - Do not store the objects in a reliable left-to-right order, rather they store based on key (also called mapping)
    - Mapping Operations
      - When written as a literal, they follow the convention: _{'label':'object', 'label_2':'object',…}_
      - Rather than using the relative position of the object, we reference the intended object by using the defined label
      - It is more common for dictionaries to be assigned not by literals, but rather by functions that add the new label and item to the dictionary
  ``` python 
D = {}_
D['name'] = 'Bob'
```
      - You can easily use this functionality to search a dictionary, by using the key (label) to return the desired object
    - Nesting Revisited
      - You can imbed a dictionary into a object in another dictionary, this can create a table like structure
    - Missing Keys: if Tests
      - Like other data types, dictionaries also have certain methods that are type specific
      - Fetching an object that doesn't exist will still return an error, as fetching non-existent objects will inherently come up as NULL
      - _in_: used to search for a key in a dictionary
        - E.g. ``` 'name' in D ``` (looking for the name key in dictionary D)
    - Sorting Keys: for Loops
      - If you needed a dictionary to be ordered with some logic, you could use a sort and a for loop to recreate the output
``` python
Ks = list(D.keys())
Ks.sort()
for key in Ks:
print(key, ',', D[key])
```
  - Output would be an ordered dictionary based on the sort order
      - Recent versions of Python have included a new built-in function called _sorted_
``` python 
for key in sorted(D):
print(key, ',', D[key])
```
  - Iteration and Optimization:
    - An object is iterable if it is either a physically stored sequence in memory, or an object that generates on item at a time in the context of an iteration operation
    - Tools such as map and filter are often faster in modern version of Python that using a for loop (up to twice as fast)
    - To test some of the performance, Python has a few tools defaulted: _time, timeit, profile,_ etc.
  - Tuples
    - Essentially an immutable list (a sequence)
    - They are syntactically created with parentheses, can contain arbitrary types, arbitrary nesting, and common sequence operators
    - Why Tuples?
      - The immutability of the object makes it ideal for large programs where you mass pass the object around multiple times, if you had a list it may be changed at any point, but a tuple cannot be altered, hence offered a type of integrity constraint
  - Files
    - There is no real default method to creating an object, rather, we typically use the _open_ function and an optional processing mode as strings
    - If you omit the processing mode it will assume you are in read mode
  - Binary Bytes Files
    - Represents data in a special byte format that allows you to access file content unaltered
    - Most useful when accessing things like media files, data created by C and other languages, or other non-text data
  - Unicode Text Files
    - Can be used to process things like memos and emails, all the way to JSON and XML documents
    - You can easily encode or decode text that is not your machine's default by passing along the encoding name you wish to use
      - E.g. ``` file = open('unidata.txt', 'w', encoding = 'utf-8') ```
  - Other File-Like Tools
    - _Open_ is the workhorse of Python file processing
    - There are other types, namely: pipes, FIFOs, sockets, keyed-access files, persistent object shelves, descriptor-based files, relational and object oriented database interfaces, etc.
  - Other Core Types
    - Sets: an unordered collection of unique, immutable objects (neither a mapping nor a sequence)
      - Often used for things like filtering out duplicates, isolating differences, or performing order neutral equality tests
    - Decimals: floating points with fixed precision
    - Fractions: contain both a numerator and a denominator in order to avoid the inherent inaccuracies of converting to a floating point
    - Booleans: a simple TRUE/FALSE object, abbreviated to "bool" when defining
- How to Break Your Code's Flexibility
  - The _type_ operator returns the type of the identified object, including itself if you so choose
  - This is really not a good thing to do, as Python uses interfaces to transform types, it doesn't really care what type the object is, rather we care about what we can do with the object. If we check all types we limit our ability to transform them
- User-Defined Classes
  - These are newly defined types that are made with the function _class_
  - These can include new methods that can be user defined
  - Often these classes build upon built in types
- Chapter summary on pg. 133
- Examples on pg. 134

## Chapter 5 - Numeric Types

- Numeric Type Basics:
  - Integer and floating-point objects
  - Complex number objects
  - Decimal: fixed-precision objects
  - Fraction: rational number objects
  - Sets: collections with numeric operations
  - Booleans: TRUE/FALSE
  - Built in function and modules: _round, math, random,_ etc.
  - Expressions: unlimited integer precision, bitwise operations, hex, octal, and binary formats
  - Third party extensions: vectors, libraries, visualization, plotting, etc.
- Numeric Literals:
  - If you write a number with a decimal or exponent, then it is stored as a float
  - Hexadecimals can be coded with a leading 0x or 0X
  - Octals can be coded with a leading 0o or 0O
  - Binary literals can be coded with a leading 0b or 0B
  - If you wish to use a function to convert to these literals, you can use _hex(), oct()_ or _bin()_
  - _complex(real, imaginary)_: used to create complex numbers
- Built-in Numeric Tools:
  - Expression Operators: +, -, *, /, , **, &amp;, etc.
  - Built-in mathematical functions: _pow, abs, round, int, hex, bin,_ etc.
  - Utility modules: _random, math,_ etc.
- Python Expression Operators:
  - Full table of expression operators on pg. 141
  - Mixed operators follow operator precedence in their calculation
  - Operator Precedence follows these rules:
    - Lower in the table found on 141, higher the precedence
    - If they fall on the same level of precedence, they are evaluated left to right
    - Parentheses circumvent the levels of precedence (just be careful)
    - Types are converted up to the level of the most complex operand (e.E.g. integer multiplied by a float, would first convert up to a float, then multiply)
      - In numbers, it is typically integer, then float, then complex
      - You can also force the conversion by calling built in functions
    - Python typically only converts operand of the numeric types, a string and a float will return an error
    - Polymorphism: the operation depends on the types of objects being operated on
- Variables and Basic Expressions:
  - Variables are created when they are assigned values
  - Variables are replaced with their values when used in expressions
  - Variables must be assigned before they can be used in expressions
  - Variables refer to objects and are never declared ahead of time
- Numeric Display Formats:
  - There are other ways than the automatic echo or the _print_ function to display the stored bits of a number, namely: _num,_ using a string formatting expression, etc.
  - _repr_: shows the as-code form of a string
  - _Str_: prints a user-friendly form of the string
- Comparisons: Normal and Chained:
  - Comparison operators perform exactly as would be expected, including type conversion to the most complex operand
  - Chaining multiple comparisons can produce more complex comparisons
    - E.g. _a  b  c_ would be equivalent to (_a  b) and (b  c)_
  - You can chain an arbitrary number of comparisons together, but they can become unintuitive if you do not pay attention to the method by which Python evaluates these expressions
  - You must be careful when using comparisons for floats, the storage of an object may have a certain precision limitation that could alter your comparison
- Division: Classic, Floor, and True:
  - X / Y: classic and true division. In 2.X this would only perform classic division and store the results of the integer division. In 3.X it will perform true division, which will store the remainders in floating point results
  - X // Y: floor division. Truncates fractional numbers down to their floor, regardless of types (the result type is dependent on operand though)
- Supporting either Python:
  - If your programs depend on integer division, you can use // in both branches
  - If you need floating point division you can specify this by using / and converting one of the variables/objects to a float (this will guarantee it saves the output as a float)
  - You can also import the 3.X division standards into 2.X by using the __future__ import statement
    - E.g. _from _future_ import division_
- Floor vs. Truncation:
  - // is technically called truncating division, but it is also accurate to call it floor division in that it truncates the result down to its floor
  - The use of floor division is more accurate, in that it will truncate but it's essentially rounded down to the nearest whole number
    - E.g. 2.5 would be 2, -2.5 would be -3
  - Truncation is the same as floor for positive numbers, but for negative it is always floor, hence this section
  - If you wish to actually use truncation for negative numbers, then you can use _math.truncate_ from the _math_ package
- Integer Precision:
  - In 3.X, all integers are stored as the same type, in 2.X they are stored as short of long
    - Long integers in 2.X are only distinguishable by the trailing L after the integer
- Complex Numbers:
  - Complex numbers are stored as two floating points: the real and the imaginary
- Hex, Octal, Binary: Literals and Conversions:
  - Return to pgs. 156-158
- Bitwise Operators:
  - Return to pgs. 158-160
- Other Built-in Numeric Tools:
  - From the _math_ module:
    - Functions: _sin, sqrt, pow, abs, min, round_ etc.
    - Method: _.floor, .trunc, .format,_ etc.
  - These functions allow for multiple ways to compute the same thing
    - E.g. to find the square root you could use _math.sqrt(), x ** .5, pow(x, .5)_
  - Standard libraries must always be imported, but built-in functions do not require imports
- Other Numeric Types:
  - Decimal:
    - Essentially a fixed precision float
    - Because floats have certain limitations in precision, we can compensate by using the decimal type and specifying the number to the accuracy we determine
    - Decimals have seen a substantial increase in performance but they are still slower than floating point calculations
    - You can define the number of decimals globally by using _decimal.getcontext().prec = n_
    - You can also locally define precision using a _with_ statement as follows:

_with decimal.localcontext() as ctx:_

_ctx.prec = n_

_expression_

  - Fraction:
    - Because fractions do not map to hardware as well as floats, there may be performance penalties, but their usefulness make them worth exploring
    - Syntax: _fraction(numerator,denominator)_
    - Fractions can also be made using floats or strings
    - Fractions will also simplify the results (3/6 to ½ for example)
    - Can convert from float to fraction or vice versa:
      - _float_or_variable_of_type_float.as_integer_ratio()_ returns two arguments (numerator and denominator)
      - _Fraction(*float_or_variable_of_type_float.as_integer_ratio())_ returns the fraction type with two arguments
      - _float(fraction_or_variable_of_type_fraction)_ returns a float
      - _Fraction.from_float(float_or_variable_of_type_float)_ returns fraction
  - Sets:
    - Sets are a grouping of unordered, unique, immutable objects, hence it behaves similarly to a valueless dictionary
    - Sets allow for iterable logic tests, such as:
      - _x -y_ difference
      - _x | y_ union
      - _x &amp; y_ intersection
      - _x ^ y_ symmetric difference (XOR)
      - _x  y_ superset (or subset if using )
    - Sets also have methods such as _.intersection, .add,_ and _.remove_
    - Generally these expressions require two sets, but the methods tend to be more flexible and work better with all types of iterable objects
    - Sets can now be called as literals in 3.X
      - e. _set([1, 2, 3, 4])_ and _{1, 2, 3, 4}_ are the same
    - Lists and dictionaries cannot be imbedded in sets, because they are mutable, but tuples can be stored
    - Because sets are mutable themselves, they cannot be nested inside other sets, in order to do this you must use _frozenset_ which makes an immutable set
    - Set comprehension can also be used similarly to list comprehensions
      - E.g. _{x ** 2 for x in [1, 2, 3, 4]}_ outputs the set _{16, 1, 4, 9}_
    - Because sets only store a value once, they can be used for things such as filtering out duplicates
    - The ordering may alter when converting to or from a set due to the unordered nature of sets themselves
  - Booleans:
    - _bool_ is effectively a class built on top of the class _int_ that has custom printing logic to treat 1 as TRUE and 0 as FALSE
- Numeric Extensions:
  - Libraries such as NumPy and SciPy
- Summary and examples on pgs. 178-180

## Chapter 6 - Dynamic Typing Interlude

- The Case of Missing Declaration Statements:
  - Statically typed languages such as C, C++, or Java do not have the same flexibility that Python does because their code requires type declarations (thus, no polymorphism)
- Variables, Objects, and References:
  - Variable creation: first occurs when you assign a value to a name. Every subsequent reassignment alters the value assigned to the name
  - Variable types: variables contain no reference to type or constraints, the type information is stored with the object and not with the name
  - Variable use: variables must all be assigned before they are used, because as soon as they are called in later code they are immediately replaced with the object they reference
  - Reference: the link between names and objects
- Objects are Garbage-Collected:
  - When assigning a variable, the previous object it was referencing is remove from memory if the object is no longer referenced by another variable or object
  - Internally, Python stores a counter for each object based on the number of times it is referenced, when this counter reaches zero, the object is removed from memory to free up additional space
  - Python also contains a cycle-detector that makes sure items with a circular reference are also removed, even though they would not be caught by the reference counter
- Shared References:
  - Shared reference: when more than one variable references the same object in the background
    - E.g. _a = 3 b = a_ the net effect of which is both a and b reference 3
  - It is impossible to link a variable to another variable, because in the background the reference are to the objects
  - If you assign a variable a, then assign a variable b as a reference to a, you are actually assigning a reference to the object a represents. If you assign a to a new value, b will retain the original reference unless overwritten
- Shared References and In-Place Changes:
  - In-Place changes are only possible on mutable objects (altering the object itself)
  - When altering an object (such as a list) that has shared references, if it is mutable then you will be performing an in-place change, which will then affect all the variables that have referenced said object. We are not creating a new object for a reassignment, we are effectively altering the object behind the references
  - If you wish to avoid this, you can always have Python copy the first object and create a new one with the desired modification, leaving the original unchanged
- Shared References and Equality:
  - _==_ will test for the same values and return TRUE if they are equivalent
  - _is_ tests to see if the variables reference the same object, and will return TRUE if they do
  - Because small integers and strings are stored in cache, it is possible for _==_ and _is_ to both return TRUE even if they would otherwise show TRUE and FALSE (this is because although they may be referencing two different objects to the user, the object is stored in memory and thus retained for later use, reappearing for the second assignment and thus evaluating _is_ to TRUE)
  - _sys.getrefcount()_: function from the _sys_ module to return the count of reference there are to an object
- Summary and examples on pgs. 192-193

## Chapter 7 - String Fundamentals

- String Basics:
  - Python strings are categorized as immutable sequences, meaning they retain a left to right order and they cannot be changed in place
  - Triple quotes allow for multiline commenting
- String Literals:
  - You can use single quotes, double quotes, triple quotes, escape sequences, raw strings, bytes literals, and Unicode literals to write strings
  - Primarily, literals are written using the single or double quotes
  - Python with automatically concatenate any strings literals that are not separated by a comma, this can also be explicitly called using the + operator
- Escape Sequences Represent Special Characters:
  - Identified by the \ character preceding the escaped text
  - \n creates a new line
  - \t creates a new tab
  - _len()_ will ignore the escaping characters and only return the true number of characters that a print() function would output
  - Some other escape code sequences:
    - \\ - stores one \
    - \' - stores single quote
    - \a - Bell
    - \b - Backspace
    - \f - formfeed
    - \r - carriage return
    - \v - vertical tab
    - \xhh - character with a hex value of hh
    - \ooo - character with octal value ooo
    - \0 - null, binary 0 character
- Raw Strings Suppress Escapes:
  - It is common to see programmers reference things like "C:\new\test.txt" but this will have both a newline escape and a newtab escape
  - In order to use the text without escaping, the string literal must be preceded by an _r_
    - E.g. _r'C:\new_folder\test_file.txt'_
  - In this example you could also use to backslashes to save one of them in the output, but it is cleaner to use a raw string
- Strings in Action:
  - Basic Operations:
    - + can be used for concatenation
    - * is used for repetition
    - These are a clear example of operator overloading: we are using the same operators that accomplish addition and multiplication for concatenation and repetition, based on operand types
  - Indexing and Slicing:
    - Python starts positioning with a zero, so the first item is indexed to position 0
    - Using a negative in your index is actually adding the negative to the length of the string to essentially count backwards from the end of a string
    - E.g. _S[1:]_ returns all characters in string S starting with position 1 (the second character) and ending at the end of the string
    - When slicing, the offset pair (used to define the beginning and end of a slice) is inclusive for the lower bound (left side) and exclusive for the upper bound (right)
    - Slice boundaries default to 0 as the lower bound and the length as the upper
    - Extended slicing takes a third argument that accepts a stride (allows skipping of characters and can count backwards if using a negative value)
      - E.g. _S[1:10:-1]_ slices characters from 2 to 9, but backwards
  - String Conversion Tools:
    - Considering that Python will not guess the type an intent of operands, you must explicitly convert items that are not compatible (like str and int)
    - You can also convert a character to its underlying byte representation
  - Changing String I:
    - Because strings are immutable, you cannot change in place, rather you can use tools like concatenation, slicing, and indexing to create a new object, which can then be assigned to the original variable name if so chosen
    - Some common tools include: _.replace_ and _.format_ which do not alter the original string, but rather create a new object based on the original string
- String Methods:
  - Method Call Syntax:
    - Methods are technically attributes that are attached to object that happen to reference callable functions which always have an implied subject
    - Methods thus combine two operations: an attribute fetch and a function call
    - Attribute fetch: essentially tells Python to fetch the attribute of the object the method is acting upon
    - Call expressions: invokes the code of function x, passing along the proper arguments, and return the result value
  - Methods of Strings:
    - These are current as of 3.3, but they are subject to change. Consult the standard library manual if need be
    - _.capitalize, .casefold, .ljust, .lower, .center,_ etc.
  - Changing Strings II:
    - E.g. _S = 'spammy'_

_S = S.replace('mm', 'xx')_

_S_ outputs 'spaxxy'

    - The replace method is very common and it can take a third argument that specifies the number of replacements you want to take place
  - Parsing text examples on pgs. 220-221
  - Other examples on pgs. 221-222
  - Original string Module's Functions were deprecated in 3.X, to see a few return to pg. 222
- String Formatting Expressions:
  - Two common methods:
    - String formatting expressions: _'...%...' % (values)_
      - Revisit table 7-4 on pg. 226 to view all the special string formatting codes that can take the place of %
        - E.g. %e takes a floating point with an exponent
    - String formatting method calls: _'...{}...'.format(values)_
  - Examples of formatting expressions on pg. 227
- Dictionary-Based Formatting Expressions:
  - You can use a dictionary (defined after the string) and use the index to format a string
    - E.g. _'%(qty)d more %(food)s' % {'qty' : 1, 'food' : 'spam')_ outputs '1 more spam'
  - You can also define a string with the % contained inside of it and assign it to a variable, then assign a variable for the dictionary you want to reference, they use these as argument for print, of simply call one or the other to do string formatting
    - E.g. _reply = 'text %(number)d text'_

_values = {'number' : 1}_

_print(reply % values)_

Output: 'text 1 text'

- String Formatting Method Calls:
  - Curly brackets in the string contain the variables that will be inserted (either by position in the value dictionary or the index name or by the relative position [requires that the string ordering and value ordering are matched])
  - Examples on pg. 230 (too long to rewrite)
  - This method can also be used to include keys, attributes, or offsets
    - E.g. _'My {1[Kind]} runs {0.platform}'.format(sys = sys, {'kind' : 'laptop'})_

Output: 'My laptop runs Windows 10'

  - Extended discussion comparing the two, not relevant to this reading (pgs. 231-242)
- General Type Categories:
  - Types share operations sets by categories
    - The three categories are Numbers, Sequences, and Mappings
    - Each category has operations that act in the same manner independent of the type
- Summary and examples on pgs. 245-246

## Chapter 8 - Lists and Dictionaries

- Lists:
  - Lists are both mutable and can contain any other objects (like strings, numbers, or lists)
  - Lists retain a left to right ordering and thus are considered sequences
  - This ordering can contain any number of arbitrary objects
  - The positionality of lists allows you to reference objects based on their offset
  - The length of lists is arbitrarily expandable
  - Because lists can contain arbitrary objects, the objects themselves can be heterogeneous and arbitrarily nestable
  - Common list literals and operations can be found in table 8-1
    - Includes: _L = [], L = list(), len(L), L.append(), L.copy(),_ etc.
  - Lists in Action:
    - Basic List Operations:
      - Lists have similar operators to strings
      - Things like the + operator work as one would expect strings to, save for the fact that we are creating a new list
      - These operations include list iterations and list comprehensions
        - E.g. _res = {}_

_for c in 'SPAM':_

_res.append(c * 4)_

Output: ['SSSS', 'PPPP', 'AAAA', 'MMMM']

    - Indexing, Slicing, and Matrixes:
      - These operations function exactly as they do for strings except that the result is of the same type as the object stored at the offset
        - e. a str while stay a str, a decimal will stay a decimal
    - Changing Lists in Place:
      - It is possible to change either a single object in a list or a slice of a list
      - These modifications have implications for all references to the amended list object
      - Modifying a slice of a list is best thought of as deleting the previous objects in those offsets and inserting new ones
      - If you are writing more objects in than you are replacing, it will modify the length of the list starting at the specified offset
    - List Method Calls:
      - Include methods like: _.append, .sort,_ etc.
    - Sorting lists can be done with the _.sort()_ method, which can take a key argument (to define the sort order over things like capitalization), a reverse argument (for reversing the order), etc.
    - _.extend()_: iterates through and add each item in an iterable object to the list (append simply adds a single as is without iteration)
    - _.index()_: returns the position of the item in the argument
- Dictionaries:
  - The key difference between lists and key is that lists contain an ordered collection, while dictionaries have an unordered collection that is defined by a key rather than position
  - Dictionaries are part of the "mutable mapping" category
  - Internally, dictionaries are hash tables (data structures that support very fast retrieval)
  - Table 8-2 contains common literals and operations on pg. 260-261
  - Dictionaries in Action:
    - Indexing and other such operations are similar to lists, but because they are not sequences, certain functions like slicing and concatenation or not supported
    - Dictionaries can be changed in place using the key rather than the position
    - Dictionaries can contain arbitrary objects of arbitrary length much like lists
  - Dictionary methods include: _.values(), .items(), .get(),_ and _.update()_
  - _.pop_: common method that deletes the key and value, and returns the value to the user
  - Example on pgs. 265-266
  - Dictionary Usage Notes:
    - Sequence operation do not work
    - Assigning to new indexes adds entries
    - Keys need not always be strings
  - By using integers as keys in a dictionary, you can essentially create a more flexible version of a list
  - Avoid Missing-Key Errors:
    - Use an if to test for the key, otherwise return some other value
    - Use _try:_ to test for the key, otherwise return some other value
    - Use the _.get()_ method to return a key if it exists (the second argument specifies the value to return if the key is non-existent)
  - Methods for creating dictionaries on pg. 271
  - Dictionary change log on pgs. 273-280, not relevant to this reading
- Summary and examples on pgs. 281-282

## Chapter 9 - Tuples, Files, and Everything Else

- Tuples:
  - Tuples share most of their properties with lists other than the fact that tuples are immutable
  - Tuples are positionally ordered collections of arbitrary objects that are accessed by offset
  - They belong to the category immutable sequences
  - Like lists, tuples are best thought of as object reference arrays, and indexing them is fairly quick considering they point to other objects
  - Table 9-1 contains common literals and operations for tuples on pg. 285
    - These include: _T = tuple(), T.index(), T.count(),_ etc.
  - Tuples in Action:
    - Tuple Syntax Peculiarities:
      - Because parentheses can contain expressions, in order to define a tuple, of length 1 or greater, you must use a comma after the first entry and between all subsequent entries
      - Python will allow you to omit the parentheses when defining your tuples, and some argue for or against this, but the most common instances in which parentheses are required are:
        - Where parentheses matter: within a function call or nested in a larger expression
        - Where commas matter: within the literal of a larger data structure like a list, or listed in the print() statement of Python 2.X
  - Why Lists and Tuples?
    - Tuples, due to their immutability, have a certain level of integrity throughout your code because they cannot be changed
    - This is similar to "constant" declarations in many other languages
  - Records Revisited: Named Tuples:
    - Allows for the use of tuples in a similar key based position found in dictionaries
    - Remember, tuples are immutable, alterations cannot be made in place
- Files:
  - Named storage compartments managed by the operating system
  - _open_: used to take a file as an input and create a Python file object that is primarily used for taking inputs from and sending outputs to
  - Table 9-2 on pg. 291 contains common methods
    - Including: _.readlines(), .close(), .flush(),_ etc.
  - To open a file, call the _open()_ function, with the filename (either absolute or relative, without an extension it will assume it exists in the working directory) followed by a comma and the mode (read, write, etc.)
  - An optional third argument is used to control output buffering
  - Additional arguments are used for specific file types
  - Using Files:
    - File text always takes the Python str object
    - File iterators are best for reading lines (by iterating line by line with a for loop)
    - Content is strings, not objects
      - You must send the information you want to the file as an already formatted string, Python makes no formatting modifications
    - By default, output files are buffered, meaning they may not automatically be written to storage from memory. Using flush or closing the program will then force the buffered data to disk
    - Files are also seekable, meaning your scripts can jump around through them
    - The _close_ method is often optional, if it is called it will terminate the connection and flush buffered data. Because Python cleans out objects without references, it could be that Python will do this flushing automatically, hence making the call optional in many instances
      - Best practice is to explicitly call the close function, in case the language spec changes or you need to guarantee system resources
  - Files in Action:
    - Python will return the characters written to the file in 3.X
    - You can use the print function to return the file contents with the formatting from the file
    - If you wish, you could also iterate line by line with a _for line_ loop
      - E.g. _for line in open('my_file.txt'):_

_print(line, end = '')_

    - Remember to reference files with either raw strings, forward slashes, or with all backslashes escaped, else the reference may be invalid
  - Text and Binary Files: The Short Story:
    - Text files represent content as normal str strings, performing Unicode encoding and decoding automatically
    - Binary files represent content as a special bytes string, allowing programs to access file content unaltered
    - Return to pg. 296 if greater specificity is needed
  - Storing Native Python Objects: pickle:
    - _eval()_ can often be too powerful, and can delete all your files if you let it
    - The standard Python package _pickle_ can help avoid this problem
      - Assign an object, assign an opened file, call _pickle.dump()_
    - pickle allows us to serialize the storage of objects, meaning it converts them to strings and back on its own
    - _shelve_ is another Python package that allows for storage of objects in an access-by-key filesystem (examples in chapter 28)
  - Storing Python Objects in JSON Format:
    - JSON is a program language agnostic data storage format
    - _json_ package allows for easy conversion of objects into JSON, which has a similar structure to Python lists and dictionaries
    - _json.dumps(name)_ to convert a named object into a JSON file
    - All JSON text is Unicode
  - Storing Packed Binary Data:
    - _struct_ package is used to pack and unpack binary data from sources like C or a network connection
- Other File Tools:
  - Standard streams: automatically opened file objects in the _sys_ module
  - Descriptor files in the _os_ module: integer file handles that support low-level tools
  - Sockets, pipe, and FIFOs: file-like objects used to synchronize processes or communications over networks
  - Access-by-key files (shelves): used to store unaltered and pickled Python objects by key
  - Shell command streams: support spawning shell commands and reading and writing to their standard streams
- Summary on pg. 305
- All comparisons are recursive in Python, meaning they are evaluated at the top level as well as their nested objects, and their respective nested objects, and so on
- 312-313 deal with differences between 2.X and 3.X, return here if needed
- Figure 9-3 on pg. 317 shows Python's type hierarchies
- Summary and examples on pgs. 321-326

# Part 3 - Statements and Syntax

## Chapter 10 - Introducing Python Statements

- By combining statements, you specify a procedure that Python performs to satisfy a program's goals
- The Python Conceptual Hierarchy Revisited:
  - The hierarchy:
    - Programs are composed of modules
    - Modules contain statements
    - Statements contain expressions
    - Expressions create and process objects
  - The previous section explored the Expressions level, now we will dive into the statements level (one step higher)
  - Statements are always components of modules, which themselves are managed by statements
- Python's Statements:
  - Table 10-1 on pgs. 330-331 contains a summary of Python's statement set
    - Including: _if, elif, else, for, while, break, continue,_ etc.
  - _print()_ is not technically a statement as it is really a function call, but it is often seen as a statement because it is usually called on its own
- A Tale of Two ifs:
  - Python's goal is to make programmers' lives easier, so, often the syntax of Python will slightly differ from that of other languages like C or Java, in that it will eliminate some syntactic components and modify others for simplicity
  - What Python Adds:
    - All Python compound statements (statements that have other statements nested inside of them) follow the pattern:
      - _Header line:_

_Nested statement block_

    - This colon usage is unique compared to most other languages
  - What Python Removes:
    - Parentheses are typically optional (for testing a logical condition in the header)
      - Inclusion will not negatively affect the code, but they are unnecessary and it is best practice to remove them for clarity and "Pythonness"
    - End-of-Line is end of statement, meaning each statement is typically confined to a single line and although you can use semicolons to terminate a statement, they are unnecessary and not Python-like
    - End of indentation is the end of the block, meaning you need not bracket your statement or call specific block ending statements like end/endif
- Why Indentation Syntax?
  - Primarily due to readability, return to section for long-winded discussion regarding formatting
- A Few Special Cases:
  - Semicolons can be used as statement separators for statements that you want to fit on a single line
  - This does not work for compound statements (like if statements or while loops)
  - In order to make your statement span across multiple lines, all that needs to be added is some form of bracketed pair ( like (), [], or {}). Python will only consider the statement complete once the ending bracket is read
  - The body of a compound statement can appear on the same line as the header after the colon if you so choose
    - This is as long as the body is composed of a simple operation line print()
- Simple interactive loop example on pgs. 340-341
- User input math example of pg. 342
- Nesting code three levels deep on pg. 347
- Summary and examples on pgs. 347-348

## Chapter 11 - Assignments, Expressions, and Prints

- Assignment Statements:
  - Assignments create object references
  - Names are created when first assigned
  - Names must be assigned before being referenced
  - Some operators perform assignments implicitly
  - Assignment Statement Forms:
    - Table 11-1 on pg. 350 shows Python assignment statements
      - Includes =, +=, and x = y = z
    - Tuple- and list- unpacking assignments:
      - Python pairs the objects on the right side with targets on the left by position and assigns them from left to right (creating multiple tuples or lists in the process)
    - Sequence assignments:
      - Any sequence of names can be assigned to any sequence of values, ordered by position
      - Extended sequence assignment functions in much the same way, but it allows for more complex assignments
    - Multiple-target assignments:
      - Python assigns names to the object (which appears furthest on the right)
        - E.g. _a = b = c_ assigned object c to both name a and name b
    - Augmented assignments:
      - Use a simplified syntax to perform a modification to the variable and can actually run faster
        - E.g. _i += 1_ is the same as _i = i +1_
  - Advanced sequence assignment examples on pgs. 352-353
  - Extended sequence packing allows for the use of an asterisk and a name to create a list of objects to assign to that name
    - E.g. _seq = [1, 2, 3, 4]_

_a, *b = seq_

_a_

_b_

_# 1_

_# [2, 3, 4]_

    - Boundary cases:
      - The starred name may only reference one variable, but it is still assigned a list
      - If there is nothing left for a starred name, it is assigned an empty list
      - Errors will appear if using more than one starred name in an assignment, if there are too few names compared to values and no star, or if the starred name is not itself part of a sequence
  - All augmented assignments:
    - _x += y_
    - _x &amp;= y_
    - _x -= y_
    - _x |= y_
    - _x *= y_
    - _x ^= y_
    - _x /= y_
    - _x = y_
    - _x = y_
    - _x %= y_
    - _x **= y_
    - _x //= y_
  - Augmented assignment offer 3 benefits:
    - Less to write
    - The left side is only evaluated once
    - Optimal technique is automatically chosen
- Variable Name Rules:
  - Syntax: underscore or letter + any number of letters, digits, or underscores
  - Case matters, Python will treat X and x differently
  - Reserved words cannot be used in assignment (like _class_)
    - Table 11-3 on pg. 364 contains the reserved words found in 3.X
  - Common naming conventions:
    - Names that begin with a single underscore are not imported by a _from module import *_ statement
    - Names that have two leading and trailing underscores are system defined names that have special meaning to the interpreter
    - Names that begin with two underscores but not trailing underscores are localized ("mangled") to enclosing classes
    - The name that is a single underscore retains the result of the last expression in an interactive session
- Expression Statements:
  - Commonly only used as statements in two instances:
    - For calls to functions and methods
    - For printing values at the interactive prompt
- Print function discussion from pgs. 369-374, return if curious
- The standard output stream (where print writes its information) can be modified to output elsewhere, including to a file, as seen on pg. 375
- Version-neutral printing on pgs. 378-380 (not very pertinent to this study)
- Summary and exercises on pgs. 381-382

## Chapter 12 - _if_ Tests and Syntax Rules

- _if_ Statements:
  - In general terms, if determines which action to take from a selection based on the results of a logic test
  - Python lets you combine statements in a program sequentially and nest them arbitrarily
  - General format:

_if test_1:_

_statement_1_

_elif test_2:_

_statement_2_

_else:_

_statement_3_

  - The nested nature of the elif function allows for multiway branching (like a tree root)
  - There is an alternative to this multiway branching:
    - Using a dictionary to and an input variable, you can use the input variable as a key to look up the desired mapped value in the dictionary
    - E.g. _choice = 'ham'_

_print({'spam':1,_

_'ham':2,_

_'Eggs':3} [choice])_

    - Dictionaries can also handle other larger actions if you imbed a function as a value and reference it with the key like above
  - Blocks of code must always be indented to the same amount of white space otherwise the syntax may be incorrect and return an error or unplanned result
- Statement Delimiters:
  - Statements may span multiple lines if you're continuing an open syntactic pair
  - Statements may span multiple lines if they end in a backslash
    - Not generally recommended
  - Special rules for string literals: namely the triple quoted string
  - Can terminate a statement with a semicolon
  - Comments and blank lines may appear anywhere in a file, but comments terminate at the end of the line on which they appear
- Truth Values and Boolean Tests:
  - All object have an inherent true or false value
  - Any nonzero number or non-empty object is true
  - Xero numbers, empty objects, and the special object _NONE_ are considered false
  - Comparison and equality tests are applied recursively to data structures
  - Comparison and equality tests return True or False
  - Boolean _and_ and _or_ operators return a true or false operand object
  - Boolean operators stop evaluating (short circuit) as soon as results are know
- The _if/else_ Ternary Expression:
  - _A = Y if X else Z_
  - A equals Y if X is true, otherwise it will be equal to Z
- Why You Will Care: Booleans sidebar on pg. 397
- Summary and exercises on pgs. 398-399

## Chapter 13 - _while_ and _for_ Loops

- _while_ Loops:
  - Most general iteration construct
  - Effectively, it repeats a block of code for as long as a test condition evaluates to true
  - Once the test evaluates to false the code block is no longer executed and control is given to the next block
  - General format:

_while test:_

_statements_

_if test: break_

_if test: continue_

_else:_

_statements_

- _break, continue, pass_ and the Loop _else_
  - _break:_ jumps out of the closest enclosing loop (past the entire loop statement)
  - _continue:_ jumps to the top of the closest enclosing loop (to the loop's header)
    - Because it only jumps up if the test is met, you can have statements below that will run if False and won't run if True, removing the need for a nested if statement
  - _pass:_ does nothing at all, it's an empty statement placeholder
    - Effectively the same to statements as None is to objects
    - Ellipsis can perform the same function
  - _Loop else_ block: runs if and only if the loop is exited normally (i.e. without hitting a break)
- _for_ Loops:
  - General format:

_for target in object:_

_statements_

_if test: break_

_if test: continue_

_else:_

_statements_

  - _break, continue,_ and _if_ all function just as they would in a while loop
  - Any sequence can be used in a for loop as it processes all sequences
  - Tuples are also very useful in for loops as they are typically how Python interacts with databases such as SQL
    - E.g. _T = [(1, 2), (3, 4), (5, 6)]_

_for (a, b) in T:_

_print(a, b)_

    - Here, T (the outer list) is the database table, the nested tuples are the rows in the table, and each item in the tuple is one value in a column
  - Starred names can also work in for loops (such as (a, *b, c))
- Loop coding techniques:
  - _range_:produces a series of successively higher integers, which can be used as indexes in a for loop
    - E.g. _for i in range(3):_

_print(i, 'pythons')_

_#0 pythons_

_1 pythons_

_2 pythons_

  - _zip_:returns a series of parallel item tuples, which can be used to traverse multiple sequences in a for
  - _enumerate_: generates both the values and the indexes of items in an iterable, so we don't need to count manually
  - _map_: can have a similar effect to zip in Python 2.X, though this role is removed in 3.X
  - for tends to run faster than while, so it is to your advantage to use these tools to work with for whenever possible
  - Sequence Shufflers:
    - Return to pgs. 419-420 for examples
  - Non-exhaustive Traversals:
    - You can either use range or a sliced sequence to accomplish the same tasks of selecting only certain items to iterate over, the advantage is that range does not create a list as it iterates, whereas slicing does, meaning a very large string may take up more memory with slicing
  - Parallel Traversals:
    - _zip:_ allows for parallel processing of multiple list objects (not at the same instance in time, such as over multiple cores, but in the same loop)
    - _zip_ will automatically truncate any iterable objects to the length of the shortest
    - zip is also useful when creating dictionaries from list objects
      - E.g. _keys = ['spam', 'eggs']_

_vals = [1, 2]_

_D1 = dict(zip(keys, vals))_

_D1_

_# {'spam': 1, 'eggs': 2}_

  - _enumerate()_:
    - Returns a generator object that essentially give us a counter in a for loop without requiring the generation of a new named object beforehand
    - E.g. _S = 'spam'_

_for (offset, item) in enumerate(S):_

_print(item, 'appears at offset', offset_

_# s appears at offset 0 …_

- Summary and exercises on pgs. 429-430

## Chapter 14 - Iterations and Comprehensions

- Iterations: A First Look:
  - Iterables include objects that are either physically stored sequences, or objects that output a single value at a time within a loop (a virtual sequence)
  - This book uses the term iterable for something that is acted upon, and iterator as the output of the acting function
  - We can use the _readlines()_ method call multiple times to iterate through a file line by line, or we can use the __next__ method to simply pull the next line from the file
    - _next_ will raise a StopIteration exception at the end-of-file rather than returning an empty string like readlines() would
- Manual Iteration: _iter_ and _next_:
  - _next(name)_: is the same as calling the named object with the name method call
    - E.g. _next(f)_ is the same as _f._next_()_
  - Figure 14-1 on pg. 436 shows Python's internal iteration protocol in detail
  - For objects like list and some other built-ins, we must first call iter to generate an iterable object, and use next to iterate over that new object
- List Comprehensions: A Detailed First Look:
  - E.g. _L = [1, 2, 3]_

_L = [x + 10 for x in L]_

_L_

_# [11, 12, 13]_

  - There can be a large performance increase using comprehensions rather than typical for loops as these operations are done at C speed
  - Extended List Comprehension Syntax:
    - Embedded for loops inside list comprehensions can also contain an if statement to filter out items that you don't want to iterate on
    - More nested for statements may be added, each with an optional if statement
- Other Iteration Contexts:
  - _map_: an iterable that applies a function call to each item in the passed in iterable object
    - Returns an iterable itself, so it should be wrapped in a list
  - Many tools utilize the iteration protocol, including sequence assignment, _in_ membership tests, slice assignments, and the _extend_ method
  - Using _*arg_ in a function call you can pass along an iterable objects values into the function call, rather than writing them out explicitly
- New Iterables in Python 3.X:
  - Stronger emphasis on iterable than 2.X versions
  - Some functions like _range_ produce result sets that can have multiple _iter()_'s running at the same time, while others like _zip_ do not
- Summary and exercises on pgs. 458-459

## Chapter 15 - The Documentation Interlude

- Python Documentation Sources:
  - # comments : in-file documentation
    - Typically restricted to single statements or a small group of statements
  - _dir_ function : lists of attributes available in objects
  - Doctrings:__doc__ : in-file documentation attached to objects
    - Called like any other attribute: _object._doc__
  - PyDoc: _help_ : interactive help for objects
    - Contains docstrings as well as structural information
  - PyDoc: HTML reports : module documentation in a browser
    - In 3.2 and later it will start a server and open a browser showing the _help_ data in a more graphical manner
  - Sphinx third-party tool : richer documentation for larger projects
  - The standard manual set : official language and library descriptions
- Common Coding Gotchas:
  - Don't forget colons
  - Start in column 1
  - Blank lines matter at the interactive prompt
  - Indent consistently
  - Use _for_ loops rather than _while_ or _range_
  - Beware of mutables in assignments
  - Always use parentheses to call a function
  - Don't use extensions or paths in imports and reloads
- Chapter and part summaries and exercises on pgs. 484-487

# Part 4 - Functions and Generators

## Chapter 16 - Function Basics

- Functions are simply collections of statements that are designed to be reused
- Functions are also often referred to as subroutines or procedures
- Function serve two main purposes:
  - Maximize code reuse and minimize redundancy
  - Procedural decomposition:
    - Splitting tasks into well-defined roles for easier implementation
- Python specific function concepts:
  - _def_ is executable code:
    - It does not exist until the script reaches it
    - It is reasonable and sometimes useful to nest _def_ inside other calls like _def_ or _while_ loops
    - Functions inside modules are often run upon import to make them accessible
  - _def_ creates an object with a name:
    - This name is like any other
    - Can also be assigned attributes
  - _lambda_ creates an object but returns it as a result:
    - See chapter 19
  - _return_ sends a result object back to the caller
  - _yield_ sends a result object to the caller but remembers where it left off
  - _global_ declares module level variables that are to be assigned
    - By default variables are only local and are only live while the function runs
    - Global is a scope in which you can bind a variable
  - _nonlocal_ declares enclosing function variables that are to be assigned
    - This allows for the state to be retained when the function completes and can be used at a later run
  - Arguments are passed by assignment (object reference)
  - Arguments are passed by position unless specified otherwise
  - Functions are not object specific and can often work on several data types
- General format:

_def name(arg1,... argN):_

_statements_

- _return_ ends a function call once called, even if the rest of the function has not completed
- Because Python supports polymorphism, code is intended to operate on interfaces (like *) rather than on data types, so do not do type error correction or you will limit utility
- You must define a function before calling it, either in the script or in a module file

## Chapter 17 - Scopes

- Scope = namespace
  - The location of the name and in which namespace determines its visibility to the code
- Names are created at assignment time (execution) which Python used to bind the name to the namespace that is being used
- Names assigned inside a function are exclusive to that namespace by default:
  - You cannot reference them outside that space
  - The same name can be used elsewhere without consequence/interference
- Global variables are only global to the file in which they reside
- Recursion allows functions to call themselves, in which case each call gets its own copy of the local variables
- Functions that alter objects may touch globals without altering the name (be aware of such changes)
- Name references search (in order): local, enclosing module, global, built-in
- Other, less common scopes:
  - Temporary loop variables in some comprehensions (like for)
  - Exception reference variables in some try handlers
  - Local scopes in class statements
- _builtins_ is its own module and named as such, in order to view it you must import it first
  - You can use this knowledge to directly call built-in functions if needed
    - E.g. _zip is builtin.zip_ returns _true_
- Because the LEGB rule takes the first occurrence, it is possible to assign overtop a higher scope in the lower levels, thus hiding function
  - E.g. assigning a text value to a name called _open_ will override the ability to use _open_ in that scope for its normal use
  - The interactive prompt acts as a global, module scope
  - Keep this fact in mind as it may come back as a bug if you in fact require the name that you overwrote
- Aside: True and False are reserved names in the _builtins_ package, but can be reassigned, this could be funny as a prank, but is nightmarish to use
  - This is only true in 2.X, as 3.X reserves these words and cannot be reassigned
- Namespace declarations:
  - _global_ and _nonlocal_
  - Tells the function to alter the global name rather than a local variable
- Program design:
  - In general, functions should rely on arguments and returns rather than globals
  - Variables inside a _def_ are defaulted to local
  - This is often to reduce debugging complexity
  - Globals are often used to retain state information (information required for the next run) as locals are removed from the namespace upon return
  - Globals are often used in parallel processing as they are used as a shared memory space
    - Multithreading can be further researched in the "Programming Python" book
  - Minimizing cross-file changes is very important as it can be subtle
- Nested Scope:
  - This is the E in LEGB
  - When looking for a reference:
    - Will look in current scope (function, L), then will look at any lexically enclosing scopes (E) before going to G and B
    - Global declarations skip the E
  - When assigning a name:
    - Global skips the E, while _nonlocal_ assigns the name in the next closest enclosing function's local scope
- Factory Functions/ Closures
  - Factory functions (in design pattern language) or closures (in functional programming terms) are functions which remember values in enclosing functions, regardless of whether they are still present in memory
  - They have state retention (attached memory of previous states)
  - Each call to a factory function returns a new nested function with different state information
  - Classes often provide more support for state retention, but closures are lightweight and viable for certain applications
- Argument = Value in a def header is a good way to retain some basic state information, and is required for certain things like loop variables
- Discussion of nonlocal in greater depth on pgs. 529-540
- Summary and exercises on pgs. 540-542

## Chapter 18 – Arguments

- Key points:
  - Arguments are passed automatically by assigning objects to local variable names
  - Assigning to argument names inside a function does not affect the caller
    - argument names in the function header become new, local names
  - Arguments can be used to alter mutable objects
  - Immutable arguments are effectively passed "by value"
    - The object reference is not really a copy, but since immutable objects cannot be altered anyway, you are basically copying
  - Mutable arguments are effectively passed "by pointer"
    - These can be changed in place and thus are more like C and similar languages when they pass arrays as pointers
- Changing a mutable object in place can impact the other object references to that object
- We can use return to help us redefine objects if we wish by returning things like tuples and using the returned values as new replacement objects
  - This appears as if we are returning multiple values, although we are only returning a single object which can be used as multiple values
- Special Argument-Matching Modes:
  - These allow us to alter the default matching behavior (left to right with a requirement to pass as many arguments into the function as defined in the def header)
  - Positionals: matched from left to right
  - Keywords: callers can specify which argument in the function is to receive a value by using the argument's name in the call with _name=value_ syntax
  - Defaults: specify default values for functions in the advent that the caller does not have enough (with _name=value_ syntax as well)
  - Varargs collecting: can collect arbitrarily many positional or keyword arguments when preceded with one or two * characters
  - Varargs unpacking: can take the * syntax and reverse the operation by unpacking a collection into separate arguments
  - Keywords only arguments: arguments must be passed by name, not by position
  - Table 18-1 on pg. 550 can help show examples of these behaviors
- Details on the how Python interprets these different methods (for package designers more than developers) can be found on pgs. 551-552
- Why use keyword names rather than just positionals? They are far more self documenting and clearly show the purpose/utility
- Defaults (as defined in the def header) allow us to skip over certain arguments that would otherwise be required
- The _name=value_ syntax means keyword in a call but default in a def
- * is used for positionals while ** is used for keywords
  - Example:
    - _def f(a, *posargs, **keyargs): print(a, poargs, keyargs)_

_f(1, 2, 3, x=1, y=2)_

_output: 1 (2, 3) {'y': 2, 'x': 1}_

- When calling a function, the * can be used to unpack the collection of arguments instead of combining them
- These methods of arbitrarily long arguments are great for times when you do no know the function's arguments and must pass along an unknown number of them
  - For example, having a function that allows you to call multiple functions with different argument sets
- _apply_ in Python 2.X is now defunct, see pg. 558 for more detail
- You can use the * in the definition to tell Python that all subsequent arguments must be called using keyword syntax
  - Example:
    - def kwonly(a, *, b, c):
  - These can also contain default values if desired
- Example wakeup call on pgs. 562-565
- Example intersection on pgs. 565-568
- Example of emulating the print function on pgs. 568-571
- Summary and exercises on pgs. 571-573

## Chapter 19 – Advanced Function Topics

- Function Design Concepts:
  - Cohesion: how to decompose tasks into functions
  - Coupling: how function interact
    - Strive to use arguments as inputs and returns as outputs, thus being independent of external factors
    - Use globals only when needed
    - Don't change mutables unless the caller expects it
  - Size: functions should be relatively small and have a single purpose
- Recursive Functions:
  - Functions that call themselves either directly or indirectly in order to loop
  - Not super common in Python, but is very useful to know
  - Loop statements (like while) often provide a more natural way to do the same thing
  - _for_ is often more memory efficient and easier to write
- More info on call stacks/cycles on pgs. 582-583
- Function Attributes and Annotations:
  - Functions are objects, and thus can be passed into other functions, reassigned to new names, etc.
  - This first-class object model allows for embedding function names and arguments into things like tuples as well
  - Functions contain attributes and thus we can examine them to learn more about the function like any generic object
  - We can also create user defined attributes and use them for tasks like state information retention, thus eliminating much of the need for globals (they are accessible anywhere that the function is)
  - Annotations can be added for things like storing argument objects or return classes
    - See pgs. 588-589 for examples
- Anonymous Functions – Lambda:
  - These functions do not return an object, just itself
  - Often used for inline function definitions
  - Syntax:
    - _lambda arg1, arg2, … argN : expression using args_
  - Lambda is an expression, not a statement
    - Can appear where def might not be able to
    - Since lambda returns a function, the return can be assigned to a name
  - Lambda's body is a single expression
    - No need to define the return statement
    - Can only put so much information into a lambda
      - Limits things like nesting
  - Lambda follows the same scope rules, with itself having a set of locals (like a nested def)
  - Often used to code jump tables (lists or dictionaries of actions to be performed on demand, like squaring or cubing)
  - Lambda can also be nested, like the def
- Functional Programming Tools:
  - Mapping Functions over Iterables
    - _map_ is used to apply a function to an iterable object
      - Example, apply the print function to a list of text objects
    - _filter_ is used to select an iterable's items based on a test function
      - Works like map, but only returns values that succeed
    - _reduce_ is like filter or map, but instead it returns a single result
      - This function works by taking the value of the previous iteration and passing it into the next lambda/function
      - For summation, this would be like summing the first two numbers, then adding them to the third, then adding all that to the fourth
- Summary and exercises on pgs. 600-602

## Chapter 20 – Comprehensions and Generations

- List comprehensions:
  - Apply an arbitrary expression to items in an iterable
  - The syntax is an expression with a defined variable, then what looks like a for loop, all surrounded in brackets
    - Example: _res = [ord(x) for x in 'spam']_
  - This syntax also allows for if statements to be employed without requiring filter
    - Example: _[x ** 2 for x in range(10) if x % 2 == 0]_
    - This example returns the square of even numbers between 0 and 9
  - List comprehensions are also very useful for matrix operations like selecting rows, diagonals, etc.
  - List comprehensions are often faster than map calls, which in turn are often faster than for loops that all do the same task
- Generator Functions and Expressions:
  - Functions are coded like def statements, but use yield to return one result at a time and suspend then resume their state between runs
  - Expressions are like list comprehensions except they return an object that produces on demand results, rather than a result list
  - This allows us to save compute time (lazy calculation) and split the computation across result requests
  - Generator functions retain their state information when suspended for the next run
    - This includes their local scope
  - Further detail on expressions on pgs. 619-624
    - Most of the concepts are already laid out in list comprehensions, just with the result set not being calculated all at once
  - Both generator functions and expressions are iteration objects and thus only support a single active iteration
    - This means no matter how you reference or run the generator, it will iterate in sequence, thus you could call it using multiple methods back to back and see that the state is retained each time
  - Example code found on pgs. 632-637
- Explicit is Better than Implicit (EIBTI) also very much applies to generators, as they may provide for shorter code, but might obscure the purpose
- Example emulating _zip_ and _map_ on pgs. 640-644
- Summary and exercises on pgs. 649-650

## Chapter 21 – The Benchmarking Interlude

- Return to this chapter to see more in-depth analysis of the iteration alternatives and their relative performance (pgs. 651-684)
- This is not necessary upon the first reading, but information like _timeit_ and impacts based on call type and operation type can be found here
- Summary and exercises on pgs. 684-688

# Part 5 – Modules and Packages

## Chapter 22 – Modules: The Big Picture

- Typically, modules relate to Python program files, and all files are modules
- Modules may contain extensions in other languages
- _import_ is used to fetch the module (as a whole)
- _from_ allows fetching of certain name(s) from modules
- _imp.reload()_ allows for reloading a module's code without stopping the Python instance
- Modules have 3 main roles:
  - Code reuse
  - System namespace partitioning
  - Implementing shared services or data
- Python Program Architecture:
  - Typically contains a master, high level file, that will call 0+ other modules, where statements are contained and do the work
  - The top level is usually just called a script and contains the flow of the program
  - Modules can be called in the script and may in turn call other modules
- Import statements are not executed until runtime, thus, cross linking modules does not create any processes until runtime
- Import also creates the objects in the library, so they do not exist until we import them
- Anything in the main namespace of the modules becomes a method on the module
- There is a group of standard library modules that are designed to run portably (anywhere where you can run Python itself)
- What happens on an import statement:
  - Finds the module file
  - Compiles it to byte code
  - Runs the module code to build the objects
- The second run does not do these three steps, only fetches the required objects
- After Python 3.2, Python will attempt to save the compiled byte code in a file (rather than just in memory during execution), but will discard the byte code from memory upon exit
- Module Search Path:
  - The home directory of the program
  - PYTHONPATH directories (if set)
  - Standard library directories
  - Contents of any .pth files
  - The site-packages home (third party extensions)
- The search path can be manually altered and things like the PYTHONPATH allow for users to define search priority
- Imports do not contain file extensions like .py in order for the search path to match things like compiled byte code as well
  - This is one reason why it is best practice to give files distinct names, as the selection picker is not always going to stay the same
- Import can use hooks to do things like import .zip file or decrypt
- Summary and exercises on pgs. 707-709

## Chapter 23 – Module Coding Basics

- Import and from are both assignments
- Modules should end with .py for reusability
- Files generate namespaces
  - Module statements run on the first import
  - Top-level assignments create module attributes
  - Module namespaces can be accessed via the attribute __dict__ or dir(M)
  - Modules are a single scope (local is global)
- Python automatically generates certain attributes during the import statement (like __file__ and __name__)
- Attribute name qualification removes the LEGB scope rules and finds the specified object.attribute
- Functions and modules cannot see names in other functions/modules unless they are enclosed or imported respectively
- Importing allows parent modules/files to nest downward, since we can use qualification to pull attributes into them
- Reload:
  - _reload_ is a function, not a statement
  - Passed as an existing module object, not a new name
  - Lives in a module and must be imported itself
  - This overwrites the existing namespace (not a deletion and refill)
- Summary and exercises on pgs. 728-729

## Chapter 24 – Module Packages

- You need not import just files; you can actually import directories which in turn are called packages
- Package importing creates a new namespace that contains attributes for the subdirectories and module files inside it
- In 3.3 and onward, each directory must contain a __init__.py file if named in the import
- Additional advanced information on pgs. 734-741
- Relative Imports:
  - X info on pgs. 742-758
  - 3 info on pgs. 759-766
- Summary and exercises on pgs. 766-768

## Chapter 25 – Advanced Module Topics

- Return to pgs. 769-801 for more info on hiding data in modules, namespace conflicts, ec.
- This chapter is not needed on the first reading so I skimmed it
- Summary and exercises on pgs. 801-804

# Part 6 – Classes and OOP

## Chapter 26 – OOP: The Big Picture

- X

## Chapter 27 – Class Coding Basics

- X

## Chapter 28 – A More Realistic Example

- X

## Chapter 29 – Class Coding Details

- X

## Chapter 30 – Operator Overloading

- X

## Chapter 31 – Designing with Classes

- X

## Chapter 32 – Advanced Class Topics

- X

# Part 7 – Exceptions and Tools

## Chapter 33 – Exception Basics

- X

## Chapter 34 – Exception Coding Details

- X

## Chapter 35 – Exception Objects

- X

## Chapter 36 – Designing with Exceptions

- X

# Part 8 – Advanced Tools

## Chapter 37 – Unicode and Byte Strings

- X

## Chapter 38 – Managed Attributes

- X

## Chapter 39 - Decorators

- X

## Chapter 40 - Metaclasses

- X

## Chapter 41 – All Good Things

- X

# Part 9 - Appendixes

55