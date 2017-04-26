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
```
function innerFunc () {
    console.log("inner!");
}

function outerFunc (callback) { // This is a function definition
    return callback;
}

// Not executed until called inside outerFunc
outerFunc(innerFunc);
```

---

## Further Example
```
function getInterests(name){
    $fake.ajaxCall(name)
}

function showUserInfo(firstName, lastName, interests, callback){
    let fullName = `${firstName} ${lastName}`;
    getInterests (fullName)
}

printUserInfo('Jason', 'Land', )
```


---