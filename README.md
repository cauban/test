# Test Algo

Tests que j'ai eus (aleatoires): Nombres premiers, compter le nombre de mots dans une string, dire si un mot est un anagramme ex jean et neja.

Control flows, stack (un array en last in first out avec methodes push, pop), [map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) le mec que j'ai eu vient de Java il va te dire que tu ne peux pas mettre des trucs dynamiquement sur un objet et que tu dois utiliser une map avec get, set..

## Nombres premiers:

Un nombre est premier s'il est divisible seulement par 1 et par lui meme.

```js
function isEven(x) {
  return x % 2 === 0;
}

function listPrimes(x) {
  let primes = [];

  // 1 n'est pas premier car 1 n'est pas distinct de lui meme
  for (let i = 2; i <= x; i++) {
    if (isPrime(i)) {
      primes.push(i);
    }
  }

  return primes;
}

function isPrime(x) {
  // 2 est premier car divisible seulement par 1 et 2
  if (x === 2) return true;

  // les nombres pairs sont divisibles par 2 donc forcement non premiers
  if (isEven(x)) {
    return false;
  }

  // jusqu'a x non inclus, si x est divisible par un nombre quelqu'il soit
  // alors il n'est pas premier
  // on peut opti en allant seulement jusqu'a la racine carree de x mais je laisse la version naive
  for (let i = 3; i < x; i++) {
    if (x % i === 0) {
      return false;
    }
  }

  // sinon il est premier
  return true;
}
```


# Test React

Todolist avec une api

Fetch, setState, preventDefault, onChange...

# Test JS

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
x === x // false - NaN n'est jamais egal a lui meme
```

```js
~~3.14 // 3 - operateur binaire, bonus
```

```js
(42).toString(16) // "2a" - bonus, 42 base 16
42..toString(16) // "2a" - bonus, .. permet a l'interpreteur de comprendre que 42. est un nombre et que le second point appelle l'objet
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

## Arrays

```js
typeof [] // "object"

const list = [1,2,3];

list.length // 3

list[0] // 1

list.slice(-1) // [3] - does not mutate list, splice does

const same = list;
same.push(4)
list // [1,2,3,4];
```

## Objects

```js
typeof {} // "object"
```

```js
const movie = {
  director: "Tsui Hark",
  title: "Time & Tide",
  get rating () {
    return 10;
  }
}

const strange = movie;
strange.title = "Ebola Syndrome";

movie.title // "Ebola Syndrome"
```

## Functions

Une fonction est un object qui a une propriete "call".

```js
typeof function() {} // "function"
```

```js
// function declaration
function add(x, y) { 
  return x + y;
}

// function expression
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

```js
const A = { foo() { return 'foo' }};
const B = Object.create(A); // cree un objet dont le prototype sera l'objet A
B.foo() // "foo" - foo n'existe pas sur B, on remonte la chaine prototypale et on trouve foo

B.hasOwnProperty("foo") // false
B.__proto__ // A
```

```js
function Person(firstname, lastname) {
  this.firstname = firstname;
  this.lastname = lastname;
};

Person.prototype.fullname = function fullname() {
  return this.firstname + " " + this.lastname;
}

const me = new Person("sun", "tzu"); // 

me.fullname() // "sun tzu"
```

## This

`this` est la valeur du contexte. La valeur de `this` est dynamique.

```js
this // Dans le browser renvoie l'objet Window
```

```js
'use strict';

this // undefined - en strict mode le contexte par defaut est undefined
```

```js
const me = {
  firstname: "sun",
  lastname: "tzu",
  fullname() {
    return this.firstname + " " + this.lastname;
  }
}

me.fullname() // "sun tzu" - this est l'objet me qui vient avant le point

const you = { 
  firstname: "wesley", 
  lastname: "snipes"
 };
 
you.fullname = me.fullname;

you.fullname() // "wesley snipes" - this est l'objet you qui vient avant le point

me.fullname.call({name: "tony", lastname: "soprano"}) // "tony soprano", call permet de setter le this
me.fullname.apply({name: "tony", lastname: "soprano"}) // "tony soprano", apply permet de setter le this

you.fullname = you.fullname.bind(me) // cree une fonction ou le this vaudra me
you.fullname() // "sun tzu"
```

Si il n'y a pas de point devant l'appel alors la fonction utilise le contexte global.

Rappel:
```js
function add(x, y) {
  return x + y;
}

add.call(null, 2, 3) // 5
add.apply(null, [2, 3]) // 5
```
Memotechnique, Apply commence par un A donc il prend un Array.

## Scopes

`var` est scope globalement ou a la fonction.
```js
var one = 1;

function () {
  one // 1

  var two = 2;
}

two // undefined

{
  var three = 3;
}

three // 3
```

`let` est scope au block
```js
let one = 1;

function () {
  one // 1
  let two = 2;
}

two // undefined

{
  let three = 3
}

three // undefined
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

Sans mot cle, la valeur est accessible dans le contexte global.
```js
function() {
  one = 1;
}
one // 1
```

### Hoisting

Les declarations sont remontees en haut du scope. On peut donc referencer une variable avant qu'elle ait une valeur assignee.

```js
var a; // declaration
a = 1; // assignment
```

Le code suivant:
```js
a // undefined

var a = 1;
```
Est traduit:
```js
var a; // declaration of var a
a // undefined
a = 1 // assignment
```

Le code suivant utilise une function declaration:
```js
foo() // "hello"

function foo() { 
  return "hello"; 
}
```

Celui ci utilise une function expression:
```js
foo() // TypeError foo is not a function (let foo; foo est undefined a ce moment la)

let foo = function () {};

```

## Control flows

### Switch

```js
const fruit = "apple";

function logName(fruit) {
  switch(fruit) {
    case "orange":
      log("orange");
      break;
    case("apple"):
      log("apple");
    default:
      log("bullshit")
  }
}

logName(fruit) // apple bullshit - default case is logged because we forgot to break in apple case so everything under is evaluated
```

### For loop

Sur le for loop ils ont une question ou le code est incomprehensible. L'important est de retenir l'ordre d'execution pour pouvoir determiner l'ordre des logs.

```js
for(i = 0; i < 5; i++) { // 0 1 2 3 4
  console.log(i);
}
```

+ On declare i a 0; 
+ 0 est inferieur a 5
+ On logge i; // 0
+ i++ // i vaut 1
+ 1 est inferieur a 5
+ On logge i // 1 ...

```js
for(i = 0; i < 5; i++) { // 0 1 2 3 4
  setTimeout(() => console.log(i)); // 5 5 5 5 5
}
```

+ On declare i a 0; 
+ 0 est inferieur a 5
+ On setTimeout
+ i++ // i vaut 1
+ 1 est inferieur a 5
+ On setTimeout ...

Une fois que la boucle est finie les console.log se lancent, i vaut 5 comme c'est une valeur globale. 

Pour logger 0 1 2 3 4 il faut ecrire `for(let i = 0`



