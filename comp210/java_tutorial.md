# Java For the COMP 110 Python Developer

> Written by Ajay Gandecha for COMP 210: Data Structures and Analysis.<br>
> *Last Updated: 5/13/2024*

## Preface

**Welcome to COMP 210** - the first core course in the Computer Science major! 🥳 Many of you are fresh out of COMP 110, where you learned foundational programming and computer science concepts through the use of the *Python* programming language.

Computer science is all about solving problems with the use of computers. To solve problems using computers, we need to develop robust ways to *model* problems and situations in ways that computers can understand.

You have already learned many examples of this! Imagine you were a teacher, and you wanted to know the names of students in a class. How might you store these students names in a Python program?

If you answered with a *list*, that would be correct! You could imagine something like the following:

```py
students = ["Kris", "Kaki", "Alyssa"]
```

Now imagine you ran a cookie shop, and you wanted to store an inventory of ingredients! How might you store this in a Python program?

If you answered a *dictionary*, that would be correct! This might look like the following:

```py
inventory = {
    "flour" : 2,
    "chocolate chips": 8, 
    "eggs" : 0
}
```

Notice that both **lists** and **dictionaries** are two different "structures" that we can model problems / situations with! We call these types of models **data structures**.

COMP 210 is called "Data Structures and Analysis". Most of you signed up for COMP 210 knowing it is the first class in the Computer Science major, but might not really know what this course aims to each! Let's break down COMP 210's official course description:

> This course will teach you how to organize the data used in computer programs so that manipulation of that data can be done efficiently on large problems and large data instances. Rather than learning to use the data structures found in the libraries of programming languages, you will be learning how those libraries are constructed, and why the items that are included in them are there (and why some are excluded).

In computer science, the problems that we model can be *significantly* larger than just a small class roster or a cookie shop inventory. We can model entire company hierarchies, the US highway network, airports and plane travel - even processes that our computers run. As our problems grow larger and more complex, we *must* ensure that we model our data in a way that our computers can efficiently process. Computer chips can run billions of operations per second. However, if we do not model our data well, we might be doing unnecessary work - decreasing performance and wasting computing power in critical situations. Worse, if the way we model our data is extremely bad, we might not be able to solve these complex problems at all.

COMP 210 gives you a toolbox of such *data structures* - different ways that you can model problems and situations in code. It also teaches you the foundations of *time complexity* - determining *how efficient* your code is, and how you can make it better (through restructuring code).

To support this effort, and in many other classes after this, COMP 210 switches out of the world of Python and introduces the **Java** programming language.

Java is a **statically typed language**, which means that variable *types* are explicit and do not change once the variable is created, unlike Python is *dynamically* typed. Static typing provides *type safety*. Java will throw type errors if things go wrong with types in your code (such as types being converted incorrectly, or data being replaced with data of a different type). This may seem annoying at first, but in larger, more complex programs, this safeguard is *essential* to ensure your code is working as expected.

Java is used in many classes in our department, including (but not limited to):
* COMP 210: Data Structures and Analysis (this course!)
* COMP 301: Foundations of Programming
* COMP 433: Mobile Computing Systems
* COMP 520: Compilers
* *and more!*

Java is particularly popular for building large-scale enterprise applications, Android apps, and is also used in web servers and application servers.

This document is designed to help you become familiar with the syntax and features of Java from the context of the Python experience you all have had in COMP 110! It compares the syntax between Python and Java in various situations and should serve as a guide going into COMP 210.

## Structure of a Java Program

Java is an **object oriented language**. Remember that in Python, you could write *scripts* that ran from top-to-bottom, and in those scripts, you could create *classes*. **In Java, every file defines a new class**! Remember from COMP 110 that classes define a new *type* and serves as a "blueprint" for *objects* of the new type. Classes do not run automatically; just like in Python, *objects* need to be created first.

If every file in a Java program defines a new class, then how do we run any code?

In Java, there is a special method called a **main method** that we can add to a class. The main method serves as the *entry point* of a pogram. By adding this method to a class in our program, we designate the code in the body of the *main method* to be the code that runs when we run our Java program. This method is defined with the following signature:

```java
public static void main(String[] args) {}
```

This code probably looks very scary to you if you have never seen Java before - do not worry! You will learn what all of this syntax means in a later section. For now, there are a few things to keep in mind. To highlight this, let's look at the most bare-bones Java program you can write - a `hello world` program!

