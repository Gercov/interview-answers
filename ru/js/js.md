# Вопросы и ответы касательно JS

### В чем разница между null и undefined?

> Для начала давайте поговорим о том, что у них общего.

- Во-первых, они принадлежат к 7 «примитивам» (примитивным типам) JS:

```js
const primitiveTypes = ['string', 'number', 'null', 'undefined', 'boolean', 'symbol', 'bigint']
```

- Во-вторых, они являются ложными значениями, т.е. результатом их преобразования в логическое значение с помощью `Boolean()` или оператора `!!` является `false`:

```js
console.log(!!null) // false
console.log(!!undefined) // false

console.log(Boolean(null)) // false
console.log(Boolean(undefined)) // false
```

> Ладно, теперь о различиях.

`undefined («неопределенный»)` представляет собой значение по умолчанию:

- переменной, которой не было присвоено значения, т.е. объявленной, но не инициализированной переменной
- функции, которая ничего не возвращает явно, например, console.log(1)
- несуществующего свойства объекта

> В указанных случаях движок JS присваивает значение undefined:

```js
const _thisIsUndefined;
const doNothing = () => {};
const someObj = {
  a: 'ay',
  b: 'bee',
  c: 'si'
};

console.log(_thisIsUndefined) // undefined
console.log(doNothing()) // undefined
console.log(someObj['d']) // undefined
```

> `null — это «значение отсутствия значения»`. null — это значение, которое присваивается переменной явно. В примере ниже мы получаем null, когда метод `fs.readFile` отрабатывает без ошибок:

```js
fs.readFile('path/to/file', (error, data) => {
  console.log(error) // здесь мы получаем null

  if (error) {
    console.log(error)
  }

  console.log(data)
})
```

> При сравнении null и undefined мы получаем true, когда используем оператор `== (нестрогое равенство)`, и false при использовании оператора `=== (строгое равенство)`

```js
console.log(null == undefined) // true
console.log(null === undefined) // false
```
