# Prototypal Inheritance in Object-Oriented Javascript

## What does that mean?

All we're talking about is how JavaScript allows us to
share code among objects.

## Why is that important?

By taking advantage of JavaScript's prototypal inheritance,
we can write less code that is better-organized and more maintainable
than non-object-oriented JavaScript. It also conserves memory.

## Learning Objectives
- Understand how *prototypal inheritance* gives programmers additional
flexibility.
- Understand how to use namespaces to organize application code.
- Understand how to use a custom constructor method to set one or more
properties on a new object.

## Overview
1. Review of Objects
2. Intro to Classes in JS
3. Classes in ES6
4. Inheritance

'what are the advantages of OOJS -- i.e. organizing the namespace
Adding methods on the prototypes of objects in JavaScript is an efficient way to conserve memory (as opposed to copying the methods on each object).
classes are really just ways to create new objects
Class Inheritance: A class is like a blueprint — a description of the object to be created. Classes inherit from classes and create subclass relationships: hierarchical class taxonomies.
Inheritance is fundamentally a code reuse mechanism: A way for different kinds of objects to share code. The way that you share code matters because if you get it wrong, it can create a lot of problems, specifically:
If you were taught to build classes or constructor functions and inherit from those, what you were taught was not prototypal inheritance. You were taught how to mimic class inheritance using prototypes. See “Common Misconceptions About Inheritance in JavaScript”.
In JavaScript, class inheritance piggybacks on top of the very rich, flexible prototypal inheritance features built into the language a long time ago, but when you use class inheritance — even the ES6+ `class` inheritance built on top of prototypes, you’re not using the full power & flexibility of prototypal OO. In fact, you’re painting yourself into corners and opting into all of the class inheritance problems.
in javascript we achieve inheritance through prototypes
## Intro

### 1. Review of Objects in JS (3 minutes)

The important thing to remember about objects is that they encapsulate related data and behavior into an organized structure. We saw this when we discussed **object literal notation**. Recall that we can define an object like this:

```js
let car = {
  make: "Honda",
  model: "Civic",
  color: "red",
  drive: function(){
    console.log("vroom vroom")
  },
  gps: function(location){
    console.log(`Beep boop, driving to ${location}`)
  },
  paint: function( newColor ){
    console.log(`Your car has been painted ${newColor}`)
    this.color = newColor
  }
}
```
**But what if we want a faster, more efficient way to build JS objects?**

### 2. Intro to classes in ES6 (3 minutes)

# Vocabulary we'll need to know:

**Class** - An object that models real world things in our application

**Instance** - An object defined by our class

**Constructor** - The function that defines instances of our class. We pass the
constructor values that will define properties on our class instance.

**Inheritance** - The passing down of properties from a parent class to a subclass.
By calling the **super** method, we

With ES6, JavaScript introduced the `class` keyword that we use (along with a capitalized class name)
to create a class. While the syntax is intended to mimic the class syntax in languages such as
Java, ES6 classes continue to rely on prototypal inheritance under the hood.

Prototypal inheritance means that certain functionality and information can be accessed
through an object's prototype. for one object, use another object as a backup -- go look in the prototype.

```js

  class Car {
    constructor(make, model, color) {
      this.make = make
      this.model = model
      this.color = color
    }

    drive() {
      console.log('vroom vroom')
    }

    gps( location ) {
      console.log(`beep beep, driving to ${location}`)
    }

    paint( newColor ) {
      this.color = newColor
    }
  }
```

<details>
  <summary>This was the ES5 syntax</summary>

  ```js
  function Car(make, model, color) {
    this.make = make;
    this.model = model;
    this.color = color;
    this.drive = () => console.log('vroom vroom');
    this.gps = location => console.log(`driving to ${location}`);
    this.paint = newColor => (this.color = newColor);
  }
  ```
</details>

### 4. Inheritance (5 minutes)

- Often we'll need to take our class and expand on it.Think about types of Cars, for instance.
For this case, we create sub-classes through a process called Inheritance.

In ES6, we extend an existing class with the `extend` keyword. This will let us create a subclass:

```js
class Car {
  constructor(make, color) {
    this.make = make
    this.color = color
  }
}

class Toyota extends Car {
  drive() {
    console.log('vroom vroom')
  }
}
```

If we have properties that we want to add to our subclass, we still need to take in the properties for our parent class, and pass them up to our parent class with `super`. Super calls the
constructor function on the parent class.

```js
class Car {
  constructor(model, color) {
    this.model = model
    this.color = color
  }
  drive() {
    console.log('vroom vroom')
  }
}

class Toyota extends Car {
  constructor(model, color) {
    super(model, color)
    this.make = 'Toyota'
  }
}
```

## Closing / Questions (10 minutes / 2:00)

* What are the benefits to using an OOP approach to programming?
* What is a class? What is `new`? How are they related?
* What does it mean to use "inheritance" when working with classes?
* How do we indicate that one class inherits from another?
* What does `super` mean?
