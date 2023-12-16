# Introduction to Higher Order Functions

> Written by Ajay Gandecha for the CSXL Web Application and for COMP 423: Foundations of Software Engineering.<br>
> *Last Updated: 12/16/2023*

## Preface

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




-----------

```ts
function doubleNumber(num: number): number {
  return num * 2;
}
```
```ts
let doubleNumber = (num: number): number => {
  return num * 2;
}
```

```ts
let name = value;

So:
```

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


-----

## Functions as Values


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
