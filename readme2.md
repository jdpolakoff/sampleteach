# Prototypal Inheritance in Object-Oriented Javascript

## Learning Objectives
- Demonstrate a use case that explains prototypal inheritance and
what kind of flexibility it gives to programmers
- Use namespaces to organize application code
- Define a custom constructor method that sets one or more
properties of a new object


## Overview
1. Review of Objects
2. Intro to OOP in JS
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

### 2. Intro to OOP concepts in JS (5 minutes)

We've already done some object-oriented programming in Ruby, but before we
get in to OOP in JS there are a few loose ends we need to tie up:

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
    <summary>4. Why does it matter that functions are objects in JS?</summary>

    That allows us to attach functions as properties on objects.
</details>
<details>
    <summary>5. Do functions have context?</summary>

    They do!
</details>

### 3. Classes in ES6 (10 minutes / 0:25)
Classes were introduced in ES5, and were instantiated with the following syntax:

```js
function Card(rank, suit, score) {
  this.rank = rank;
  this.suit = suit;
  this.score = score;
  this.title = `${rank} of ${suit}`;
  this.isHigher = (cardOne, cardTwo) => cardOne > cardTwo;
}
```

With ES6, the language was updated to bring the syntax more inline with how other popular programming languages handle OOP. This includes the introduction of the `class` keyword. Nothing changed under the hood, just what we type to create a class.

```js
class Card {
  constructor(rank, suit, score) {
    this.rank = rank;
    this.suit = suit;
    this.score = score;
    this.title = `${rank} of ${suit}`;
  }

  isHigher(cardOne, cardTwo) {
    return cardOne > cardTwo;
  }
}
```

#### Vocabulary:

**Class** - an object that models real world things in our application

**Instance** - a object defined by our class

**Constructor** - the function that defines instances of our class

<details>
  <summary>Solution</summary>

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

</details>

### 4. Inheritance (15 minutes / 1:30)

Often we'll need to take our class and expand on it for particular types of implementations of it. Think about types of Cars, for instance. For this case, we create sub-classes through a process called Inheritance.

In ES6, we extend an existing class with the `extend` keyword. This will let us create a subclass:

```js
class Car {
  constructor(make, color) {
    this.make = make
    this.color = color
  }
}

class Toyota extends Card {
  drive() {
    console.log('vroom vroom')
  }
}
```

If we have properties that we want to add to our subclass, we still need to take in the properties for our parent class, and pass them up to our parent class with `super`.

```js
class Car {
  constructor(model, color) {
    this.model = model
    this.color = color
  }
}

class Toyota extends Card {
  constructor(model, color) {
    super(model, color)
    this.make = 'Toyota'
  }
  drive() {
    console.log('vroom vroom')
  }
}
```

## You Do: [Inheritance](https://git.generalassemb.ly/ga-wdi-exercises/es6-classes-inheritance-practice) (20 minutes / 1:50)

> 15 minutes exercise. 5 minutes review.

-------

## Closing / Questions (10 minutes / 2:00)

* What are the benefits to using an OOP approach to programming?
* What is a class? What is `new`? How are they related?
* What does it mean to use "inheritance" when working with classes?
* How do we indicate that one class inherits from another?
* What does `super` mean?

## Homework: [Geometry](https://git.generalassemb.ly/ga-wdi-exercises/js_geometry)

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
