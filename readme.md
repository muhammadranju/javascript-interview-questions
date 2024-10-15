## 1. JavaScript কি ধরনের ভাষা?

উত্তর: JavaScript একটি scripting ভাষা, যা মূলত client-side ওয়েব ডেভেলপমেন্টের জন্য ব্যবহৃত হয়। এটি interpreted language যার মানে এটি সরাসরি browser এ run হয়, কোনো compilation ছাড়াই।

## 2. Variable declaration এর ক্ষেত্রে var, let, এবং const এর মধ্যে পার্থক্য কি?

উত্তর:

- var: এটি function-scoped, মানে এটি শুধুমাত্র একটি ফাংশনের ভিতরে সীমাবদ্ধ।
- let: এটি block-scoped, মানে এটি শুধুমাত্র {} ব্লকের ভিতরে সীমাবদ্ধ থাকে।
- const: এটি block-scoped, কিন্তু এর মান একবার সেট করার পর আর পরিবর্তন করা যায় না।

## 3. Closures কী এবং কীভাবে কাজ করে?

উত্তর: Closure হলো একটি ফাংশন যা তার বাহিরের scope এর ভ্যারিয়েবলগুলোকে মনে রাখে। Closure এর কারণে inner function তার parent function এর variable access করতে পারে।

উদাহরণ:

```
function outerFunction() {
  let outerVar = 'Hello';
  function innerFunction() {
    console.log(outerVar);
  }
  return innerFunction;
}

const closure = outerFunction();
closure(); // Output: Hello
```

## 4. Hoisting কী?

উত্তর: Hoisting হলো একটি মেকানিজম যেখানে JavaScript variable declaration এবং function declaration কে স্বয়ংক্রিয়ভাবে স্কোপের উপরের দিকে নিয়ে যায়। কিন্তু initialization টা পরে হয়।

উদাহরণ:

```
console.log(x); // Output: undefined
var x = 10;
```

এখানে, `x` প্রথমে `undefined `হিসেবে `hoist `করা হয়েছে।

## 5. Callback Function কি?

উত্তর:
Callback ফাংশন হলো এমন একটি ফাংশন যা অন্য একটি ফাংশনের argument হিসেবে পাস করা হয় এবং সেই ফাংশনের ভিতরে এক সময়ে call করা হয়।

উদাহরণ:

```
function greet(name, callback) {
  console.log('Hello ' + name);
  callback();
}

function sayGoodbye() {
  console.log('Goodbye!');
}

greet('Alice', sayGoodbye); // Output: Hello Alice, Goodbye!
```

## 6. Asynchronous JavaScript কী এবং এটি কীভাবে কাজ করে?

উত্তর: Asynchronous JavaScript হলো এমন একটি মেকানিজম যেখানে কিছু কাজগুলো non-blocking ভাবে করা যায়। যেমন: setTimeout, fetch, বা AJAX কল। এটি Event Loop এর মাধ্যমে কাজ করে, যা কলব্যাকগুলিকে এক সময়ে execute করে।

## 7. Event Bubbling এবং Event Capturing এর মধ্যে পার্থক্য কি?

উত্তর:

- Event Bubbling: যখন একটি ইভেন্ট ঘটে, তখন এটি প্রথমে target element এ ঘটে এবং তারপর উপরের parent elements এর দিকে চলে যায়।
- Event Capturing: এর উল্টো, ইভেন্টটি প্রথমে root element এ ঘটে এবং নিচের target element এ পৌঁছায়।

## 8. `this `কী?

উত্তর: `this `হলো একটি কিওয়ার্ড যা বর্তমান execution context কে নির্দেশ করে। অর্থাৎ এটি সেই অবজেক্টকে নির্দেশ করে যা বর্তমান ফাংশনকে কল করেছে।

উদাহরণ:

```
const person = {
  name: 'Alice',
  greet: function() {
    console.log('Hello, ' + this.name);
  }
}

person.greet(); // Output: Hello, Alice
```

## 9. `==` এবং `===` এর মধ্যে পার্থক্য কি?

উত্তর:

