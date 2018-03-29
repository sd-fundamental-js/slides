---
theme: sky
---

# Fundamental JS

Bind & Trick Questions

---

Ohhhh I would do anything for scope, but I won’t do that = `this`

— Jake Archibald

---

## What is this now?

All javascript functions have access to an implicit argument `this`. By default, this refers to the global window object, but when a function is bound to an object as a method, this refers to the object.

---

## Example Time

```
var myObj = {
    specialFunction: function () {
    },

    getAsyncData: function (cb) {
        cb();
    },

    render: function () {
        var that = this;
        this.getAsyncData(function () {
            that.specialFunction();
        });
    }
};

myObj.render() //TypeError: this.specialFunction is not a function
```

---

## How do I get `specialFunction`?

```
render: function () {
    this.getAsyncData(function () {
        this.specialFunction();
        this.anotherSpecialFunction();
    }.bind(this));
}
```

---

## What's going on?

.bind() creates a new function that has its `this` keyword set to the provided value.

---

## Syntax

`fun.bind(thisArg[, arg1[, arg2[, ...]]])`

#### thisArg

The value to be passed as the this parameter to the target function when the bound function is called.

#### arg1, arg2, ...

Arguments to prepend to arguments provided to the bound function when invoking the target function.

---

## Another Example

```
this.x = 9; // this === global "window" object in the browser
var module = {
  x: 81,
  getX: function() { return this.x; }
};

module.getX(); // 81
```

---

```
class App extends React.Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this); // bound early
  }

  handleClick(event, value) {
    // do stuff with value ("foo" or "baz")
  }

  render() {
    return (
      <div>
        <button onClick={this.handleClick.bind("foo")} /> // incorrect code
        <button onClick={this.handleClick.bind("bar")} /> // incorrect code
      </div>
    )
  }
}
```

