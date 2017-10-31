# Prototypal Inheritance in Object-Oriented Javascript

## Learning Objectives
- Demonstrate a use case that explains prototypal inheritance and
what kind of flexibility it gives to programmers
- Use namespaces to organize application code
- Define a custom constructor method that sets one or more
properties of a new object

## Overview
1. Review of Objects
2. Intro to Classes in JS
3. Classes in ES6
4. Inheritance

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

### 2. Intro to classes in ES6 (3 minutes)

# Vocabulary:

**Class** - An object that models real world things in our application

**Instance** - An object defined by our class

**Constructor** - The function that defines instances of our class


### 3. Classes in ES5 vs. Classes in ES6 (5 minutes)
Classes were introduced in ES5, and were instantiated with the following syntax:

```js
function Car (make, model, color) {
  this.make = make;
  this.model = model;
  this.color = color;
  this.drive = function () {
    console.log('vroom vroom')
  }
}
```
With ES6, the language was updated to bring the syntax more inline with how other popular programming languages handle OOP. This includes the introduction of the `class` keyword. Nothing changed under the hood, just what we type to create a class.

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
}

class Toyota extends Car {
  constructor(model, color) {
    super(model, color)
    this.make = 'Toyota'
  }
  drive() {
    console.log('vroom vroom')
  }
}
```

## Closing / Questions (10 minutes / 2:00)

* What are the benefits to using an OOP approach to programming?
* What is a class? What is `new`? How are they related?
* What does it mean to use "inheritance" when working with classes?
* How do we indicate that one class inherits from another?
* What does `super` mean?
