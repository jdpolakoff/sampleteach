# Object-Oriented Programming in Javascript

## Learning Objectives
- Answer the question, what is Object-Oriented Programming (OOP)?
- Identify and define: a class, an instance, and a constructor
- Create a class
- Use the `new` keyword to create instances of a class
- Define the concept of inheritance as it pertains to classes
- Create a class that inherits from another using the `extends` and `super` keywords

## Overview
1. Review of Objects
2. Intro to OOP in JS
3. Classes in ES6
4. Inheritance

## Schedule
| Time | Section |
| --- | --- |
| 10 min | Review Objects |
| 10 min | Intro to OOP |
| 15 min | Defining a Class |
| 10 min | Domain Modeling and build your first class |
| 10 min | Classes in ES6 |
| 20 min | Make an ATM Class |
| 10 min | Break |
| 15 min | Inheritance |
| 20 min | Inheritance Exercise |
| 10 min | Closing |

## Intro

### 1. Review of Objects in JS (10 minutes / 0:10)

The important thing to remember about objects is that they encapsulate related data and behavior into an organized structure. We saw this when we discussed **object literal notation**. Recall that we can define an object like this:

Lets check out `one.js` in the `demos/` folder!

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

### 3. Classes in ES6 (10 minutes / 0:25)
Understanding the old syntax is important for understanding the new syntax. With ES6, the language was updated to bring the syntax more inline with how other popular programming languages handle OOP. This includes the introduction of the `class` keyword. Nothing changed under the hood, just what we type to create a class.

Lets checkout `three.js` in the `exercises/` folder!

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


## Break (10 minutes / 1:15)

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
