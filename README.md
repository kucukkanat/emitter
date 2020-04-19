# HackDonald's Emitter

## Table of Contents

-   [Install](#install)
-   [Usage](#usage)
-   [Examples & Demos](#examples--demos)
-   [API](#api)
-   [Contribute](#contribute)
-   [License](#license)

## Install

This project uses [node](http://nodejs.org) and [npm](https://npmjs.com). Go check them out if you don't have them locally installed.

```sh
$ npm install --save @hackdonalds/emitter
```


```javascript
// using ES6 modules
import Emitter from '@hackdonalds/emitter'

// using CommonJS modules
var Emitter = require('@hackdonals/emitter').default
```

The [UMD](https://github.com/umdjs/umd) build is also available on [unpkg](https://unpkg.com/@hackdonalds/emitter@0.5.1/dist/index.js):

```html
<script src="https://unpkg.com/@hackdonalds/emitter@0.5.1/dist/index.js"></script>
```

You can find the library on `window.HackDonalds.Emitter`.

## Usage

```js
import Emitter from '@hackdonalds/emitter'
// OR
const Emitter = require('@hackdonalds/emitter').default

const emitter = new Emitter()

// listen to an event
emitter.on('foo', e => console.log('foo', e) )

// listen to all events
emitter.on('*', (type, e) => console.log(type, e) )

// fire an event
emitter.emit('foo', { a: 'b' })

// working with handler references:
function onFoo() {}
emitter.on('foo', onFoo)   // listen
emitter.off('foo', onFoo)  // unlisten
```

## Typescript

For better autocompletion Emitter class takes parameters for possible event names : 

```js
import Emitter from '@hackdonalds/emitter'
const emitter = new Emitter<'foo' | 'bar'>()
emitter.on('foo', e => console.log('foo', e) )
emitter.on('bar', e => console.log('foo', e) )
// Will throw an error:
emitter.on('bar2', e => console.log('foo', e) )
```

* * *

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Emitter


**Parameters**

-   `all` **EventHandlerMap** 

Returns **Mitt** 

### on

Register an event handler for the given type.

**Parameters**

-   `type` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Type of event to listen for, or `"*"` for all events
-   `handler` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** Function to call in response to given event

### off

Remove an event handler for the given type.

**Parameters**

-   `type` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Type of event to unregister `handler` from, or `"*"`
-   `handler` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** Handler function to remove

### emit

Invoke all handlers for the given type.
If present, `"*"` handlers are invoked after type-matched handlers.

_Note: Manually firing "*" handlers is not supported._

**Parameters**

-   `type` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The event type to invoke
-   `evt` **Any?** Any value (object is recommended and powerful), passed to each handler


### Reporting Issues

Found a problem? Want a new feature? First of all see if your issue or idea has [already been reported](../../issues).
If don't, just open a [new clear and descriptive issue](../../issues/new).


## License

[MIT License](https://opensource.org/licenses/MIT) © [Hilmi Tolga SAHIN](https://kucukkanat.com/)