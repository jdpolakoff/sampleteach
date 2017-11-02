# Prototypal Inheritance in Object-Oriented Javascript

## What does that mean?

Prototypal Inheritance is how JavaScript allows us to share code among objects. Prototypes are simply objects that define the behavior of other objects by passing down data and functionality.

## Why is prototypal inheritance good for developers?

1) It allow us to write less code -- remember the DRY (Don't Repeat Yourself) principle.
2) It allows us to write code that is better-organized and more maintainable for other developers.
This will be especially important when you're working on large projects with other developers.

## Learning Objectives
- Learn to use namespaces to organize application code.
- Learn to use a custom constructor method to set one or more properties on a new object.
- Learn how prototypal inheritance gives programmers additional flexibility.

## Overview
1. Review of Objects
2. Classes in ES6
3. Inheritance

### 1. Review of Objects in JS (3 minutes)

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
We're doing three really important things here:

  1. We're modeling a real world thing (in this case, a car) inside our code.
  2. We're storing all the data and behavior for that thing is accessible in a single place.
  3. We're creating a namespace in the ```car``` object, which helps to declutter the global namespace. Let's go into the console and call ```car.drive()```. What happens when we try to call the drive method on the global object -- ```window.drive()```.

Let's go back to the first point, which is what makes Object-Oriented Programming so powerful.

Why might we want to model real world things in our code?

__Example: lets say we're building an app for a car rental company (Rent-a-Car). If they buy a new car to rent out to customers, they'll want to manage that new car inside the app we're building for them. Do we want to create a new object like the one above for each car new car? No, most likely we want to use a class to help us create the new cars.__

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

### 2. Classes in ES6 (5 minutes)

**What is a class?**

1) A class is an object we can use to help us create new objects and define the behavior of new objects.

2) Classes can also pass data and functionality to sub-classes through prototypal inheritance. (More on that in a minute).

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

  2) The constructor method. This method assigns properties to objects when a new instance of the class is instantiated.

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

#### We Do: Let's create an instance of Car with the ```new``` keyword (1 minute)

### 3. Inheritance (5 minutes)

- Often we'll need to take our class and expand on it. Think about types of cars, for instance.

- For these cases, we create sub-classes through a process called *inheritance.*

In ES6, we extend an existing class with the `extend` keyword. This will let us create a subclass.

If we have properties that we want to add to our subclass from our parent class, we need to call the `super` method. `Super` calls the constructor function on the parent class.

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
Let's go into the console and create a new Toyota. Then let's try to call the ```drive()``` method from within the context of that new instance of a Toyota. What happens?

What happens if we insert this method into the Toyota class and then call the method from a newly instantiated object?
```js
drive() {
  console.log('beep beep')
}
```

By creating sub-classes that inherit from parent classes, developers gain flexibility in how they structure their data and functionality.

**BONUS:** Write the above code into your console and then run ```Object.getPrototypeOf(Toyota)```.

What do you get? What is the prototype of the Toyota class?

## Closing / Questions

* What are the benefits to namespacing in an OOP approach to programming?
* What is a class? What is `new`? How are they related?
* What does it mean to use "inheritance" when working with classes?
* How do we indicate that one class inherits from another?
* What does `super` mean?

## Additional Reading

* [MDN Documentation on Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
* [Introduction to Javascript ES6 Classes](https://strongloop.com/strongblog/an-introduction-to-javascript-es6-classes/)
* [Getters, Setters, and Organizing Responsibility in Javascript](http://raganwald.com/2015/08/24/ready-get-set-go.html)
* [Static Members in ES6](http://odetocode.com/blogs/scott/archive/2015/02/02/static-members-in-es6.aspx)
* [Lesson: JS View Classes](https://git.generalassemb.ly/ga-wdi-lessons/js-view-classes)

#### Prototypical Inheritance

* [Inheritance and the Prototype Chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
* [ES6 Classes and Javascript Prototypes](https://reinteractive.com/posts/235-es6-classes-and-javascript-prototypes)
* [Master the Javascript Interview: What's the Difference Between Class & Prototypical Inheritance](https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9#.uzl8ohf8c)