```java
public class MyApp {

  public static void main(String[] args) {
    System.out.println("Hello, world!");
  }
}
```

This Java file defines a class called `MyApp`, which contains our `main` method! Therefore, the code inside of this method is what runs when we run our program.

There are a lot of syntax differences that are apparent right away. Let's compare this code to what it would look like in Python:

<table>
<tr><th width="520">Java</th><th width="520">Python</th></tr>
<tr>
<td>
 
```java
public class MyApp {

  public static void main(String[] args) {
    System.out.println("Hello, world!");
  }
}
```

</td>
 <td>
  
```py
class MyApp:

  @staticmethod
  def main(args: list[str]) -> None:
    print('Hello, world!')
```

</td>
</tr>
</table>

You may begin to notice a few differences:
* In Python, we use a `:` after headers / definitions (like `class MyApp`), and then all of the code *inside* of the definition are indented. In Java, we instead surround all code inside of the definition with curly brackets `{ }`.
* In Python, we define functions / methods using `def`. In Java, we do not use a special keyword to define functions. Intead, we place the *data type* we expect to return first! In functions that do not return anything, we use the return type of `void` in Java. This is why the method header has `void main()`. In Python, the return type is placed afterwards, in `def main(...) -> None`.
* This also applies to arguments! Notice that in Python, we define the argument `args` as `(args: list[str])`. In Java, we put the data type first: `(String[] args)`. Notice that instead of `list[..type..]`, in Java we use `..type..[]`. This comes with more nuance, as these are not entirely equivalent data structures. We will talk about this later!
* Print looks different! In Python, `print` is built into the language, so we can call it as `print(text)`. In Java, the `println()` function is part of the `System.out` Java library. This is already available to us and we do not need to import it directly, but we still need to call the function using `System.out.println(text)`.
* Do not worry about the specifics with access modifiers (`public`) and the `static` keyword if you have not learned it already - we will talk about this later!
* Notice that in Java, **semicolons are required after every statement**! This does not apply to after curly brackets or headers, but it does apply to executable code *within* `{ }`.

Now that we have talked a little bit about the structure of a Java file and you have seen Java for the first time, we can begin to discuss Java's syntax.

## Syntax

The syntax for Java is a little bit more verbose than Python, but code is more explicit (and therefore intentional). In this section, you will learn the syntax of Java code with the context of the Python syntax you have worked in throughout *COMP 110*.

### Typing

The first major distinction between Python and Java is its typing system. Recall the following from COMP 110:

* **Primitive types** are a set of basic data types in a programming language. All other data types and classes can be constructed from these primitive types. Using standard programming conventions, primitive types are often denoted with an *all-lowercase* name and usually do not need to be imported.
* **Reference types**, on the other hand, are all of the other types in a language. Reference types are defined as structures that contain or build upon the basic primitive types. Reference types are defined by *classes*. Reference types, like the name of all clases, often start with a capital letter (For example, `Dog` or `Cat`).

In **Java**, we have the following *primitive* types:
* `int`: Represents a number with no decimal places.
* `double`: Represents a number that can store fractions (decimal places).
* `boolean`: Represents a state that can either be `true` or `false`.

Notice that *`string`* is **NOT** a primitive type! In Java, strings are represented as a reference type, and goes by the name `String`. This is because strings are *objects* that we can call methods on. We can only call methods on objects / reference types. Notice that in Python, this line is blurred. Java's type safety and langauge features keeps working with types more consistent.

### Variable Declarations

Now that you know a bit about the basic data types in Java, let's take a look at how to define **variables**.

Let's compare a number declaration in Python and Java, then compare more generally.

<table>
<tr><th width="520">Python</th><th width="520">Java</th></tr>
<tr>
<td>
 
```py
# Declaring a number
my_number: int = 88

# General Formula
name: type = value

# Reassign the variable
my_number = 100
```

</td>
 <td>
  
```java
// Declaring a number
int myNumber = 88;

// General Formula
type name = value;

// Reassign the variable
myNumber = 100;
```

</td>
</tr>
</table>

In Python, we put the *data type* after the `:` following the variable name. In Java, the data type always goes **first** and is *required* (unlike in Python, where you can omit it). When reassigning a variable already instantiated, however, the type is not repeated. 

