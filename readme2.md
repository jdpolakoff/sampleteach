# Prototypal Inheritance in Object-Oriented Javascript

## What does that mean?

All we're talking about is how JavaScript allows us to share code among objects.
That's it. It's a simple concept with a fancy name.

## Why is prototypal inheritance important?

1) It allow us to write less code -- remember the DRY (Don't Repeat Yourself) principle.
2) It allows us to write code that is better-organized and more maintainable for other developers.
This will be especially important when you're working on large projects with other developers.

## Learning Objectives
- Understand how prototypal inheritance gives programmers additional flexibility.
- Understand how to use namespaces to organize application code.
- Understand how to use a custom constructor method to set one or more properties on a new object.

## Overview
1. Review of Objects
2. Intro to Classes in JS
3. Classes in ES6
4. Inheritance

### 1. Review of Objects in JS (2 minutes)

**Objects encapsulate related data and behavior into an organized structure.**

We can define an object using **object literal notation**, like this:

```js
let car = {
  make: "Honda",
  model: "Civic",
  color: "red",
  drive: function(){
    console.log("vroom vroom")
  }
}
```
We're doing two really important things here:

  1. We're encapsulating all data and behavior for a car inside a single object (i.e. a single place)
  2. We're modeling some real world thing inside our code

The second point is the basis of Object-Oriented Programming and what makes it so powerful.

Why might we want to model real world things in our code?

__Example: lets say we're building an app for a car rental company (Rent-a-Car). If they buy a new car to rent out to customers, they'll want to manage that new car inside the app we're building for them. Do we want to create a new object like the one above for each car new car?__

Before we get deeper in to OOP in JS there are a few loose ends we need to tie up:

<details>
    <summary>1. What is context?</summary>

    A reference (through `this`) to the object that owns the currently executing code.
</details>
<details>
    <summary>2. What is scope?</summary>

    Where variables are accessible during function invocation.
</details>
<details>
    <summary>3. What `type` is a function?</summary>

    Well it's a function, but a function is a type of object!
</details>
<details>
    <summary>4. Do functions have context?</summary>

    They do!
</details>

### 2. Intro to classes in ES6 (3 minutes)

**What is a class?**

A class is an object we can use to help us create new objects. Classes pass down data and functionality to other objects. In other words, they are prototypes. (More on that in a minute).

Let's take a look at an ES6 class.

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
  <summary>How is the class syntax different from our object literal syntax?</summary>


  1) The capitalized variable name.

  2) The constructor method. This method is called when a new instance of the class is instantiated.

  3) Also, notice the use of ```this```. We'll discuss ```this``` in much greater detail later.

</details>

<details>
  <summary>Compare with the ES5 class syntax</summary>

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

### We Do: Let's create an instance of Car with the ```new``` keyword (1 minute)

### 3. Inheritance (5 minutes)

- Often we'll need to take our class and expand on it. Think about types of cars, for instance.

- For these cases, we create sub-classes through a process called *inheritance.*

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