`==` (Loose Equality): এটি ভ্যালুগুলির মধ্যে type coercion করে এবং তারপর তাদের তুলনা করে।
`===` (Strict Equality): এটি ভ্যালুগুলির type এবং value উভয়ই চেক করে। যদি তারা একই না হয়, তবে এটি false রিটার্ন করে।

উদাহরণ:

```
console.log(1 == '1');  // true (type coercion হয়)
console.log(1 === '1'); // false (different types)
```

## 10. Promises কী এবং এটি কীভাবে কাজ করে?

উত্তর:
Promise হলো একটি অবজেক্ট যা ভবিষ্যতে কোন একটি asynchronous operation এর সফলতা বা ব্যর্থতার প্রতিনিধিত্ব করে। Promises এর তিনটি স্টেট থাকে:

- Pending: অপারেশনটি চলছে।
- Fulfilled: অপারেশনটি সফল হয়েছে।
- Rejected: অপারেশনটি ব্যর্থ হয়েছে।

উদাহরণ:

```
const promise = new Promise((resolve, reject) => {
  let success = true;
  if(success) {
    resolve('Operation Successful');
  } else {
    reject('Operation Failed');
  }
});

promise.then(result => console.log(result))
       .catch(error => console.log(error));
```

## ১১. `prototype` এবং `__proto__` এর মধ্যে পার্থক্য কি?

উত্তর:

- `prototype`: এটি একটি অবজেক্ট যা কনস্ট্রাক্টর ফাংশনের সাথে যুক্ত থাকে। এটি নতুন অবজেক্ট তৈরির সময় প্রোটোটাইপ চেইনে যুক্ত হয়।
- `__proto__`: এটি প্রতিটি অবজেক্টের অভ্যন্তরীণ প্রোপার্টি যা অবজেক্টের প্রোটোটাইপকে নির্দেশ করে।

উদাহরণ:

```
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log('Hello, ' + this.name);
}

const alice = new Person('Alice');
alice.greet(); // Output: Hello, Alice

console.log(alice.__proto__ === Person.prototype); // true

```

## ১২. `map`, `filter`, এবং `reduce` ফাংশনের মধ্যে পার্থক্য কি?

উত্তর:

- `map`: এটি একটি নতুন অ্যারে তৈরি করে যেখানে প্রতিটি উপাদান একটি নির্দিষ্ট ফাংশনের মাধ্যমে পরিবর্তিত হয়।
- `filter`: এটি একটি নতুন অ্যারে তৈরি করে যা শুধুমাত্র সেই উপাদানগুলো ধারণ করে যা নির্দিষ্ট শর্ত পূরণ করে।
- `reduce`: এটি একটি একক মানে অ্যারের সমস্ত উপাদানকে রিডিউস করে, সাধারণত সমষ্টি বা গুণফল হিসাব করার জন্য ব্যবহৃত হয়।

উদাহরণ:

```
const numbers = [1, 2, 3, 4, 5];

// map
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// filter
const even = numbers.filter(num => num % 2 === 0);
console.log(even); // [2, 4]

// reduce
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15
```

## ১৩. `async` এবং `await` কীভাবে কাজ করে?

উত্তর: `async` এবং `await` হল asynchronous কোড লেখার একটি সহজ উপায়। `async` ফাংশনকে প্রতিশ্রুতি (Promise) রিটার্ন করে এবং `await` ব্যবহার করে সেই প্রতিশ্রুতির ফলাফল পাওয়া যায়।

উদাহরণ:

```
function fetchData() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('Data received');
    }, 2000);
  });
}

async function getData() {
  console.log('Fetching data...');
  const data = await fetchData();
  console.log(data);
}

getData();
// Output:
// Fetching data...
// (২ সেকেন্ড পরে)
// Data received
```

## ১৪. `spread` এবং `rest` অপারেটরের মধ্যে পার্থক্য কি?

উত্তর:

- `spread` অপারেটর (`...`): এটি একটি অ্যারের উপাদানগুলোকে পৃথক পৃথক করে, যেমন ফাংশনে আর্গুমেন্ট পাস করতে।
- `rest` অপারেটর (`...`): এটি একটি ফাংশনের আর্গুমেন্টগুলোকে একটি অ্যারে হিসেবে গ্রহণ করে।

উদাহরণ:

