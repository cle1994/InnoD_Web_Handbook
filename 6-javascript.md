*ES6 stuff to come!*

# Javascript (JS)

If you can only read one thing in this section, please read the DOM section.
It's the most relevant for web developers.

**Quick Jump**

* [Javascript as a Language](6-javascript.md#language)
  * [Typing](6-javascript.md#language-type)
  * [Objects](6-javascript.md#language-objects)
  * [Arrays](6-javascript.md#language-arrays)
  * [Functions](6-javascript.md#language-functions)
  * [Coercion](6-javascript.md#language-coercion)
  * [True/False (Booleans)](6-javascript.md#language-booleans)
  * [Equality](6-javascript.md#language-equality)
* [Scope](6-javascript.md#scope)
* [`this`](6-javascript.md#this)
* [DOM](6-javascript.md#dom)

# Introduction to JavaScript
===================================
Shamelessly copied and modified parts before scope from "You Don't Know JS" by
getify. Modified and simplified for Web Tier because there's just so much.
But when you get the chance read through his books, I wish I had this when
I started out.

[You Don't Know JS](https://github.com/getify/You-Dont-Know-JS)

Javascript is much like any other programming language. It's quite an abstract,
high level language. It's untyped, dynamic, and interpreted, kind of like
Python. It's the quintessential programming language of the web.

While you're first starting out, Javascript will mostly be used so that
you can manipulate DOM elements. We'll go over how jQuery can make this
a lot easier for you later, but you should understand how jQuery does it
and how to use plain Javascript with frameworks or libraries (it comes
up a lot if you ever interview for a web engineer position).

In general, it's good to know Javascript fairly well because you can use
it to build simple backends or APIs to talk to those backends using Node.js.
This is another conversation though.

<a name="language"></a>
# JavaScript as a language

<a name="language-type"></a>
## Values & Types
JavaScript has typed values, not typed variables.

This is what it means to have typed values but not typed variables...
```javascript
var a;
typeof a;               // "undefined"

a = "hello world";
typeof a;               // "string"

a = 10;
typeof a;               // "number"

a = true;
typeof a;               // "boolean"

a = null;
typeof a;               // "object" (weird right?)

a = undefined;
typeof a;               // "undefined"

a = { hello: "world" };
typeof a;               // "object"
```
*Note that typeof returns a string of the type*

<a name="language-objects"></a>
## Objects
Learn to love them because that's pretty much all Javascript is...
They kind of work like dictionaries.

```javascript
var myObj = {
  hello: 'world',
  dog: 1,
  js: true
};

myObj.hello;            // 'world'
myObj.dog;              // 1
myObj['js'];            // true

var cat = 'dog';
myObj[cat];             // 1
```

<a name="language-arrays"></a>
## Arrays
Like most languages.

```javascript
var arr = [
  'dog',
  'cat',
  'penguin',
  'cow'
];

arr[0];                 // 'dog'
```

Not much to see here...

<a name="language-functions"></a>
## Functions
Lookie your friend the object is back. Functions are a subtype of
objects in Javascript.

```javascript
function hello(world) {
    return world;
};

hello.bye = 'sadness';

typeof hello;           // 'function'
typeof hello();         // 'undefined'
typeof hello.bye;       // 'string'
```

<a name="language-coercion"></a>
## Coercion
```javascript
// Explicit
var a = '10';
var b = Number(a);

a;                      // '10'
b;                      // 10

// Implicit
var c = a * 1;
c;                      // 10
```

<a name="language-booleans"></a>
## True/False
These are false
- ""
- 0, -0, NaN
- null, undefined
- false

Everything else is true

<a name="language-equality"></a>
## Equality
```javascript
var a = "42";
var b = 42;

a == b;
a === b;
```

What's the difference?

```javascript
var a = [1,2,3];
var b = [1,2,3];
var c = "1,2,3";

a == b;                 // false
a == c;                 // true (LOL wtf right)
```

<a name="scope"></a>
# Scope
## Lifetime of a variable

Maps a name to a value in a given environment

```javascript
function add(x, y) {
  var sum = x + y;
  if (true) {
    var sum = 42;
  }
  return sum;       // 42
};
```

It's the job scope -- and scope resolution -- to pick which sum to return.

```c
printf("web");
if (true) {
  int i = 0;
  for (i; i < 5; i += 1) {
    int forty_two = 42;
  }
}
```

```javascript
console.log("web");
if (true) {
  var i = 0;
  for (i; i < 5; i += 1) {
    var forty_two = 42;
  }
}
```

In C, and other languages, scope is established by blocks: curly braces.
Scope1: Entire block
Scope2: If statement
Scope3: For loop

Javascript does not do this. There's only 1 scope here. You can't create
scopes with blocks.

Javascript is functionally scoped. Whenever you are in a function, you have
that functions scope, your private scope. Because the only way to create
private scope is to be inside a function, you sometimes have to
create functions on the fly. One way is to use self-invocation.

*Scope is a bit different with arrow functions found in ES6 (ECMAScript 6)
standards. We'll go into it later*

```javascript
(function() {
  // Stuff in here is ran the moment it's encountered
  // On demand private scope
})();
```

Pretty much, this function is executed immediately by the interpreter when
it's seen.

## Scope Game
```javascript
var a = "Fear cuts deeper than swords.";
if (true) {
  var a = "Any man who must say, I am the king, is no true king."
}
console.log(a);
```

```javascript
// "Any man who must say, I am the king, is no true king."
```

```javascript
var a = "Fear cuts deeper than swords.";
(function() {
  var b = "Any man who must say, I am the king, is no true king."
})();
console.log(b);
```

```javascript
// Error: b not defined
```

```javascript
var name = "Bob";
function printName(name) {
  console.log(name);
}
printName("Joe");
```

```javascript
// "Joe"
```

Demonstrates innermost precedence. Javascript will give precedence over
variables defined closer to the call-site or it's most immediate scope.

## Easy right? Meet Global Scope...
#### This shit is dumb... (my opinion)

```javascript
var a = "Fear cuts deeper than swords.";
(function() {
    b = "Any man who must say, I am the king, is no true king."
})();
console.log(b);
```

Can you guess what is logged?
```javascript
// Error: b not defined
```

Yea you wish no... This is what's logged;
```javascript
// "Any man who must say, I am the king, is no true king."
```

This is because we neglected the keyword var. Javascript then hoists the
variable `b` up to the global scope: the window object if you're in a browser.

My recommendation, please don't use global scope. It's just super confusing and
bad practice. If you want to check if you write code that accidentally writes to
the global scope, you can use:

```javascript
// For browsers only
Object.keys(window);
```

<a name="this"></a>
# 'this' Keyword
## It's like magic, not really...

#### Lexical Scoping
If we look at the code, we know what variables are and what their values are.
But you can define variables that don't depend on text in code or a program.

meet...

#### Dynamic Scoping and Context
Context, in Javascript, uses dynamic scoping.

If a you think of a function as a sentence, then context is like the subject,
the who or what the sentence/function is about. To get to any functions
context you use 'this'.

#### So why 'this' and why is it so 'hard'?
1. Because we are so used to lexical scoping
2. And because of dynamic scoping

There's 4 (I think) ways to set the value of `this`.
1. If you call a method on an object, then `this` is the object.
```javascript
var person = {
  name: "Doe",
  logName: function() {
    console.log(this.name);
  }
};

person.logName();     // Logs "doe"
```

2. Use `.call()` or `.bind()` which allows you to pass in `this`.
```javascript
var person = {
  name: "Doe",
  logName: function(shouldLog) {
    if (shouldLog) {
      console.log(this.name);
    }
  }
};

person.logName.call({ name: "John" }, true);      // Logs "John"
```

```javascript
var person = {
  name: "Doe",
  logName: function(shouldLog) {
    if (shouldLog) {
      console.log(this.name);
    }
  }
};

person.logName.apply({ name: "John" }, [true]);       // Logs "John"
```

3. Using `.bind()`
```javascript
var logName = function(name) {
  if (name === this.name) {
    console.log(this.name);
  } else {
    console.log("Cow");
  }
};

var joe = {
  name: 'Joe'
};

var boundName = logName.bind(joe);

boundName('Joe');     // Logs "Joe"
```

4. Use the `new` keyword
```javascript
function person(name) {
  this.name = name;
};
var christian = new Person("Christian");
```

`new` will actually return the `this` value for that object back to you.

#### Context Game
```javascript
// In a browser
(function() {
  console.log(this);
})();
```

```javascript
// Global object
// In browser: window
```

```javascript
var colors = ["green", "blue", "pink"];
(function() {
  console.log(this);
}).call(colors);
```

```javascript
// colors
```

```javascript
var user = {
  print: function() {
    console.log(this);
  }
};
user.print();
```

```javascript
// Object {print: function}
```

<a name="dom"></a>
# DOM/DOM trees/Dom Manipulation
