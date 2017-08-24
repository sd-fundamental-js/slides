---
theme: black
revealOptions:
    transition: 'fade'
---

# Prototypes

---

## Dictionary Definition of "Prototype"

A preliminary model of something, from which other forms are developed or copied.

---

## A Javascript definition of "Prototype"

A prototype is another object that is used as a fallback source of properties. When an object gets a request for a property that it **does not have**, its prototype will be searched for the property, then the prototype’s prototype, and so on until it's found or `undefined` is returned.

---

## Why is this Important?

- It can help you define patterns that can be reused
- To save on memory; it's only created once and each object refers up the prototype chain

---

```
Vehicle Class

```
---

## Nota Bene

- `prototype` is a reserved word.
- All objects have a prototype
- All instances of a prototype will have the methods and properties set on it up the chain

---

## Further Reading

https://medium.com/javascript-scene/master-the-javascript-interview-what-s-the-difference-between-class-prototypal-inheritance-e4cd0a7562e9