```
function fetchData() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('Data received');
    }, 2000);
  });
}

async function getData() {
  console.log('Fetching data...');
  const data = await fetchData();
  console.log(data);
}

getData();
// Output:
// Fetching data...
// (২ সেকেন্ড পরে)
// Data received
```

## ১৫. `debounce` এবং `throttle` এর মধ্যে পার্থক্য কি?

উত্তর:

- Debounce: এটি একটি ফাংশনকে একটি নির্দিষ্ট সময়ের মধ্যে একবার কল হতে বাধা দেয়, যতক্ষণ না নির্দিষ্ট সময় পেরোয়া হয়।
- Throttle: এটি একটি ফাংশনকে একটি নির্দিষ্ট সময়ের জন্য সীমিত করে, যাতে নির্দিষ্ট সময়ের মধ্যে একাধিক কল করা না যায়।

উদাহরণ:

```
// Debounce
function debounce(func, delay) {
  let timeout;
  return function(...args) {
    clearTimeout(timeout);
    timeout = setTimeout(() => func.apply(this, args), delay);
  }
}

window.addEventListener('resize', debounce(() => {
  console.log('Window resized');
}, 500));

// Throttle
function throttle(func, limit) {
  let inThrottle;
  return function(...args) {
    if (!inThrottle) {
      func.apply(this, args);
      inThrottle = true;
      setTimeout(() => inThrottle = false, limit);
    }
  }
}

window.addEventListener('scroll', throttle(() => {
  console.log('Scrolled');
}, 1000));
```

## ১৬. `bind`, `call`, এবং `apply` এর মধ্যে পার্থক্য কি?

উত্তর:

- `call`: এটি একটি ফাংশনকে নির্দিষ্ট this কনটেক্সট সহ কল করে এবং আর্গুমেন্টগুলো আলাদা আলাদা পাস করে।
- `apply`: এটি call এর মতই কাজ করে কিন্তু আর্গুমেন্টগুলো একটি অ্যারে হিসেবে পাস করে।
- `bind`: এটি একটি নতুন ফাংশন তৈরি করে যা নির্দিষ্ট this কনটেক্সট সহ কল করা যাবে।

উদাহরণ:

```
const person = {
  name: 'Alice'
};

function greet(greeting, punctuation) {
  console.log(greeting + ', ' + this.name + punctuation);
}

// call
greet.call(person, 'Hello', '!'); // Hello, Alice!

// apply
greet.apply(person, ['Hi', '!!']); // Hi, Alice!!

// bind
const greetAlice = greet.bind(person);
greetAlice('Hey', '!!!'); // Hey, Alice!!!
```

## ১৭. `undefined` এবং `null` এর মধ্যে পার্থক্য কি?

উত্তর:

- `undefined`: এটি একটি ভ্যালু যা ইঙ্গিত করে যে কোনো ভেরিয়েবল ডিফাইন করা হয়েছে কিন্তু সেটি কোনো মান ধারণ করছে না।
- `null`: এটি একটি ভ্যালু যা ইঙ্গিত করে যে কোনো ভেরিয়েবল সচেতনভাবে কোনো মান নেই বলে সেট করা হয়েছে।

উদাহরণ:

```
let a;
console.log(a); // undefined

let b = null;
console.log(b); // null
```

## ১৮. `localStorage` এবং `sessionStorage` এর মধ্যে পার্থক্য কি?

উত্তর:

`localStorage`: এটি ডেটা ব্রাউজারে স্থায়ীভাবে সংরক্ষণ করে, ব্রাউজার বন্ধ হলেও ডেটা থাকবে।
`sessionStorage`: এটি ডেটা শুধুমাত্র ব্রাউজার সেশনের জন্য সংরক্ষণ করে, ব্রাউজার বন্ধ করলে ডেটা মুছে যাবে।

উদাহরণ:

```
// localStorage
localStorage.setItem('username', 'Alice');
console.log(localStorage.getItem('username')); // Alice

// sessionStorage
sessionStorage.setItem('token', '12345');
console.log(sessionStorage.getItem('token')); // 12345
```

## ১৯. `JSON.stringify` এবং `JSON.parse` কী?

উত্তর:

