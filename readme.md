# JavaScript Style Guide (Best Practices)
> How to write maintainable JavaScript applications.

*To start using these guidelines in your project, see [Quick Start](#quick-start).*

## Rules

1. Be consistent
2. `use strict`
3. Use semicolons
4. Strict equality (`!==` in favor of `!=`)
5. Do not extend native object prototypes
6. Space after keywords and between arguments and operators
7. Let your code document itself. Comments can often be avoided by employing better naming conventions
8. Favor using existing libraries over re-inventing functionality

Have a reason if you're going to stray from the following recommendations.

## Recommendations

1. 2 space indentation
2. Single-quotes
3. Camelcase
4. No trailing whitespace
5. Multiple variable statements
6. Return early
7. Favor function declarations (`function hi() {}`) over function expressions (`var hi = function () {};`)

## Examples
```js
'use strict';

// Favor function declarations over function expressions
function sayHi(name) {
  // Return early.
  if (!name) {
    return; 
  }
  
  // Multiple variable statements
  // Camelcase
  // Single-quotes
  // Space after keywords and between arguments and operators
  var greeting = 'Hey, ' + name;
  var isStephen = name === 'Stephen';
  var seven = 4 + 3;
  
  alert(greeting); // Unspoken rule: don't use `alert`
}
```

### Comments
```js
// Ok.
function removeTodo(todo) {
  var record = todo.getModel(); // Grab the model from the todo item.
  todo.find('.destroy').click(); // Trigger a click to remove the element from the <ul>.
  record.remove(); // Removes the todo model from localStorage.
}

// Better.
function removeTodo(todo) {
  // Grab the model from the todo item.
  var record = todo.getModel();

  // Trigger a click to remove the element from the <ul>.
  todo.find('.destroy').click();

  // Removes the todo model from localStorage.
  record.remove();
}

// Best.
function removeTodo(todoItemElement) {
  // Trigger a click to remove the element from the <ul>.
  todoItemElement.find('.destroy').click();
  
  todoItemElement.getModel().remove();
}
```

### AngularJS
*See [Best Practice Recommendations for Angular App Structure](https://docs.google.com/document/d/1XXMvReO8-Awi1EZXAXS4PzDzdNvV6pGcuaF4Q9821Es/pub)*.

```js
angular
  .module('app')
  .config(function (dependency) {
    // Code here.
  });
```

### RequireJS / Modules
```js
define('Block', [
  'jQuery',
  'Handlebars'
], function ($, Handlebars) {
  'use strict';

  // Code here.
});
```

## Tooling

Rules and guidelines will easily be broken if the proper tooling isn't in place to validate your JavaScript. Included with this repository are configuration files for three popular, well-supported tools that will make sure your rules are honored.

- `.editorconfig` - [EditorConfig](http://editorconfig.org)
- `.jshintrc` - [JSHint](http://www.jshint.com)
- `.jscsrc` - [JavaScript Code Style checker](https://github.com/mdevils/node-jscs)

It is worth the investment of your time to explore these tools, and integrate them into your editor and build process.

## Quick Start

Start using this configuration right away with Yeoman by installing the [Javascript Style Generator](https://github.com/stephenplusplus/generator-javascript-style).

```sh
$ npm install -g generator-javascript-style

# cd to your project directory
$ yo javascript-style

Extracting stephenplusplus/javascript-style...
Done!

[?] Which direction shall we go? (Use arrow keys)
❯ Install npm dependencies (jscs, jshint)
  --------
  Visit stephenplusplus/javascript-style
  Visit EditorConfig.org
  Visit JSHint.com
  Visit JavaScript Code Style Checker
  Visit idiomatic.js
```

## Resources
- [idiomatic.js](https://github.com/rwaldron/idiomatic.js)
- [TasteJS TodoMVC Code Style](https://github.com/tastejs/todomvc/blob/gh-pages/codestyle.md)
