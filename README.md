Automatic dependency import for Angular & RequireJS projects. Described here: [Solving quadruple dependency injection problem](http://blog.rogach.org/2016/02/solving-quadruple-dependency-injection.html).

Essenitally, it allows to transform this:

```js
// answer.js
define(["angular"], function() {
  angular.module("the.answer")
    .value("TheAnswer", 42);
});

// main.js
define(["angular", "the.answer"], function() {
  angular.module("main", ["the.answer"])
    .run(["TheAnswer", function(TheAnswer) {
      console.log(TheAnswer);
    }]);
});
```

into this:

```js
// answer.js
angular.module("the.answer")
  .value("TheAnswer", 42);

// main.js
angular.module("main")
  .run(function(TheAnswer) {
    console.log(TheAnswer);
  });
```

using awesome [recast](https://github.com/benjamn/recast) library for JavaScript AST parsing and manipulation.

Dependencies
------------
```
npm install recast underscore
```