- `JSON.stringify`: এটি একটি জাভাস্ক্রিপ্ট অবজেক্টকে JSON স্ট্রিং এ রূপান্তর করে।
- `JSON.parse`: এটি একটি JSON স্ট্রিংকে জাভাস্ক্রিপ্ট অবজেক্টে রূপান্তর করে।

উদাহরণ:

```
const obj = { name: 'Alice', age: 25 };

// stringify
const jsonString = JSON.stringify(obj);
console.log(jsonString); // '{"name":"Alice","age":25}'

// parse
const parsedObj = JSON.parse(jsonString);
console.log(parsedObj); // { name: 'Alice', age: 25 }
```

## ২০. `strict mode` কী এবং কেন এটি ব্যবহার করা হয়?

উত্তর: Strict mode হলো জাভাস্ক্রিপ্টের একটি ফিচার যা কোডের কিছু ভুল কম্পনেন্টগুলি ধরতে সাহায্য করে এবং কিছু অপ্রত্যাশিত বিহেভিয়র প্রতিরোধ করে। এটি ব্যবহার করলে কোড আরও নিরাপদ এবং ত্রুটি মুক্ত হয়।

কিভাবে ব্যবহার করবেন:

```
'use strict';

function myFunction() {
  // Strict mode-এ কিছু অপারেশন করতে পারবেন না যা সাধারণত পারতেন না
  // উদাহরণস্বরূপ, অপরিবর্তনীয় ভেরিয়েবল পুনরায় ডিক্লেয়ার করা
  var x = 10;
  // var x = 20; // এটি Strict mode-এ এরর দিবে
}

myFunction();
```

## ২১. `setTimeout` এবং `setInterval` এর মধ্যে পার্থক্য কি?

উত্তর:

- `setTimeout`: এটি একটি নির্দিষ্ট সময় পরে একবার একটি ফাংশন কল করে।
- `setInterval`: এটি একটি নির্দিষ্ট সময় অন্তর ফাংশনটি বারবার কল করে।

উদাহরণ:

```
// setTimeout
setTimeout(() => {
  console.log('This runs once after 2 seconds');
}, 2000);

// setInterval
const intervalId = setInterval(() => {
  console.log('This runs every 3 seconds');
}, 3000);

// বাতিল করতে
// clearInterval(intervalId);

```

## ২২. `new` অপারেটর কী করে?

উত্তর: `new` অপারেটর একটি ফাংশনকে কনস্ট্রাক্টর হিসেবে ব্যবহার করে একটি নতুন অবজেক্ট তৈরি করে। এটি প্রোটোটাইপ সেট করে, অবজেক্ট ইন্সট্যান্স তৈরি করে এবং কনস্ট্রাক্টর ফাংশনে `this` নির্দেশ করে।

উদাহরণ:

```
function Person(name) {
  this.name = name;
}

const alice = new Person('Alice');
console.log(alice.name); // Alice
```

## ২৩. `bind` মেথড কেন এবং কখন ব্যবহার করবেন?

উত্তর: `bind` মেথড একটি ফাংশনের this কনটেক্সট নির্দিষ্ট করে এবং একটি নতুন ফাংশন রিটার্ন করে। এটি তখন ব্যবহার করা হয় যখন ফাংশনের this কনটেক্সট নির্দিষ্টভাবে সেট করতে হয়, যেমন ইভেন্ট হ্যান্ডলারে।

উদাহরণ:

```
const person = {
  name: 'Alice',
  greet: function() {
    console.log('Hello, ' + this.name);
  }
}

const greet = person.greet.bind(person);
greet(); // Hello, Alice
```

## ২৪. `Symbol` কী এবং কেন এটি ব্যবহার করা হয়?

উত্তর: `Symbol` হল একটি প্রিমিটিভ ডেটা টাইপ যা ইউনিক এবং ইমিউটেবল। এটি অবজেক্টের প্রোপার্টি কী হিসেবে ব্যবহৃত হয় যাতে প্রোপার্টি গুলি কনফ্লিক্ট না করে।

উদাহরণ:

```
const sym1 = Symbol('description');
const sym2 = Symbol('description');

console.log(sym1 === sym2); // false

const obj = {
  [sym1]: 'value1',
  [sym2]: 'value2'
}

console.log(obj[sym1]); // value1
console.log(obj[sym2]); // value2
```

