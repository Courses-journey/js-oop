<div align="center">
<img src="https://elzero.org/wp-content/themes/elzero/imgs/logo.png" alt='source' width="200"/>

# Elzero Web School

[JS OOP Course](https://www.youtube.com/playlist?list=PLDoPjvoNmBAzLyvrWPwMw6bbBlTwPxgLF)
</div>

# 01

- What u will learn?
  - Class + Object
  - Object Method
  - Instantiation
  - Prototype
  - Inheritance
  - Future Feature

---

# 03

- Defining Object

  - [1] Object Literal

- Accessing Object
  - Properties
    - `Object.Property` => Dot Notation
    - `Object["Property"]` => Bracket Notation
  - Methods
    - `Object.Method()` => Dot Notation

---

# 05

Dot Notation vs Bracket Notation

```
let myObj = {
"One": 1,
"Two!": 2
};

console.log(myObj.One);
// console.log(myObj."One"); // Syntax Error
// console.log(myObj.Two!); // Syntax Error

console.log(myObj["One"]); // 1
console.log(myObj["Two!"]); // 2

let myObj2 = {
1: "One",
2: "Two"
};

// console.log(myObj2.1); // Syntax Error

console.log(myObj2["1"]);
console.log(myObj2["2"]);

let myVariable = "name";

let myLastObj = {
name: "Osama"
};

console.log(myLastObj.myVariable); // Undefined
console.log(myLastObj[myVariable]); // Osama
console.log(myLastObj["name"]); // Osama
```

---

# 06

- Defining Object
  - [1] Object Literal
  - [2] With New Keyword

```
let user = new Object();

user.firstName = "Osama";
user.lastName = "Elzero";
user["age"] = 37;

user.getFullName = function () {
  return `Full Name Is ${user.firstName} ${user.lastName}`;
};

console.log(user);
console.log(user.firstName);
console.log(user["lastName"]);
console.log(user.age);
console.log(user.getFullName());
```

---

# 07

- Defining Object
  - [1] Object Literal
  - [2] With New Keyword
  - [3] With Object.create()

`[3] With Object.create()` to create object from exisiting one and u can edit it

---

# 08

- Defining Object
  - [1] Object Literal
  - [2] With New Keyword
  - [3] With Object.create()
  - [4] With Object.assign(target,sources..)

`[4] With Object.assign()` to copy object properties and methods from sources to target

---

# 09

- Delete Operator

  - can't delete any variable declared with const let var
  - can't delete any thing from frezzed object `Object.freeze(object)`
  - can't delete any property with `configurable:false`

  - return `true` if delete done
  - return `false` if delete not done

`delete object.property`

```
const user = { name: "Osama" };

console.log(user);
console.log(user.name);

// delete user; // Delete Property Not Object
// delete user.name;
// delete user["name"];
console.log(delete user["name"]);

console.log(user);
console.log(user.name);

console.log("#".repeat(15));

const username = "Osama";
console.log(username);
console.log(delete username);
console.log(username);

console.log("#".repeat(15));

const freezedObj = Object.freeze({ age: 37 });
console.log(freezedObj);
console.log(freezedObj.age);

console.log(delete freezedObj.age);

console.log(freezedObj);
console.log(freezedObj.age);

console.log("#".repeat(15));

const eObj = {};
Object.defineProperty(eObj, "a", { value: 1, configurable: false });
console.log(eObj);
console.log(eObj.a);

console.log(delete eObj.a);

console.log(eObj);
console.log(eObj.a);
```

---

# 10

For ... In Loop
Loop Through The Properties Of The Objects

```
const user = {
  name: "Osama",
  country: "Egypt",
  age: 37,
};

let finalData = "";

for (let info in user) {
  // console.log(`The ${info} Is => ${user[info]}`);
  finalData += `<div>The ${info} Is => ${user[info]}</div>`;
}

// console.log(user.country);
// console.log(user["country"]);

console.log(finalData);

document.getElementById("info").innerHTML = finalData;
```

---

# 11

- Constructor Function
  - it's recommended to name Constructor Function with capital case
  - if u want to assign const value and never be changed use `this.property = value`
  - to init object frim it use new keyword like `let phone2 = new Phone(12,3,2)`

```
function Phone(serial, color, price) {
  this.camera = none;
  this.serial = serial;
  this.color = color;
  this.price = price;
}
```

---

# 12

- Constructor Function
  - `instanceof` To check if created object is init from Object u can use `object instanceof Object`
  - `.constructor` To check if created object is init from Object u can use `object.constructor === Object`

```
function Phone(serial) {
  // this is The Created Object From The Constrcutor Function
  console.log(this);
  this.serial = `#${serial}`;
}

let phone1 = new Phone(123456);
let phone2 = new Phone(528951);
let phone3 = Phone(125698);

console.log(phone1.serial);
console.log(phone2.serial);
console.log(window.serial);

console.log(phone1 instanceof Phone);
console.log(phone2 instanceof Phone);
console.log(phone3 instanceof Phone);

console.log(phone1.constructor === Phone);
console.log(phone2.constructor === Phone);
// console.log(phone3.constructor === Phone); // Error

function sayHelloTo(someone) {
  // someone => Parameter
  return `Hello ${someone}`;
}

