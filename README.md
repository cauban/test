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

```js
"1" + 1 // "11"
[] + 1 // "1" - empty array coerced into an empty string
undefined + 1 // NaN
false + 1 // 0 - false coerced to zero
```

## Objects

## Functions

## Booleans

## Prototypes

## This

## Scopes