## ২৫. `Generator` ফাংশন কী এবং কিভাবে কাজ করে?

উত্তর: `Generator` ফাংশন একটি বিশেষ ধরনের ফাংশন যা ইটারেটর অবজেক্ট রিটার্ন করে। এটি `function`\* সিনট্যাক্স দিয়ে ঘোষণা করা হয় এবং `yield` কিওয়ার্ড ব্যবহার করে মান রিটার্ন করে।

উদাহরণ:

```
function* myGenerator() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = myGenerator();

console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // 3
console.log(gen.next().done);  // true
```

## ২৬. `ES6` এর কিছু গুরুত্বপূর্ণ ফিচার কী কী?

উত্তর: `ES6` বা `ECMAScript` 2015 হল জাভাস্ক্রিপ্টের একটি বড় আপডেট যা অনেক নতুন ফিচার নিয়ে আসে। এর মধ্যে কিছু গুরুত্বপূর্ণ ফিচার হলো:

- `Let` এবং `Const`: ব্লক-স্কোপড ভেরিয়েবল ডিক্লেয়ারেশন।
- Arrow Functions: সংক্ষিপ্ত ফাংশন সিনট্যাক্স এবং `this` বাইন্ডিং।
- Template Literals: স্ট্রিং ইন্টারপোলেশন।
- Destructuring: অবজেক্ট এবং অ্যারের মান সরাসরি ভেরিয়েবলে ডিক্লেয়ার করা।
- Classes: ক্লাস-বেসড অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং সাপোর্ট।
- Promises: অ্যাসিঙ্ক্রোনাস অপারেশন হ্যান্ডলিং।
- Modules: কোড মডুলারাইজেশন এবং রিইউজিবিলিটি।

উদাহরণ:

```
// Arrow Function
const add = (a, b) => a + b;

// Template Literal
const name = 'Alice';
console.log(`Hello, ${name}!`);

// Destructuring
const person = { name: 'Alice', age: 25 };
const { name, age } = person;

// Classes
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log('Hello, ' + this.name);
  }
}

const alice = new Person('Alice');
alice.greet(); // Hello, Alice
```

## ২৭. `Memory Leak` কী এবং জাভাস্ক্রিপ্টে কিভাবে এড়ানো যায়?

উত্তর: `Memory Leak` হল এমন একটি অবস্থা যেখানে প্রোগ্রামটি অতিরিক্ত মেমরি ব্যবহার করে এবং সেই মেমরি মুক্ত হয় না। জাভাস্ক্রিপ্টে মেমোরি লিক এড়াতে:

- অনুপযুক্ত গ্লোবাল ভেরিয়েবল এড়িয়ে চলা।
- ইভেন্ট লিসেনারগুলো রিমুভ করা যখন আর প্রয়োজন না।
- অবজেক্ট রেফারেন্সগুলো মুক্ত করা যখন আর প্রয়োজন না।

উদাহরণ:

```
// মেমোরি লিক উদাহরণ
function createLeak() {
  const element = document.getElementById('myElement');
  window.myLeak = element; // গ্লোবাল ভেরিয়েবলে রেফারেন্স রাখা
}

// এড়ানোর উপায়
function preventLeak() {
  const element = document.getElementById('myElement');
  // প্রয়োজন না হলে রেফারেন্স মুক্ত করা
}
```

## ২৮. `DOM` এবং `BOM` এর মধ্যে পার্থক্য কি?

উত্তর:

- `DOM` (Document Object Model): এটি একটি API যা ওয়েব পেজের HTML বা XML ডকুমেন্টকে অবজেক্ট হিসেবে মডেল করে, যা জাভাস্ক্রিপ্ট দিয়ে ম্যানিপুলেট করা যায়।
- `BOM` (Browser Object Model): এটি ব্রাউজারের নিজস্ব অবজেক্ট এবং মেথডের সংগ্রহ যা ব্রাউজার উইন্ডো এবং এর প্রোপার্টি নিয়ন্ত্রণ করে, যেমন `window`, `navigator`, `location` ইত্যাদি।

উদাহরণ:

