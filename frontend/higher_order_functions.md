# Introduction to Higher Order Functions

> Written by Ajay Gandecha for the CSXL Web Application and for COMP 423: Foundations of Software Engineering.<br>
> *Last Updated: 12/16/2023*

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
let name: name = value;
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

In TypeScript, we can use the arrow syntax we learned to create ***function literals***. Function literals are how we can store functions as values. They define the three basic parts of a function - the *inputs (parameters)* that the function should take in, and the body of the function that ultimately performs some sort of action and returns an *output*.

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

As you can see, this literal takes in a number and returns a number - just as shown in the arrow function syntax! However, *we cannot call it* because it does not have a name! This is the same if you just typed `14` in your TypeScript file. That value is *never stored or accessible if we do not save it as a variable.*

<table>
<tr><th width="520">Values</th></tr>
<tr>
<td>
 
```ts
14
// ... this does nothing! We can never access this.

let myNumber = 14;
// Better! We can now use this number elsewhere.

(num: number): number => {
 return num * 2;
}
// ... this does nothing! We can never access this.

let doubleNumber = (num: number): number => {
  return num * 2;
}
// Better! We can now use this function elsewhere.
```

</td>
</tr>
</table>

Hopefully, you are able to see how we can *use functions as values* to assign to a variable!

Lastly, remember that values always have a certain *data type* associated with them. Recall the able above - the `course` variable is of type `number`, the `name` variable is of type `string`, and the `yoda` variable is of type `Jedi`. So, *what type is `doubleNumber`?

The type annotations for function literals *are based on their inputs and output*. The type annotation has the following formula:

`(param: type, param2: type, ...) => returnType`

So in this case, the type annotation for `doubleNumber` would be **`(num: number) => number`**!

Just like with normal TypeScript variables, we can also apply type annotations to our arrow function, like so:

<table>
<tr><th width="520">Arrow Function</th></tr>
<tr>
<td>
 
```ts
/** Function that doubles the input number */
let doubleNumber = (num: number): number {
  return num * 2;
}

// OR

/** Function that doubles the input number */
let doubleNumber: (num: number) => number = (num: number): number {
  return num * 2;
}
```

</td>
</tr>
</table>

Understanding the *typings* of functions and how to pass functions as values is ***extremely useful***. Let's explore some use cases for passing functions around as values!


## Passing Functions as Parameters

Let's take a look at the following example. Say that I have an *array of `number`s*. I want to create a function to *modify these numbers* so that I *call the `doubleNumber` function on every single one of them!

So, if I were to have the following input:

`[0, 2, 4, 8]`

I expect the following output:

`[0, 4, 8, 16]`

Using what you learned from the TypeScript tutorial, we can create this function by utilizing some array functionality. Let's create this function as an arrow function and call it `modifyNumbers()`. This function will take in an array of numbers (`numbers[]`) and return an array of numbers as well.

Feel free to try to implement this on your own as practice first, or look at the code below:

<table>
<tr><th width="520">Implement `modifyNumbers`</th></tr>
<tr>
<td>
 
```ts
/** Function that doubles the input number */
let modifyNumbers = (nums: number[]): number[] => {

 // Create an empty list of numbers
 let newNums: number[] = [];

  // Loop over all of the input numbers
  for(let num of nums) {
    // Modify the number
    let newNum = doubleNumber(num);
    // Save the new number
    newNums.append(newNum);
  }

  // Return the final number
  return newNums;
}
```

</td>
</tr>
</table>

We can now easily pass in an array of numbers, and it should return an array of numbers with all of its numbers doubled.

However, ***what if we want to make `modifyNumbers` more multipurpose?*** *What if we wanted to have `modifyNumbers` also be able to triple a number? Halve a number? Square the number?*

We *could* rewrite the `modifyNumbers` function every single time, except that seems incredibly inefficient. *What if there was a way to pass in which function we wanted to modify each number with into the `modifyNumbers` function?* So for example, I could pass in `doubleNumber` if I wanted my function to double the numbers, or pass in `squareNumber` if I wanted to square each number.

Well, ***we can!*** Since *functions can be used as values, we can use them as **function parameters** too!*

Recall how we implemented the `doubleNumber` function again. We could easily implement a few more functions like `doubleNumber` that would perform these other operations for us.

<table>
<tr><th width="520">Number Modifier Functions</th></tr>
<tr>
<td>
 
```ts
/** Function that doubles the input number */
let doubleNumber: (num: number) => number = (num: number): number {
  return num * 2;
}

/** Function that triples the input number */
let tripleNumber: (num: number) => number = (num: number): number {
  return num * 3;
}

/** Function that halves the input number */
let halveNumber: (num: number) => number = (num: number): number {
  return num * 0.5;
}

/** Function that squares the input number */
let squareNumber: (num: number) => number = (num: number): number {
  return num * num;
}
```


</td>
</tr>
</table>

We now have many different functions that perform an operation on a specific input number! Despite it being messier and less readable, the functions above include their *type annotations*. If you notice, all of these functions have the same type annotation: `(num: number) => number`!

Recall the header from our `modifyNumbers` function:

```ts
let modifyNumbers = (nums: number[]): number[] => { ... }`
```

The header for our function takes in *one* parameter currently - a list of numbers. We then perform operations with the inputted list of numbers. To specify this parameter, we just included a name and a *type annotation*.

If we wanted to pass in a *function* in here, how would we add this into our function header?

```ts
let modifyNumbers = (nums: number[], modifierFunction: (num: number) => number): number[] => { ... }
```

As you can see, this now would provide a new parameter called `modifierFunction` of type `(num: number) => number` that will enable us to pass in a function with that type annotation! 

To make our lives easier and make our code a lot more concise, we can also create a [*type alias*](https://github.com/unc-csxl/orientation/blob/main/frontend/typescript_tutorial.md#type-aliases) for our function's type! That will make it easier to type and more readable. If you are not familiar with type annotations, check out the TypeScript Tutorial docs to learn more.
 
```ts
type NumberModifier = (number: number): number
```

Now, our new header for `modifyNumbers` would look like so:

```ts
let modifyNumbers = (nums: number[], modifierFunction: NumberModifier): number[] => { ... }
```

Finally, let's implement our new `modifyNumbers` function!

<table>
<tr><th width="800">Implement `modifyNumbers` With Function Parameter</th></tr>
<tr>
<td>
 
```ts
/** Type alias for our number modifier functions */
type NumberModifier = (number: number): number

/** Function that modifies the input number */
let modifyNumbers = (nums: number[], modifierFunction: NumberModifier): number[] => {

 // Create an empty list of numbers
 let newNums: number[] = [];

  // Loop over all of the input numbers
  for(let num of nums) {
    // Modify the number
    // !! - We call the passed in function here!
    let newNum = modifierFunction(num);
    // Save the new number
    newNums.append(newNum);
  }

  // Return the final number
  return newNums;
}
```

</td>
</tr>
</table>

This is super useful! Let's see our new `modifierFunction` in action:

<table>
<tr><th width="520">Use the `modifierFunction` Function</th></tr>
<tr>
<td>
 
```ts
let numList: number[] = [0, 1, 4]

// Double the number
modifyNumbers(numList, doubleNumber);
// Returns : [0, 2, 8]

// Triple the number
modifyNumbers(numList, tripleNumber);
// Returns : [0, 3, 12]

// Halve the number
modifyNumbers(numList, halveNumber);
// Returns : [0, 1, 4]

// Square the number
modifyNumbers(numList, squareNumber);
// Returns : [0, 1, 16]
```

</td>
</tr>
</table>