console.log(sayHelloTo("Osama")); // Osama => Argument
```

---

# 19

- Prototype
  - [1] Every Object Has A Prototype
  - [2] Prototype Chain Ends With Object.prototype
  - [2] In Javascript Function Is Object

```
function User(name) {
/_
[1] Create Empty Object
[2] Assign The New Object To this Context
[3] New Object Created Prototype = Function Prototype
this = {};
this.**proto** = User.**proto**
_/
this.name = name;
/_
[4] Return The New Object
return this
_/

// if (!(this instanceof User)) {
// // throw new Error("Must Be Called With New Keyword");
// console.log("Error");
// }

// ES6
if (!new.target) {
// throw new Error("Must Be Called With New Keyword");
console.log("Error");
}
}

let user1 = new User("Osama");
let user2 = new User("Ahmed");
console.log(User.prototype);
console.log(user1);

let myArray = [1, 2, 3, 4];
```

---

# 21

Class

```
class User {
constructor(name, email) {
this.name = name;
this.email = email;
}
sayHello() {
return `Hello ${this.name}`;
}
showEmail() {
return `Your Email Is ${this.email}`;
}
}

let user1 = new User("Osama", "o@nn.sa");
let user2 = new User("Ahmed");

console.log(user1);
console.log(user2);
```

---

# 21

Class

Static Properties & Methods

```
class User {
// Static Properties
static counter = 0;

constructor(name, email, counter) {
this.name = name;
this.email = email;
this.counter = counter;
User.counter++;
}
sayHello() {
return `Hello ${this.name}`;
}
showEmail() {
return `Your Email Is ${this.email}`;
}

// Static Methods
static countObjects = function () {
return `${this.counter} Objects Created.`;
};
}

let user1 = new User("Osama", "o@nn.sa", 2);
let user2 = new User("Ahmed", "o@nn.sa", 2);
let user3 = new User("Osama", "o@nn.sa", 2);
let user4 = new User("Osama", "o@nn.sa", 2);
// let user2 = User("Ahmed", "a@nn.sa"); // TypeError: Class constructor User

console.log(typeof User); // Function
console.log(User === User.prototype.constructor); // True

console.log(User.countObjects());
```

---

# 22

Class

- Inheritance
  - use `extend` key word to inherit
  - to override paernt function in child make one of the same name and u are done
  - use `super()` in child to pass param to parent

```
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
  sayHello() {
    return `Hello ${this.name}`;
  }
  showEmail() {
    return `Your Email Is ${this.email}`;
  }
  writeMsg() {
    return `Message From Parent Class`;
  }
}

class Admin extends User {
  constructor(name, email) {
    super(name, email);
  }
  adminMsg() {
    return `You Are Admin`;
  }
  writeMsg() {
    return `Message From Child Class`;
  }
}

let admin1 = new Admin("Osama", "o@nn.sa");
```

---

# 23

JavaScript Accessors
Getters & Setters

js don't apply the right functionality of get and set

```
class User {
  constructor(name, email) {
    this.name = name;
    this.email = email;
  }
  sayHello() {
    return `Hello ${this.name}`;
  }
  get showInfo() {
    return `Name: ${this.name}, Email" ${this.email}`;
  }
  changeName(newName) {
    this.name = newName;
  }
  set changeEmail(newEmail) {
    this.email = newEmail;
  }
}
```

---

# 24

Object Metadata And Descriptor

- Object Meta Data

  - `writable` => key can be edited
  - `enumerable` => key can be used in loop
  - `configurable` => key can be configured
  - `value` => value of key to assign

Object.defineProperty(obj, prop, descriptor)

```
const myObject = {
  a: 1,
  b: 2,
};

Object.defineProperty(myObject, "c", {
  writable: false,
  enumerable: false,
  configurable: true,
  value: 3,
});

Object.defineProperty(myObject, "c", {
  writable: true,
});

// console.log(delete myObject.c); // Will Not Delete Because configurable is False
myObject.c = 500; // Will Not Change Because writable is False

console.log(myObject);

console.log("#".repeat(10));

for (let prop in myObject) {
  console.log(prop, myObject[prop]);
}

console.log("#".repeat(10));

console.log(Object.getOwnPropertyNames(myObject));
```

---

# 25

Object.defineProperties & Trainings

- Descriptor has a default value of `false` when using `Object.defineProperty(obj, prop, descriptor)`
- Descriptor has a default value of `true` when using `Object.property = value`
- `Object.getOwnPropertyDescriptor(myObject,key)` to get Descriptor of certin key

## getOwnPropertyNames(myObject) vs keys(myObject)

- `Object.keys(myObject)` => get all iteratables keys in object.
- `Object.getOwnPropertyNames(myObject)` => get all keys in object.

## defineProperties vs defineProperty

- `defineProperty` => can set only one property
- `defineProperties` => can set multipule properties

```
const myObject = {
  a: 1,
  b: 2,
};

Object.defineProperty(myObject, "a", {
  writable: false,
  enumerable: false,
  configurable: false,
  value: 500,
});

Object.defineProperty(myObject, "c", {
  value: 3,
});

myObject.d = 4;

Object.defineProperties(myObject, {
  e: {
    value: 5,
  },
  f: {
    value: 6,
  },
  g: {
    value: 7,
  },
});

console.log(myObject);
console.log(Object.getOwnPropertyDescriptor(myObject, "a"));
console.log(Object.getOwnPropertyDescriptor(myObject, "c"));
console.log(Object.getOwnPropertyDescriptor(myObject, "d"));

console.log(Object.getOwnPropertyNames(myObject));
console.log(Object.keys(myObject));
```

---

# 26 - Done
