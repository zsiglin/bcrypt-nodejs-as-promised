## Basic Usage

hashing:
```javascript
    bcrypt.hash('my password', 10)
      .then(console.log, console.error)
```

comparing:
(note that an invalid password/hash combo errors as a rejected promise)
```javascript
    bcrypt.compare('my password', someHash)
      .then(console.log, console.error)
```

The rejection can be checked against `instanceof bcrypt.MISMATCH_ERROR`

```js
bcrypt.compare('invalid password', someHash)
  .then(handleValidPassword)
  .catch(bcrypt.MISMATCH_ERROR, handleInvalidPassword)
  .catch(handleOtherErrors);
```

generating a salt:
```javascript
    bcrypt.genSalt(10)
      .then(console.log, console.error)
```

calculating the rounds used in a salt:
```javascript
    bcrypt.getRounds(someHash)
      .then(console.log, console.error)
```
