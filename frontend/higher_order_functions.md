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

```ts
(number: number): number
```

```ts
type NumberModifier = (number: number): number
```

```ts

let doubleNumber = (num: number) => {
  return num * 2;
}


let modifyNumbers = (nums: number[]): number[] => {

  let newNums: number[] = [];

  for(let num of nums) {
    let newNum = doubleNumber(num);
    newNums.append(newNum);
  }

  return newNums;
}

```
