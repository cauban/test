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

1 + 1 // 2

1 + 2 * 3 // 7 simple maths

const x = NaN;
x !== x // true - NaN n'est jamais egal a lui meme
```

## Strings

```js
typeof 'hello' // "string"

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

1 == '1' // true - loose equality
1 === '1' // false - strict equality
```

## Objects

```js
typeof ({}) // "object"
```

## Functions

Une fonction est un object qui a une propriete "call".

```js
typeof function() {} // "function"

function add(x, y) {
  return x + y;
}

const add = (x, y) => x + y;
```

## Booleans

## Prototypes

## This

## Scopes