```
// DOM - একটি এলিমেন্ট নির্বাচন এবং ম্যানিপুলেট করা
const title = document.getElementById('title');
title.textContent = 'New Title';

// BOM - ব্রাউজার উইন্ডো নিয়ন্ত্রণ করা
console.log(window.innerWidth);
window.alert('Hello!');
```

## ২৯. `Event Delegation` কী এবং কেন এটি ব্যবহার করা হয়?

উত্তর: Event Delegation হল এমন একটি টেকনিক যেখানে একটি প্যারেন্ট এলিমেন্টে ইভেন্ট লিসেনার বসানো হয় এবং চাইল্ড এলিমেন্টের ইভেন্টগুলোকে হ্যান্ডেল করা হয়। এটি পারফরম্যান্স উন্নত করে এবং ডাইনামিক এলিমেন্টের ইভেন্ট হ্যান্ডলিং সহজ করে।

উদাহরণ:

```
// HTML
/*
<ul id="parentList">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
*/

// JavaScript
const parentList = document.getElementById('parentList');

parentList.addEventListener('click', function(event) {
  if(event.target && event.target.nodeName === 'LI') {
    console.log('List item clicked:', event.target.textContent);
  }
});
```

## ৩০. `Shadow DOM` কী এবং কেন এটি গুরুত্বপূর্ণ?

উত্তর: `Shadow DOM` হল ওয়েব কম্পোনেন্টের একটি অংশ যা একটি পৃথক, ইনক্যাপসুলেটেড DOM রুট তৈরি করে। এটি স্টাইল এবং স্ক্রিপ্টের আইসোলেশন নিশ্চিত করে, যাতে বাইরের কোডের সাথে কনফ্লিক্ট না হয়।

উদাহরণ:

```
const host = document.getElementById('shadowHost');
const shadowRoot = host.attachShadow({ mode: 'open' });

shadowRoot.innerHTML = `
  <style>
    p { color: blue; }
  </style>
  <p>This is inside Shadow DOM</p>
`;
```

৩১. `Immutable` এবং `Mutable` অবজেক্টের মধ্যে পার্থক্য কি?
উত্তর:

- `Immutable`: এগুলো এমন অবজেক্ট যা একবার তৈরি হলে পরিবর্তন করা যায় না। পরিবর্তন করলে নতুন অবজেক্ট তৈরি হয়।
- `Mutable`: এগুলো এমন অবজেক্ট যা তাদের প্রোপার্টি পরিবর্তন করা যায়।

উদাহরণ:

```
// Mutable
const obj = { name: 'Alice' };
obj.name = 'Bob'; // পরিবর্তন করা যায়

// Immutable (using Object.freeze)
const immutableObj = Object.freeze({ name: 'Alice' });
immutableObj.name = 'Bob'; // পরিবর্তন হবে না
console.log(immutableObj.name); // Alice
```

## ৩২. `Destructuring` কি এবং কিভাবে এটি কাজ করে?

উত্তর: `Destructuring` হল জাভাস্ক্রিপ্টের একটি সিনট্যাক্স যা অবজেক্ট বা অ্যারের মানগুলোকে সরাসরি ভেরিয়েবলে আলাদা করে নিয়ে আসে।

উদাহরণ:

```
// Array Destructuring
const numbers = [1, 2, 3];
const [a, b, c] = numbers;
console.log(a, b, c); // 1 2 3

// Object Destructuring
const person = { name: 'Alice', age: 25 };
const { name, age } = person;
console.log(name, age); // Alice 25
```

## ৩৩. `Immutable Data Structures` কী এবং কেন এটি গুরুত্বপূর্ণ?

উত্তর: Immutable Data Structures হল এমন ডেটা স্ট্রাকচার যা একবার তৈরি হলে পরিবর্তন করা যায় না। এটি ডেটা ফ্লোকে সহজ করে এবং বাগ কমাতে সাহায্য করে, বিশেষ করে রিয়েক্টের মতো লাইব্রেরিতে।

উদাহরণ:

```
const original = { name: 'Alice', age: 25 };

// Immutable update
const updated = { ...original, age: 26 };
console.log(original.age); // 25
console.log(updated.age);  // 26
```

## ৩৪. `CORS (Cross-Origin Resource Sharing)` কী এবং এটি কিভাবে কাজ করে?