Also notice the use of the semicolon at the end of the line!

Also, Java uses **camelCase** as convention for variable names rather than *snake_case*. So, when creating variable names with multiple words, the second word and on are capitalized, and words are not separated by *_*.

### Working with Strings

As you learned in the previous section, strings in Java are *objects*. In Java, we instantiate objects using the *`new`* keyword, the name of the class, and the parameters for its constructor. Here is the formula for insantiating objects:

```java
Type obj = new Type(inputA, inputB);
```

With this in mind, we can create a string like so:

```java
String welcomeMessage = new String("Welcome to COMP 110!");
```

Java also supports *string literal* syntax, which is far more common to use:

```java
String welcomeMessage = "Welcome to COMP 110!";
```

Notice that in Java, we use double quotes (`"`) rather than single quotes (`'`) to define strings like we did in Python. The use of both types of quotes is interchangeable in Python - it is **not** in Java! You must use double quotes.

Since strings are objects in Java, there are many methods that you can call on strings to perform certain actions. Below are a few examples:

<table>
<tr><th width="520">Method</th><th width="520">Usage</th></tr>
<tr></tr>
<tr>
<td>
 
```java
.length()
```

</td>
 <td>

This method is used to determine the number of characters in a string.

**Example:**
```java
String name = "Ajay";
name.length(); // Returns 4.
```
</td>
</tr>

<tr></tr>

<tr>
<td>
 
```java
.equals(otherString)
```

</td>
 <td>

This method is used to determine if two strings have the same sequence of characters.

*NOTE: We cannot just use `==` to compare strings! Using `==` compares the *memory addresses* of strings and not their actual contents. So, when comparing strings, make sure to use `==`!*

**Example:**
```java
String name = "Kaki";
String otherName = "kaki";
String finalName = "Kaki;

name.equals(otherName); // Returns false.
name.equals(finalName); // Returns true.
```
</td>
</tr>

<tr></tr>

<tr>
<td>
 
```java
.substring(startIndex, endIndex?)
```

</td>
 <td>
     
This method is used to create a new string containing characters from a starting to, but not including, the ending index in a string.

*NOTE: The ending index is optional (hence the `?`). Excluding it will just return a substring starting at `startingIndex` and ending at the end of the string.*

**Example:**
```java
String name = "Kaki";
name.substring(1); // Returns "aki".
name.substring(0,2); // Returns "Ka".
name.substring(0, name.length() - 1); // Returns "Kak".
```
</td>
</tr>

<tr></tr>

<tr>
<td>
 
```java
.indexOf(substring);
```

</td>
 <td>
     
This method determines whether or not a substring is present in the string. If it is present, the starting index of the substring is returned. If it is not present, an index of `-1` is returned.

**Example:**
```java
String name = "Kaki";
name.indexOf("ki"); // Returns 2.
name.indexOf("Ajay"); // Returns -1.
```
</td>
</tr>

</table>

