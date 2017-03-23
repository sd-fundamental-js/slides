---
theme: beige
revealOptions:
    transition: 'fade'
---

# Fundamental JS

The Anatomy of a XMLHttpRequest

---

## Why do I need a XMLHttpRequest?

Or in other words:

So you want to get data from a server

---

```
                 ------                    ------
                |client| <====(data)====> |server|
                 ------                    ------
```

* Get Data from an API
* Authenticate (Register/Login)

---

## How do I do this magic?

---

## Information Overload

<pre
    style="font-size:18px;
    background-color: black;
    color: white;
    padding: 1rem;"
>
const request = new XMLHttpRequest();

request.open("GET", "http://omdbapi.com/?s=Star%20Wars", false);

request.onreadystatechange = function(){
    if (request.readyState === request.DONE) {
        if (request.status === 200) {
            console.log(request.response);
            console.log(request.responseText);
        }
    }
};

request.send(params);
</pre>

---

## A Little At A Time

First we need to declare a variable to hold the request object

<pre
    style="font-size:18px;
    background-color: black;
    color: white;
    padding: 1rem;"
>
const request = new XMLHttpRequest();
<span style="color:midnightblue;">
request.open("GET", "http://omdbapi.com/?s=Star%20Wars", false);

request.onreadystatechange = function(){
    if (request.readyState === request.DONE) {
        if (request.status === 200) {
            console.log(request.response);
            console.log(request.responseText);
        }
    }
};

request.send(params);
</span>
</pre>

---

We're *opening* a connection
* `"GET"` is the method we're connecting with
    - `"POST"`,`"PUT"`,`"DELETE"` are other methods

<pre
    style="font-size:18px;
    background-color: black;
    color: white;
    padding: 1rem;"
>
<span style="color:midnightblue;">
const request = new XMLHttpRequest();
</span>
request.open("GET", "http://omdbapi.com/?s=Star%20Wars", false);
<span style="color:midnightblue;">
request.onreadystatechange = function(){
    if (request.readyState === request.DONE) {
        if (request.status === 200) {
            console.log(request.response);
            console.log(request.responseText);
        }
    }
};

request.send(params);
</span>
</pre>

---

* The URL after "GET" is the destination the data is coming from / going to
* 'false' is whether or not the request is **asynchronous**

<pre
    style="font-size:18px;
    background-color: black;
    color: white;
    padding: 1rem;"
>
<span style="color:midnightblue;">
const request = new XMLHttpRequest();
</span>
request.open("GET", "http://omdbapi.com/?s=Star%20Wars", false);
<span style="color:midnightblue;">
request.onreadystatechange = function(){
    if (request.readyState === request.DONE) {
        if (request.status === 200) {
            console.log(request.response);
            console.log(request.responseText);
        }
    }
};

request.send(params);
</span>
</pre>

---

This is the **callback** that will happen once the response comes back.

Checking for the response is best practices

<pre
    style="font-size:18px;
    background-color: black;
    color: white;
    padding: 1rem;"
>
<span style="color:midnightblue;">
const request = new XMLHttpRequest();

request.open("GET", "http://omdbapi.com/?s=Star%20Wars", false);
</span> 
request.onreadystatechange = function(){
    if (request.readyState === request.DONE) {
        if (request.status === 200) {
            console.log(request.response);
            console.log(request.responseText);
        }
    }
};

<span style="color:midnightblue;">

request.send(params);
</span>
</pre>

---

## Send off the **request**.

* The **params** variable is if you need to send email, password, form data, etc

<pre
    style="font-size:18px;
    background-color: black;
    color: white;
    padding: 1rem;"
>
const params = {
    email: 'me@mail.com',
    password: 'lololol'
}

request.send(params);

</pre>

---

## Live Example
<iframe height='1024px' scrolling='no' title='jBxwdy' src='//codepen.io/wishinghand/embed/jBxwdy/?height=265&theme-id=0&default-tab=result&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/wishinghand/pen/jBxwdy/'>jBxwdy</a> by Jason Land (<a href='http://codepen.io/wishinghand'>@wishinghand</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>