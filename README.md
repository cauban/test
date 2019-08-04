## Tests

```js
it('adds two numbers', () => {
  expect(1 + 1).toBe(2); // pass
})
```

`typeof` retourne une string

## Numbers 

```js
typeof 1 // "number"
```

```js
1 + 1 // 2

1 + 2 * 3 // 7 simple maths
```

```js
const x = NaN;
x !== x // true - NaN n'est jamais egal a lui meme
```

```js
~~3.14 // 3 - operateur binaire, bonus
```

## Strings

```js
typeof 'hello' // "string"
```

```js
const name = "jean";
"hello" + name // "hellojean" - concatenation
`hello ${name}` // "hello jean" - template string
```

## Coercion

La coercion, c'est le JS qui fait son maximum en convertissant un type vers un autre. Il suit la spec pour determiner la conversion selon des scenarios.

```js
"1" + 1 // "11"
[] + 1 // "1" - empty array coerced into an empty string
undefined + 1 // NaN
false + 1 // 1 - false coerced to zero
```

```js
1 == '1' // true - loose equality
1 === '1' // false - strict equality
```

## Objects

```js
typeof {} // "object"
```

## Functions

Une fonction est un object qui a une propriete "call".

```js
typeof function() {} // "function"
```

```js
function add(x, y) {
  return x + y;
}

const add = (x, y) => x + y;
```

## Booleans

```js
typeof true // "boolean"
```

Les valeurs suivantes sont falsy:
+ `undefined`
+ `null`
+ `0`
+ `NaN`
+ `false`
+ `""`

`{}` et `[]` sont truthy

```js
true && false // false
true || false // true
true && (false || true) // true
```

## Prototypes

## This

## Scopes

`var` est scope globalement ou a la fonction.
```js
var one = 1;

function () {
  one // 1

  var two = 2;
}

two // undefined
one = 'one' // ok

{
  var three = 3;
}

three // 3
```

`let` est scope au block
```js
let one = 1;
{
  one // 1
  let two = 2;
}
two // undefined
one = 'one' // ok
```

`const` est scope au block, la difference est qu'on ne peut pas rebind sa valeur
```js
const one = 1;
{
  one // 1
  const two = 2;
}
two // undefined
one = 'one' // TypeError assignment to constant variable
```
