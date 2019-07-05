# Introduction to TypeScript

## Key

👉 Instruction  
❔ Question  
🏃 Exercise  
🏆 Tough challenge  
📄 Information  
💬 Tip  
🔗 Link to useful information

## Introduction

📄 TypeScript is a superset of JavaScript and needs to be transpiled in order to run in a browser. TypeScripts main purpose is to add a rich type system to JavaScript.

👉 [Open the TypeScript Playground](https://www.typescriptlang.org/play/)

## Primitive types

❔ Does JavaScript have types? 

❔ What JavaScript operator can we use to find the type of a variable?  

🏃 Find out the type of the `today` variable in the following code:
```
const today = new Date();
``` 

❔ What are the primitive types available in JavaScript?

🔗 JavaScript primitive types: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures

## Type annotations

📄 A type annotation lets us declare a variable with a specific type. This allows the TypeScript compiler to check that code references to that variable adheres to that type.

📄 A type annotation is placed after a variable declaration using a colon and then the type.

🏃 Create a numeric variable called `score` and set this to `9`.  
🏃 Instead of `9`, try to set this to `"9"` - what happens?

❔ Are the type annotations included in the transiled code?

## Type inference

📄 TypeScript's type inference system means we don't always have to enter a type annotation for the TypeScript compiler to know a variables type.

💬 Let TypeScript infer types where it can to avoid bloating code with unnecessary type information.

🏃 Create a numeric variable called `score` and set this to `9` without using a type annotation. Hover over the variable to confirm that it is of type `number`.

🏃 Create a revised implementation of the function below without the unnecessary type annotations but still maintaining the same level of strong typing.

```
function sum(num1: number, num2: number): number {
    const total: number = num1 + num2;
    return total;
}
```

## The `any` type

❔ What is the type of the `value` parameter in the function below? 
```
function add10(value) {
    return value + 10;
}
```

❔ What situations is `any` useful?

💬 There is a TypeScript type called `unknown` that can be used to strongly-type variables that have unknown types at runtime.  
🔗 Information on the `unknown` type. https://mariusschulz.com/blog/typescript-3-0-the-unknown-type


## Arrays

📄 Square brackets can be added to a type annotation to denote that it is an array type.

🏃 Create a strongly-typed function that takes in an array of numbers and returns the result of adding all of them together.


🔗 Basic types in TypeScript docs. https://www.typescriptlang.org/docs/handbook/basic-types.html

## Interfaces

📄 An interface allows us to create strongly-typed objects. It allows all the object property types to be defined as well as method signature typing.  
e.g.
```
interface Person {
  firstname: string;
  surname: string;
  sayHello: () => string;
}
const bob:Person = {
  firstname: "Bob",
  surname: "Jones",
  sayHello() {
      return `hello ${this.firstname}`
  }
}
```

❔ What would `typeof bob` return at run time for the above example? Does it return `Person`? If not why not?

🏃 Create a strongly-typed function called `getHighestScore` that takes in an array of objects containing a name and a score. Return the maximum score with the associated persons name. Example data that could be processed by this function is as follows:
```
[{name: "Fred", score: 9}, {name: "Bob", score: 7}, {name: "Gemma", score: 10}]
```

🏃 Create an interface `ILogger` that contains a method called `log` which takes a `string` message to log. The `log` method should return the `void` type because no data is returned.

🏃 Create a class that implements the `ILogger` interface that outputs the message to the console.

🔗 Interfaces in TypeScript docs. https://www.typescriptlang.org/docs/handbook/interfaces.html

## Optional properties and parameters

📄 Function parameters and interface parameters can be declared as optional by using a `?` before the type annotation.

🏃 Adjust the `getHighestScore` function so that the score is optional and defaults to `0`.

## Type aliases

📄 A type alias creates a new name for a type. To define a type alias, we use the type keyword, followed by the alias name, followed by the type that we want to alias.

e.g. 
```
type Numbers = number[];
const someNumbers: Numbers = [1, 2, 3];
```

❔ Can a type alias be used instead of an interface for the following type?  
🏃 If so, do it!
```
interface Person {
  firstname: string;
  surname: string;
}
```

🔗Interfaces v Type aliases https://pawelgrzybek.com/typescript-interface-vs-type/

## Union type

📄 Union types are types that we can combine together to form a new type. The types in the union are separated by `|` (pipe).

🏃 Create a `grade` variable that can have values `A`, `B` or `C`  
🏃 Create a union type called `Grade` so that we can reuse this type in other areas of our code

🏆 Create a function called `logIt` which takes in a person or company and outputs their name to the console. The types for the person and company are below:
```
interface Person {
  firstname: string;
  surname: string;
}
interface Company {
  name: string;
}
```

🔗 Union types in TypeScript docs. https://www.typescriptlang.org/docs/handbook/advanced-types.html#union-types

## Generics

📄 Generics is a mechanism for allowing the
type parameters to be passed into functions or classes. This allows the internal implementation of the function or class to work with varied types.

📄 The type is passed into the function using angle brackets before the function parameters. In the function definition, the generic type that was passed in is referenced rather than a specific type. Typically a function parameter or the return value will be given the generic type.

```
function someFunction1<T>( someParam: T ) {
  ...
}

function someFunction2<T>(): T {
  ...
}

interface Person { ... } 

const person1:Person = { ... };
someFunction1<Person>(person1);

const person2 = someFunction2<Person>()
```

📄 The type is passed into a class using angle brackets after the class name:

```
class SomeClass<T> {
}
```

📄 Multiple types can be passed into a function or class using a comma delimited list of types in the angle brackets
```
<T1,T2,..>
``` 

🏆 Create a list class that has a generic parameter for the type of the list items. The class needs to have a `add` method to add an item and a `getNth` method to return the nth item in the list.

## Closing questions

❔ Are TypeScript types available at runtime to inspect?

❔ Are there any features in JavaScript that are not in TypeScript?

❔ What are the benefits of coding in TypeScript rather than JavaScript?


