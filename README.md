# Technical Writing Assignment

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt 1     

Imagine you are teaching a friend about OOP. They mainly want to understand what is Encapsulation. Write a brief lesson on Encapsulation that includes the following:

* What is encapsulation?
* What major goal does this help to achieve in software engineering?
* Give an example (in code) of encapsulation.
* An explanation of how the code example demonstrates encapsulation

### Response 1

Encapsulation is one of the core pillars of Object-Oriented Programming.
 OOP is the concept of bundling variabls and the methods
that operate on that data into a class. Encapsulation 
also restricts direct access to some details of an object’s data, protecting 
it from unintended interference and misuse. This is often achieved using access 
modifiers like `private`, `protected`, and `public`.

Encapsulation helps achieve data hiding, which improves security and maintains
data integrity by preventing external entities from directly modifying the internal
state of an object. It also promotes modularity and code maintainability.

```js

class BankAccount {
  #balance; // Private field

  constructor(balance) {
    this.#balance = balance;
  }

  deposit(amount) {
    if (amount > 0) this.#balance += amount;
  }

  withdraw(amount) {
    if (amount > 0 && amount <= this.#balance) this.#balance -= amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount(1000);
account.deposit(500);
account.withdraw(200);
console.log(account.getBalance()); // Output: 1300
console.log(account.#balance); // Error: Private field is not accessible



```
1. The `#balance` field is private, so it cannot be accessed or modified directly.

2. The `deposit` and `withdraw` methods control how the balance is updated.

3. The `getBalance` method provides read-only access to the balance.


## Prompt 2

The following `friendsManager` object is an example of an interface that is **NOT** consistent and predictable:

```js
const friendsManager = {
 friends: [],
 addFriend(newFriend) {
   if (typeof newFriend !== 'string') return;
   this.friends.push(newFriend);
 }
}


friendsManager.addFriend('daniel');
friendsManager.addFriend(true);
friendsManager.friends.push('emmaneul');
friendsManager.friends.push(42);
```

Explain how the code is not consistent or predictable, then provide an example in code that uses closure to make it more consistent and predictable.

### Response 2

## Prompt 3

With OOP in JavaScript, it's possible to use factory functions to achieve encapsulation and re-use them to make objects that look alike. However, factory functions have drawbacks and we often use classes instead. 

How would you explain to a budding developer what the drawbacks of using factory functions are and why it is better to use classes instead?

### Response 3
Factory functions have drawbacks because they create a new copy of methods for each object,
leading to higher memory usage and slower performance. Additionally, factory functions do not
automatically link objects to a prototype, requiring manual setup for shared behavior. This proves that classes are more efficient 
because methods are stored on the prototype, meaning all instances share the same function, reducing
memory consumption. Classes also support built-in inheritance, faster execution, and `instanceof checks, 
making them the preferred choice for optimized JavaScript applications. 
## Prompt 4

Do some research on the history of when / how classes were introduced into JavaScript and share your findings. Your response should include:

* What version of JavaScript were classes introduced in and when did it come out?
* Why were classes introduced into JavaScript?


### Response 4

## Prompt 5

OOP can still be achieved in JavaScript without using the `class` keyword and instead using the "Constructor Functions" and the "Prototype Chain" (look them up!)

```js
function Person(name, age) {
 this.name = name;
 this.age = age;
}


Person.prototype.greet = function () {
 return `Hi, I'm ${this.name}, and I'm ${this.age} years old.`;
};


const alice = new Person('Alice', 30);
console.log(alice.greet());
```

Provide one point that advocates for the use of this syntax and then provide a counter-argument for the use of classes instead.

### Response 5