There are many other string methods, but these are the most common ones! To see a more complete list, check out [this link](https://www.w3schools.com/java/java_ref_string.asp).

### Conditionals

Python and Java differ slightly in how we create *conditional statements* and *if-statements*.

Java has the same boolean operators, however they are written differently between languages.

<table>
<tr><th width="520">Python</th><th width="520">Java</th></tr>
<tr>
<td>
 
```py
a and b
a or b
not a
a == b
```

</td>
 <td>
  
```java
a && b // and
a || b // or
!a     // not
a == b // equals
```

</td>
</tr>
</table>

In Python, we represent truth values as `True` and `False`. In Java, these are lowercased as `true` and `false`.

Additionally, following in the C-family heritage, Java has a feature called short-circuit evaluation, which is used by the `&&` and `||` operators. If the left-hand expression of an `&&` operator is `false`, the right-hand expression will not be evaluated. Conversely, if the left-hand expression of an `||` operator is `true`, then the right-hand expression will not be evaluated.

Here is the syntax for **if-statements**:

<table>
<tr><th width="520">Python</th><th width="520">Java</th></tr>
<tr>
<td>
 
```py
if a and b:
  # Runs if a == True and b == True 
elif a:
  # Runs if A == True
else:
  # Runs if A == False 
```

</td>
 <td>
  
```java
if (a && b) {
  // Runs if a == true and b == true 
}
else if (a) {
  // Runs if a == true
}
else {
  // Runs if A == false 
}
```

</td>
</tr>
</table>

Notice that the use of `{ }` rather than `:` applies to control flow structures such as if statements (and loops). Also, **parenthesis are required around the conditional statements** in Java.

There is no combined `elif` keyword in Java like there is in Python. Instead, we have to use `else if`.

### While Loops

#### The `while` Loop

Just like with if-statements, both Python and Java have the same differences for while-loops! We use parenthesis around the conditional in loops too.

<table>
<tr><th width="520">Python</th><th width="520">Java</th></tr>
<tr>
<td>
 
```py
while condition_a:
 # Some code here!
```

</td>
 <td>
  
```java
while (conditionA) {
 // Some code here!
}
```

</td>
</tr>
</table>

### For Loops

In Java, there are two types of `for` loops. The first `for` loop functions similarly to the `for i in range(...)` loop in Python, where it creates a locally-scoped variable that increments through a range. Here is an example:

<table>
<tr><th width="520">Python</th><th width="520">Java</th></tr>
<tr>
<td>
 
```py
for i in range(0, 10):
  print(i)
```

</td>
 <td>
  
```java
for(int i = 0; i < 10; i++) {
  System.out.println(i);
}
```
</td>
</tr>
</table>

Both of these code snippets print `0` through `9`! The syntax for this type of loop in Java is expanded, but it helps to give a better sense of what is going on.

This type of loop in Java has three parts:

```java
for (variable declaration; conditional; step) {}
```

The *variable declaration* creates the counter `i` variable of type `int` and gives it a starting value of `0`. Then, we supply a *conditional*. Our loop will continue to run until this conditional turns `false`. Then, the final *step* part tells the program how to update the `i` variable after each iteration.

In Java, `i++` is shorthand for `i +=1`.

So, this loop creates a variable `i`, increments until `i` is no longer less than `10`, and after each iteration, `i` is incremented by `1`.

This type of for-loop is quite common, and it is helpful to get used to this syntax, as it is used in other languages as well.

### Defining Functions

Functions are the most fundamental abstraction technique we use in software engineering. It is important to note that in Java, we create *methods*, which are functions that are members of a *class*. In Python, you worked in the context of classes, but we are not necessarily required to. So, if you are hearing the term "functions" and "methods" passed around, it is useful to remember this distinction: methods are called on an object (e.g. `object.method()`) whereas functions are generally called standalone `function()`. In Java, we work with methods only, since all of our code is contained within classes.

Let's compare the function definition syntax of Python and Java.

<table>
<tr><th width="520">Python</th><th width="520">Java</th></tr>
<tr>
<td>
 
```py
def greet(name: str) -> str:
  return 'Welcome, ' + name + '!'
```

</td>
 <td>
  
```java
String greet(String name) {
 return "Welcome, " + name + "!";
}
```
</td>
</tr>
</table>

You will notice a few common themes throughout a lot of these syntax differences. In Java, we do not use `def` to create functions - instead, the *return type* of the function goes first! If there is no return type for a function, you must write `void` as the return type, like so:

<table>
<tr><th width="520">Python</th><th width="520">Java</th></tr>
<tr>
<td>
 
```py
def do_something() -> None:
  # Do something
```

</td>
 <td>
  
```java
void doSomething() {
  // Do something
}
```
</td>
</tr>
</table>

In parameter definitions, the type also goes first in Java.

### Extra TypeScript Features

#### Comments

The examples throughout this document have already used many comments, however here is how we write comments in Java!

<table>
<tr><th width="520">Python</th><th width="520">Jaca</th></tr>
<tr>
<td>
 
```py
# This is a single-line comment.

"""
This is an example of a
multi-line comment!
"""
```

</td>
 <td>
  
```ts
// This is a single-line comment.

/*
This is an example of a
multi-line comment!
*/
```

</td>
</tr>
</table>

## Conclusion

Congratulations! 🎉 Java is an extremely useful, industry-grade language - and you will have the chance to work with Java code throughout the entire class! If you are having trouble remembering Java syntax, feel free to return to this document at any time. As you have seen throughout your computer science careers so far, sometimes the best way to learn is to dive right in! So, if you want to practice Java, I highly recommend creating a new class in the Java 210 workspace and trying it out!
