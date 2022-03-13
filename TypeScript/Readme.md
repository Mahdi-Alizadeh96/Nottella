# Intro

<img src="https://upload.wikimedia.org/wikipedia/commons/4/4c/Typescript_logo_2020.svg" width="200" style="text-align:center; display:flex; margin: auto; margin-bottom: 2rem">


**TypeScript is a strongly typed programming language that builds on JavaScript, giving you better tooling at any scale.**

Source : [(*www.typescriptlang.org*)](www.typescriptlang.org)
## What is JavaScript ? A Brief History

JavaScript (also known as ECMAScript) started its life as a simple scripting language for browsers. At the time it was invented, it was expected to be used for short snippets of code embedded in a web page — writing more than a few dozen lines of code would have been somewhat unusual. Due to this, early web browsers executed such code pretty slowly. Over time, though, JS became more and more popular, and web developers started using it to create interactive experiences.

> "JavaScript has problems. If you work with it long enough, you will run into these and you'll need to find a way to deal with them. TypeScript solves most of these problems out of the box for you. So it can be a good fit for those coming from another language, not interested in learning JavaScript deeply." - Library Author

#### JavaScript’s equality operator (==) coerces its arguments, leading to unexpected behavior:

```js
if ("" == 0) {
  // It is! But why??
}
if (1 < x < 3) {
  // True for *any* value of x!
}
```

---

## TypeScript: A Static Type Checker

We said earlier that some languages wouldn’t allow those buggy programs to run at all. Detecting errors in code without running it is referred to as static checking. Determining what’s an error and what’s not based on the kinds of values being operated on is known as static type checking.

TypeScript checks a program for errors before execution, and does so based on the kinds of values, it’s a static type checker. For example, the last example above has an error because of the type of obj. Here’s the error TypeScript found:

```ts
const obj = { width: 10, height: 15 };
const area = obj.width * obj.heigth;
//Property 'heigth' does not exist on type '{ width: number; height: number; }'. Did you mean 'height'?
```
---
## A Typed Superset of JavaScript

TypeScript is a language that is a **superset** of JavaScript: JS syntax is therefore legal TS. Syntax refers to the way we write text to form a program.

This syntactically-legal program logs Infinity. TypeScript, though, considers division of number by an array to be a nonsensical operation, and will issue an error:

```ts
console.log(4 / []); //error
//The right-hand side of an arithmetic operation must be of type 'any', /'number', 'bigint' or an enum type.
```
---
## Runtime Behavior

TypeScript is also a programming language that preserves the runtime behavior of JavaScript. For example, dividing by zero in JavaScript produces **Infinity** instead of throwing a runtime exception. As a principle, TypeScript never changes the runtime behavior of JavaScript code.

This means that if you move code from JavaScript to TypeScript, it is guaranteed to run the same way, even if TypeScript thinks that the code has type errors.

---
## Defining Types

You can use a wide variety of design patterns in JavaScript. However, some design patterns make it difficult for types to be inferred automatically (for example, patterns that use dynamic programming). To cover these cases, TypeScript supports an extension of the JavaScript language, which offers places for you to tell TypeScript what the types should be.

For example, to create an object with an inferred type which includes name: string and id: number, you can write:

```ts
const user = {
  name: "Hayes",
  id: 0,
};
```
You can explicitly describe this object’s shape using an interface declaration:

```ts
interface User {
  name: string;
  id: number;
}
```

Since JavaScript supports classes and object-oriented programming, so does TypeScript. You can use an interface declaration with classes:

```ts
interface User {
  name: string;
  id: number;
}
 
class UserAccount {
  name: string;
  id: number;
 
  constructor(name: string, id: number) {
    this.name = name;
    this.id = id;
  }
}
 
const user: User = new UserAccount("Murphy", 1);
```

---

## Composing Types

With TypeScript, you can create complex types by combining simple ones. There are two popular ways to do so: with unions, and with generics.

### Unions
With a union, you can declare that a type could be one of many types.

```ts
type MyBool = true | false;
type WindowStates = "open" | "closed" | "minimized";
type LockStates = "locked" | "unlocked";
type PositiveOddNumbersUnderTen = 1 | 3 | 5 | 7 | 9;
```

Unions provide a way to handle different types too. For example, you may have a function that takes an array or a string:

```ts
function getLength(obj: string | string[]) {
  return obj.length;
}
```

### Generics

Generics provide variables to types. A common example is an array. An array without generics could contain anything. An array with generics can describe the values that the array contains.

```ts
type StringArray = Array<string>;
type NumberArray = Array<number>;
type ObjectWithNameArray = Array<{ name: string }>;
```



