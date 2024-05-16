# Introduction to Higher Order Functions

> Written by Ajay Gandecha and edited by Kris Jordan for the CSXL Web Application and for COMP 423: Foundations of Software Engineering.<br>
> *Last Updated: 12/18/2023*

## Preface and Recap

In the previous reading, you learned about *arrow functions*. Arrow functions are a more compact and concise method of defining traditional functions. Let's take a look at the following TypeScript function:

<table>
<tr><th width="520">TypeScript - Traditional Function</th></tr>
<tr>
<td>
 
```ts
/** Function that doubles the input number */
function doubleNumber(num: number): number {
  return num * 2;
}
```

</td>
</tr>
</table>

This function is rather simple - it takes in a `number` as an input, then returns *double that number* as its output!

Here, we are using the [traditional function syntax](https://github.com/unc-csxl/orientation/blob/main/frontend/typescript_tutorial.md#defining-functions) to define this function. We use the `function` keyword first, provide the name of the function, its parameters with type annotations, a return type of `number`, then the function body.

Now, using what you learned in the [arrow function section](https://github.com/unc-csxl/orientation/blob/main/frontend/typescript_tutorial.md#arrow-functions) of the *TypeScript for the COMP 301 Java Developer* reading, let's convert the `doubleNumber()` function into *arrow function syntax*.

<table>
<tr><th width="520">TypeScript - Traditional Function</th><th width="520">TypeScript - Arrow Function</th></tr>
<tr>
<td>
 
```ts
/** Function that doubles the input number */
function doubleNumber(num: number): number {
  return num * 2;
}
```

</td>
 <td>
  
```ts
/** Function that doubles the input number */
let doubleNumber = (num: number): number => {
  return num * 2;
}
```

</td>
</tr>
</table>

On the left is `doubleNumber` as a traditional TypeScript function, and on the right is `doubleNumber` as an arrow function. Both are perfectly valid ways to declare the `doubleNumber` function. In addition, we can call both functions in the same way - using `doubleNumber(num)`.

## Functions as Values

In the *arrow function* example, you probably notice something rather interesting. It appears that the arrow function syntax *uses the same syntactical structure we use to define variables!*

<table>
<tr><th width="520">Variables in TypeScript</th></tr>
<tr>
<td>
 
```ts
// General formula with type annotation:
let name: type = value;
// General formula without type annotation
// (where TypeScript infers the type):
let name = value;

// Examples
let courseCode: number = 423;
let name = "Maddy";
let thisIsSoCool = true;
```

</td>
</tr>
</table>

Now, let's take a look at our arrow function example:

<table>
<tr><th width="520">TypeScript - Arrow Function</th></tr>
<tr>
 <td>
  
```ts
/** Function that doubles the input number */
let doubleNumber = (num: number): number => {
  return num * 2;
}
```

</td>
</tr>
</table>

This follows the general formula for creating a TypeScript variable! Let's break this down:

<table>
<tr><th width="100"></th><th width="200">Name</th><th width="50"></th><th width="450">Value</th></tr>
<tr>
<td>

`let`
  
</td>
<td>
 
`
doubleNumber
`

</td>
<td>

`=`
  
</td>
 <td>
  
`
(num: number): number => { return num * 2; }
`

</td>
</tr>
</table>

As you can see, we are creating a *variable* with the name `doubleNumber`, our function name. But, woah - *our entire function is the value of this variable*! This is both simultaneously fascinating and scary. When we created the `doubleNumber` arrow function, we treated `(num: number): number => { return num * 2; }` as a value assigned to the name `doubleNumber`.

Let's take a step back and think about some examples of *values* that we typically store. Look at the following table:

<table>
<tr><th width="460">Variable</th><th width="150">Value</th><th width="213">Value's Type</th></tr>
<tr>
<td>
 
```ts
let course = 423;
```

</td>
 <td>

`423`

</td>
<td>

`number`
 
</td>
</tr>
<tr>
<td>
 
```ts
let name = "Kris";
```

</td>
 <td>

`"Kris"`

</td>
<td>

`string`
 
</td>
</tr>
<tr>
<td>
 
```ts
let yoda = new Jedi("Yoda");
```

</td>
 <td>

`Jedi("Yoda")`

</td>
<td>

`Jedi`
 
</td>
</tr>
</table>

In the examples above, we store various values - from primitive types in TypeScript to objects. ***Functions*** now join the list as a possible type of value that can be stored in variables.

In TypeScript, we can use the arrow syntax we learned to create ***function literals***. Function literals declare anonymous functions and are reference values. They define the three basic parts of a function - the *parameters (inputs)* that the function expects a caller's arguments to provide, the *return type*, and the *body* of the function that ultimately returns the evaluated value of a function call.

The function literal syntax looks like the following:

<table>
<tr><th width="520">Function Literal Syntax</th></tr>
<tr>
<td>
 
```ts
// Function literal used to define a function that
// takes in a number and returns double the number.
(num: number): number => {
 return num * 2;
}
```

</td>
</tr>
</table>

As you can see, this literal takes in a number and returns a number - just as shown in the arrow function syntax! 

Calling such a function literal directly is possible, but rarely used in such a fashion:

```ts
((num: number): void => { console.log(num); })(423)
```

(When such a construct is useful is a bit beyond our concerns, but as a hint it is a clever tactic for avoiding introducing any identifiers into a scope, like globals, while still giving you an isolated scope of function execution. In other words, it's useful in scenarios where might want to define a function and call it exactly once without giving any subsequent code the ability to call it again.)

In a sense, it's similarly as infrequent to use as directly subscripting a string, such as:

```ts
"abcd"[Math.floor(Math.random() * 4)]
```

<table>
<tr><th width="520">Values</th></tr>
<tr>
<td>
 
```ts
(num: number): number => {
 return num * 2;
}
// ... this does nothing without calling it directly!

let doubleNumber = (num: number): number => {
  return num * 2;
}
// Better! We can refer to this function definition 
// and call it from elsewhere.
```

</td>
</tr>
</table>

Hopefully, you are able to see how we can *use functions as values* to assign to a variable!

Lastly, remember that values always have a certain *data type* associated with them. Recall the table above - the `course` variable is of type `number`, the `name` variable is of type `string`, and the `yoda` variable is of type `Jedi`. So, *what type is `doubleNumber`*?

The type annotations for function literals *are based on their parameter types and return type*. The type annotation has the following formula:

`(param: type, param2: type, ...) => returnType`

So in this case, the type annotation for `doubleNumber` would be **`(num: number) => number`**!

Just like with normal TypeScript variables, we can also apply type annotations to our arrow function, like so:

<table>
<tr><th width="520">Arrow Function</th></tr>
<tr>
<td>
 
```ts
/** Function that doubles the input number */
let doubleNumber = (num: number): number => {
  return num * 2;
}

// OR

/** Function that doubles the input number */
let doubleNumber: (num: number) => number = (num: number): number => {
  return num * 2;
}
```

</td>
</tr>
</table>

Understanding the *typings* of functions and how to pass functions as values is ***extremely useful***. Let's explore some use cases for passing functions around as values!


## Passing Functions as Parameters

Let's take a look at the following example. Say that I have an *array of `number`s*. I want to create a function to *modify these numbers* so that I *call the `doubleNumber` function on every single one of them*!

So, if I were to have the following input:

`[0, 2, 4, 8]`

I expect the following output:

`[0, 4, 8, 16]`

Using what you learned from the TypeScript tutorial, we can create this function by utilizing some array functionality. Let's create this function as an arrow function and call it `mapNumbers()`. This function will take in an array of numbers (`numbers[]`) and return an array of numbers as well.

Feel free to try to implement this on your own as practice first, or look at the code below:

<table>
<tr><th width="520">Implement `mapNumbers`</th></tr>
<tr>
<td>
 
```ts
/** Function that doubles the input number */
let mapNumbers = (nums: number[]): number[] => {

 // Create an empty list of numbers
 let newNums: number[] = [];

  // Loop over all of the input numbers
  for(let num of nums) {
    // Modify the number
    let newNum = doubleNumber(num);
    // Save the new number
    newNums.push(newNum);
  }

  // Return the final number
  return newNums;
}
```

</td>
</tr>
</table>

We can now easily pass in an array of numbers, and it should return an array of numbers with all of its numbers doubled.

However, ***what if we want to make `mapNumbers` more multipurpose?*** *What if we wanted to have `mapNumbers` also be able to triple a number? Halve a number? Square the number?*

We *could* rewrite the `mapNumbers` function every single time, except that seems incredibly inefficient. *What if there was a way to pass in which function we wanted to modify each number with into the `mapNumbers` function?* So for example, I could pass in `doubleNumber` if I wanted my function to double the numbers, or pass in `squareNumber` if I wanted to square each number.

Well, ***we can!*** Since *functions can be used as values, we can use them as **function parameters** too!*

Recall how we implemented the `doubleNumber` function again. We could easily implement a few more functions like `doubleNumber` that would perform these other operations for us.

<table>
<tr><th width="520">Number Transform Functions</th></tr>
<tr>
<td>
 
```ts
/** Function that doubles the input number */
let doubleNumber: (num: number) => number = (num: number): number => {
  return num * 2;
}

/** Function that triples the input number */
let tripleNumber: (num: number) => number = (num: number): number => {
  return num * 3;
}

/** Function that halves the input number */
let halveNumber: (num: number) => number = (num: number): number => {
  return num * 0.5;
}

/** Function that squares the input number */
let squareNumber: (num: number) => number = (num: number): number => {
  return num * num;
}
```


</td>
</tr>
</table>

We now have many different functions that perform an operation on a specific input number! Despite it being messier and less readable, the functions above include their *type annotations*. If you notice, all of these functions have the same type annotation: `(num: number) => number`!

Recall the header from our `mapNumbers` function:

```ts
let mapNumbers = (nums: number[]): number[] => { ... }
```

The header for our function takes in *one* parameter currently - a list of numbers. We then perform operations with the inputted list of numbers. To specify this parameter, we just included a name and a *type annotation*.

If we wanted to pass in a *function* in here, how would we add this into our function header?

```ts
let mapNumbers = (nums: number[], transformFunction: (num: number) => number): number[] => { ... }
```

As you can see, this now would provide a new parameter called `transformFunction` of type `(num: number) => number` that will enable us to pass in a function with that type annotation! 

To make our lives easier and make our code a lot more concise, we can also create a [*type alias*](https://github.com/unc-csxl/orientation/blob/main/frontend/typescript_tutorial.md#type-aliases) for our function's type! That will make it easier to type and more readable. If you are not familiar with type annotations, check out the TypeScript Tutorial docs to learn more.
 
```ts
type NumberTransformer = (num: number) => number
```

Now, our new header for `mapNumbers` would look like so:

```ts
let mapNumbers = (nums: number[], transformerFunction: NumberTransformer): number[] => { ... }
```

Finally, let's implement our new `mapNumbers` function!

<table>
<tr><th width="800">Implement `mapNumbers` With Function Parameter</th></tr>
<tr>
<td>
 
```ts
/** Type alias for our number transformer functions */
type NumberTransformer = (num: number) => number

/** Function that modifies the input number */
let mapNumbers = (nums: number[], transformerFunction: NumberTransformer): number[] => {

 // Create an empty list of numbers
 let newNums: number[] = [];

  // Loop over all of the input numbers
  for(let num of nums) {
    // Modify the number
    // !! - We call the passed in function here!
    let newNum = transformerFunction(num);
    // Save the new number
    newNums.push(newNum);
  }

  // Return the final number
  return newNums;
}
```

</td>
</tr>
</table>

This is super useful! As you can see, we modified our function to use the passed in `transformerFunction` to actually transform each number in our array. Let's see our new `mapNumbers` function in action:

<table>
<tr><th width="520">Use the `mapNumbers` Function</th></tr>
<tr>
<td>
 
```ts
let numList: number[] = [0, 1, 4]

// Double the number
mapNumbers(numList, doubleNumber)
// Returns : [0, 2, 8]

// Triple the number
mapNumbers(numList, tripleNumber)
// Returns : [0, 3, 12]

// Halve the number
mapNumbers(numList, halveNumber)
// Returns : [0, 0.5, 2]

// Square the number
mapNumbers(numList, squareNumber)
// Returns : [0, 1, 16]
```

</td>
</tr>
</table>

The ability to pass functions into other functions is an extremely powerful feature of TypeScript that is commonly used and built-in to many TypeScript language features. We will explore these features in a second, optional reading.

## Returning Functions from other Functions

In the previous section, we explored passing functions into other functions as parameters. In this section, we are going to try one more thing: *returning functions from functions*. Remember that ultimately, functions just return *values*. Since the arrow function syntax allows us to represent functions as values, we can also use this **return functions from within functions!**

Let's continue to use the example we have been working with in the previous sections. We implemented two functions - `doubleNumber` and `tripleNumber`. What if, though, we wanted to multiply a number by 4? 5? any number?

Recall a nifty design pattern from COMP 301 - the *factory* design pattern. The factory design pattern allows us to create different versions of a class based on a certain parameter.

**What if we can create a function that *generates* different functions depending on what number we want to multiply by?**

That way, if we call our new function `generateMultiplyTransformerFunction`, we ultimately can do the following:

<table>
<tr><th width="520">The Goal</th></tr>
<tr>
<td>
 
```ts
let numList: number[] = [0, 1, 4]

// Generates a function that doubles a number
let doubleNumber: (num: number) => number = generateMultiplyTransformerFunction(2);

// Double the numbers
mapNumbers(numList, doubleNumber);
// Returns : [0, 2, 8]

// Generates a function that quadruples a number
let quadrupleNumber: (num: number) => number = generateMultiplyTransformerFunction(4);

// Quadruple the numbers
mapNumbers(numList, quadrupleNumber);
// Returns : [0, 4, 16]

```

</td>
</tr>
</table>

We know that our new function should *return* a function that is compatible with the parameter in `mapNumbers`, which should be a function that inputs a number and returns a number. So, the return type signature should be `(num: number) => number`.

From there, we also need an *input* to our generate function. This input is the *factor* by which we want to multiply.

Let's create the skeleton of our `generateMultiplyTransformerFunction` function!

<table>
<tr><th width="520">`generateMultiplyTransformerFunction` Header</th></tr>
<tr>
<td>
 
```ts

/** Generates a tranformer function that takes in a number and
returns the number multiplied by the factor. */
let generateMultiplyTransformerFunction = (factor: number): (num: number) => number => {
 
}

/* NOTE: I will not use the type alias in the next examples to get you a bit more familiar
* with the expanded syntax so you are able to recognize it if you see it. However, if it
* helps to understand the input and output, here would be the function header using
* the NumberTransformer alias created in this line: `type NumberTransformer = (num: number) => number`
*
* let generateMultiplyTransformerFunction = (factor: number): NumberTransformer => { ... }
*/

```

</td>
</tr>
</table>

Now, let's think about what we are actually trying to *return*. Let's think about what we would want as the *output* of this function given a few sample inputs:

<table>
<tr><th width="460">Function Call</th><th width="520">Expected Return Value</th></tr>
<tr>
<td>
 
```ts
generateMultiplyTransformerFunction(2);
```

</td>
 <td>

```ts
(num: number): number => {
 return num * 2;
}
```

</td>
</tr>
<tr>
 <td>
 
```ts
generateMultiplyTransformerFunction(5);
```

</td>
 <td>

```ts
(num: number): number => {
 return num * 5;
}
```

</td>
</tr>
<tr>
 <td>
 
```ts
generateMultiplyTransformerFunction(0.5);
```

</td>
 <td>

```ts
(num: number): number => {
 return num * 0.5;
}
```

</td>
</tr>
</table>

As you can see, there is a pattern emerging! Let's extrapolate such that we replace our input with an arbitrary `factor`:

<table>
<tr><th width="460">Function Call</th><th width="520">Expected Return Value</th></tr>
<tr>
<td>
 
```ts
generateMultiplyTransformerFunction(factor);
```

</td>
 <td>

```ts
(num: number): number => {
 return num * factor;
}
```

</td>
</tr>
</table>

We have just found *what we want our function to return!* Let's finish implementing the `generateMultiplyTransformerFunction` function.

<table>
<tr><th width="520">`generateMultiplyTransformerFunction` Implementation</th></tr>
<tr>
<td>
 
```ts
/** Generates a transformer function that takes in a number and
returns the number multiplied by the factor. */
let generateMultiplyTransformerFunction = (factor: number): (num: number) => number => {

 // Return a transformer function that takes in a number and returns the number * factor
 return (num: number): number => {
  return num * factor;
 }
}
```

</td>
</tr>
</table>

As you can see, this might be a bit confusing at first! Essentially though, our `generateMultiplyTransformerFunction` just returns another function for us to use elsewhere.

Ultimately though, there are some pretty cool use cases for functions being able to generate other functions. While the syntax is a bit messy, using some TypeScript language features such as *type aliases* may help to make it easier to understand.

## Conclusion

Congratulations! ✨ Throughout this reading, you have learned how to use *functions as values*. Doing so has enabled us to use functions both ***as parameters*** in other functions, as well as ***return values*** of other functions. What you have learned to implement here are *higher order functions*.

**Higher order functions** are functions that either take in other functions are parameters, or return a function as their result. Higher order functions enable us to program more in a *funtional programming style* by allowing us to abstract functionality into higher order functions, and to use higher order functions to generate functionality based on certain parameters.

TypeScript uses higher order functions throughout its language features, and higher order functions are used a lot throughout the CSXL web application's codebase. Being able to trace code with higher order functions is quite challenging at first. One of the best ways to practice using higher order functions is to play around with them and create your own examples! Just like in the previous tutorial, we highly recommend you go to the official [TypeScript playground](https://www.typescriptlang.org) or open a new [Repl.it](https://replit.com) and play around with creating and using higher order functions.

In addition, below are some additional resources that you may find useful:

## Extra Resources

* [Learn JS: Iterators and Higher Order Functions](https://www.codecademy.com/learn/game-dev-learn-javascript-higher-order-functions-and-iterators/modules/game-dev-learn-javascript-iterators/cheatsheet)