উত্তর: CORS হল একটি সিকিউরিটি ফিচার যা ওয়েব ব্রাউজারকে এক ডোমেইন থেকে অন্য ডোমেইনের রিসোর্সে অ্যাক্সেস নিয়ন্ত্রণ করতে দেয়। সার্ভার সঠিক হেডার পাঠিয়ে CORS নিয়ন্ত্রণ করে।

উদাহরণ:

```
Access-Control-Allow-Origin: https://example.com
```

এই হেডারটি ব্রাউজারকে বলে যে `https://example.com` থেকে আসা রিকোয়েস্টগুলোকে অনুমতি দেওয়া হয়েছে।

## ৩৫. `Service Workers` কী এবং কেন এটি ব্যবহৃত হয়?

উত্তর: Service Workers হল জাভাস্ক্রিপ্ট স্ক্রিপ্ট যা ব্যাকগ্রাউন্ডে রান করে, নেটওয়ার্ক রিকোয়েস্ট ক্যাচ করে এবং অফলাইন অভিজ্ঞতা প্রদান করে। এটি PWA (Progressive Web Apps) তৈরিতে ব্যবহৃত হয়।

উদাহরণ:

```
// service-worker.js
self.addEventListener('install', event => {
  console.log('Service Worker installing.');
});

self.addEventListener('fetch', event => {
  event.respondWith(
    caches.match(event.request)
      .then(response => response || fetch(event.request))
  );
});
```

## ৩৬. `WebAssembly` কী এবং জাভাস্ক্রিপ্টের সাথে এর সম্পর্ক কি?

উত্তর: WebAssembly (Wasm) হল একটি বাইনারি ইন্সট্রাকশন ফরম্যাট যা ব্রাউজারে উচ্চ কর্মক্ষমতার কোড চালানোর জন্য ডিজাইন করা হয়েছে। এটি জাভাস্ক্রিপ্টের সাথে কমপ্লিমেন্টারি হিসেবে কাজ করে, যেখানে জাভাস্ক্রিপ্ট হাই-লেভেল লজিক হ্যান্ডেল করে এবং ওয়াসম হাই-পারফরম্যান্স কাজগুলিকে দ্রুত সম্পাদন করে।

উদাহরণ:

```
// জাভাস্ক্রিপ্ট থেকে WebAssembly মডিউল লোড করা
fetch('module.wasm')
  .then(response => response.arrayBuffer())
  .then(bytes => WebAssembly.instantiate(bytes))
  .then(results => {
    const instance = results.instance;
    console.log(instance.exports.exportedFunction());
  });
```

## ৩৭. `Memoization` কী এবং এটি কিভাবে কাজ করে?

উত্তর: Memoization হল একটি অপ্টিমাইজেশন টেকনিক যেখানে ফাংশনের পূর্বের ফলাফলগুলো ক্যাশে করে রাখা হয় যাতে একই ইনপুটের জন্য পুনরায় গণনা না করতে হয়। এটি পারফরম্যান্স বাড়ায়, বিশেষ করে ভারী ফাংশনের ক্ষেত্রে।

উদাহরণ:

```
function memoize(fn) {
  const cache = {};
  return function(...args) {
    const key = JSON.stringify(args);
    if(cache[key]) {
      return cache[key];
    } else {
      const result = fn(...args);
      cache[key] = result;
      return result;
    }
  }
}

const slowFunction = (num) => {
  // ভারী কাজের সিমুলেশন
  for(let i = 0; i < 1e9; i++) {}
  return num * 2;
}

const fastFunction = memoize(slowFunction);

console.log(fastFunction(10)); // প্রথমবার: সময় সাপেক্ষ
console.log(fastFunction(10)); // দ্বিতীয়বার: ক্যাশ থেকে তাড়াতাড়ি
```

## ৩৮. `Tail Call Optimization` কী?

উত্তর: Tail Call Optimization (TCO) হল একটি অপ্টিমাইজেশন যেখানে রিকার্সিভ ফাংশনের শেষ কলটি অপ্টিমাইজ করে স্ট্যাক ওভারফ্লো প্রতিরোধ করা হয়। এটি শুধুমাত্র কিছু ভাষায় এবং ইঞ্জিনে সমর্থিত।

