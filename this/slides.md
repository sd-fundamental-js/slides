---
theme: beige
revealOptions:
    transition: 'fade'
---

# Fundamental JS


---

## I am Javascript and What is this?

What does this get you?

```
console.log(this);
```

<p class="fragment">The `Window` Object</p>
<p class="fragment">In other instances, it depends on where `this` is called</p>

---

## What is the name for these different circumstances?

<span class="fragment">Context</span>

---

# 1. The Global Object

```
console.log(this);
```

---

## What about this?

```
function test() {
  return this;
}

test();
```

<p class="fragment">The `Window` Object again</p>
<p class="fragment">It's not in a declared object, so it defaults to Window</p>

---

# 2. Declared Object

```
var person = {
  first: 'John',
  last: 'Smith',  
  full: function() {
    console.log(this.first + ' ' + this.last);
  }
};

person.full();
```

<p class="fragment">// logs => 'John Smith'</p>

---

## Double this
```
var person = {
  first: 'John',
  last: 'Smith',
  full: function() {
    console.log(this.first + ' ' + this.last);
  },
  personTwo: {
    first: 'Allison',
    last: 'Jones',
    full: function() {
      console.log(this.first + ' ' + this.last);
    }
  }
};
```

---

```
person.full();
person.personTwo.full();
```

<pre class="fragment">
// logs => 'John Smith'
// logs => 'Allison Jones'
</pre>


---

# 3. New Objects

```
function Car(make, model) {
  this.make = make;
  this.model = model;
};

var myCar = Car('Ford', 'Escape');
console.log(myCar);
```

<pre class="fragment">
// logs => undefined
</pre>

---

```js
var myCar = new Car('Ford', 'Escape');
```

<pre class="fragment">
// logs => Car {make: "Ford", model: "Escape"}
</pre>

---

# 4. Call, Bind, Apply
- Methods available to all function (except arrow functions)
- They allow you to explicitly change `this` at runtime

---

## Call

- Invoked immediately
- two paramenters:
    - this
    - arguments

---

## Apply

- Invoked immediately
- two paramenters:
    - this
    - an array of arguments

---

## Obvious, right?

---

## Example

```
function add(c, d) {
  console.log(this.a + this.b + c + d);
}

add(3,4);
// logs => NaN
```

---

## Continued

```
function add(c, d) {
  console.log(this.a + this.b + c + d);
}

var ten = {a: 1, b: 2};

add.call(ten, 3, 4);
// logs => 10

add.apply(ten, [3,4]);
// logs => 10
```

---

## Bind

- Not invoked immediately
- Returns a function with the context of this already bound

---

# 5. Arrow Functions

- Almost like they don't have a `this`
- `this` is lexically scoped
- They use the context of the scope they were declared in
- Behind the scenes:
```
let that = this
```

---
