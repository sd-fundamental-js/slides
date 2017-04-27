---
theme: beige
revealOptions:
    transition: 'fade'
---

# Fundamental JS

Callbacks and Where to Call Them

---

## Why do I need a Callback?

Or in other words:

So you want to do a thing after a thing

---

## Recap on Javascript functions

They can be:
* Stored in variables
* passed as arguments to other functions
* created inside of other functions
* returned from inside of functions

---

## What is a Callback?

A Javascript callback is when a function is passed as an argument to another function and is then run (or "called") inside.

---

## What does it look like?

```
// Common Jquery implementation
$("#btn_1").click(function() {
  alert("Btn 1 Clicked");
});

// This is the same:
$("#btn_1").click(alertMe);

function alertMe(){
  alert("Btn 1 Clicked");
}
```

---

## Nota Bene
- It's not called immediately

```
function innerFunc () {
    console.log("inner!");
}

function outerFunc (callback) { // This is a function definition
    //some other stuff happens
    callback();
}

// Not executed until called inside outerFunc
outerFunc(innerFunc);
```

---

## Callback === Function

- It's just a function
- It can do all of the things a function can do
- All callbacks are closures
- Pass parameters to them

---

## Pass Parameters

```
function description(name, interests){
    console.log(`${name} has many interests`);
    console.log('These include ${interests[0]}');
}

function printUserInfo(firstName, lastName, callback){
    let fullName = `${firstName} ${lastName}`;
    let returnArray = $fake.Ajax.Call;
    description (fullName, returnArray)
}

printUserInfo('Jason', 'Land', description)
```


---

## What's this?

- The `this` context gets lost inside of a callback

```
​var user = {
    fullName: "Not Set",
    setUserName: function (firstName, lastName)  {
      this.fullName = `${firstName} ${lastName}`;
    }
}
​
​function getUser(firstName, lastName, callback)  {
    callback (firstName, lastName);
}

getUser("Jason", "Land", user.setUserName)
console.log (user.fullName); // returns "Not Set"
```

---

## Apply preserves `this`

Using the `apply` method
 ```
function getUser(first, last, callback, userObj)  {
    callback.apply(userObj, [first, last]);
}

getUser("Jason", "Land", user.setUserName, user)
 ```

`Apply` requires the object who's `this` context needs to be bound, and then an array of arguments to be passed

---

## Quick hacks preserve `this`

- `let that = this`

OR

-  `let self = this`

---

## Callback Hell

```
getData(function(a){
    thenAuthenticate(a, function(b){
        thenSaveToSession(b, function(c){
            Alertuser(c, function(d){
                etc(d, function(e){
                    ...
                });
            });
        });
    });
});
```

---

## Keep your program shallow

```
getData(thenAuthenticate)

function thenAuthenticate(a, thenSaveToSession){
    // do stuff with `a`
    thenSaveToSession(a)
}

function thenSaveToSession(b, Alertuser){
    // do stuff with `b`
    Alertuser(b)
}

function Alertuser(c){
    alert(c)
}
```

---

## Use Promises

```
getData()
.then(function(a){
    thenAuthenticate(a)
})
.then(function(b){
    thenSaveToSession(b)
})
.then(function(c){
    alertuser(c)
})
.then(function(d){
    console.log("Not in hell!")
})
```

---