উদাহরণ:

```
function factorial(n, acc = 1) {
  if(n <= 1) return acc;
  return factorial(n - 1, n * acc); // Tail call
}

console.log(factorial(5)); // 120
```

## ৩৯. `Event Loop` কী এবং এটি কীভাবে কাজ করে?

উত্তর: Event Loop হল জাভাস্ক্রিপ্টের একটি মেকানিজম যা সিঙ্গেল থ্রেডেড ভাষার মধ্যে অ্যাসিঙ্ক্রোনাস অপারেশন হ্যান্ডল করে। এটি কলব্যাক কিউ এবং মাইক্রোটাস্ক কিউয়ের মাধ্যমে কাজ করে, এবং স্ট্যাক ফ্রি হলে কলব্যাকগুলো এক্সিকিউট করে।

উদাহরণ:

```
console.log('Start');

setTimeout(() => {
  console.log('Timeout');
}, 0);

Promise.resolve().then(() => {
  console.log('Promise');
});

console.log('End');

// Output:
// Start
// End
// Promise
// Timeout
```

## ৪০. `Immutable.js` কী এবং কেন এটি ব্যবহৃত হয়?

উত্তর: Immutable.js হল একটি লাইব্রেরি যা ইমিউটেবল ডেটা স্ট্রাকচার প্রদান করে, যেমন ইমিউটেবল লিস্ট, ম্যাপ, সেট ইত্যাদি। এটি ডেটা ম্যানিপুলেশনে নিরাপত্তা এবং পারফরম্যান্স বৃদ্ধি করে, বিশেষ করে রিয়েক্টের সাথে ব্যবহৃত হয়।

উদাহরণ:

```
const { Map } = require('immutable');

const original = Map({ name: 'Alice', age: 25 });
const updated = original.set('age', 26);

console.log(original.get('age')); // 25
console.log(updated.get('age'));  // 26
```

## ৪১. Higher-Order Functions কী? উদাহরণ সহ ব্যাখ্যা করুন।

উত্তর: Higher-Order Functions হল সেই ধরনের ফাংশন যা অন্য ফাংশনকে আর্গুমেন্ট হিসেবে গ্রহণ করে অথবা ফাংশনকে রিটার্ন করে। এটি ফাংশনাল প্রোগ্রামিং এর একটি গুরুত্বপূর্ণ ধারণা।

উদাহরণ:

```
// Map
const map = new Map();
const obj = {};
map.set(obj, 'value');
console.log(map.get(obj)); // 'value'

// WeakMap
const weakMap = new WeakMap();
weakMap.set(obj, 'value');
console.log(weakMap.get(obj)); // 'value'
```

## ৪২. `State Management` কী এবং কেন এটি গুরুত্বপূর্ণ?

উত্তর: State Management হল অ্যাপ্লিকেশনের স্টেট (ডেটা) পরিচালনার পদ্ধতি। এটি গুরুত্বপূর্ণ কারণ বড় অ্যাপ্লিকেশনগুলিতে বিভিন্ন কম্পোনেন্টের মধ্যে স্টেট শেয়ার এবং ম্যানেজ করা কঠিন হতে পারে।

কেন গুরুত্বপূর্ণ:

- সহজ স্টেট ট্র্যাকিং: স্টেট পরিবর্তনগুলো সহজে ট্র্যাক করা যায়।
- কম্পোনেন্টের মধ্যে ডেটা শেয়ারিং: বিভিন্ন কম্পোনেন্টের মধ্যে ডেটা সহজে শেয়ার করা যায়।
- Predictable State Updates: স্টেট আপডেটগুলো পূর্বানুমানযোগ্য হয়।

উদাহরণ: React এর ক্ষেত্রে Redux ব্যবহার:

```
// Action
const increment = () => ({ type: 'INCREMENT' });

// Reducer
function counter(state = 0, action) {
  switch(action.type) {
    case 'INCREMENT':
      return state + 1;
    default:
      return state;
  }
}

// Store
import { createStore } from 'redux';
const store = createStore(counter);

// Subscribe
store.subscribe(() => console.log(store.getState()));

// Dispatch
store.dispatch(increment()); // 1
store.dispatch(increment()); // 2
```
