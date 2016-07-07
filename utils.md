# UTILS

## Bind

```js
// jQuery
$.proxy(fn, context);

// IE9+
fn.bind(context);
```

## Array Each

```js
// jQuery
$.each(array, function(i, item){

});

// IE9+
array.forEach(function(item, i){

});
```

## Deep Extend

```js
// jQuery
$.extend(true, {}, objA, objB);

// IE8+
var deepExtend = function(out) {
  out = out || {};

  for (var i = 1; i < arguments.length; i++) {
    var obj = arguments[i];

    if (!obj)
      continue;

    for (var key in obj) {
      if (obj.hasOwnProperty(key)) {
        if (typeof obj[key] === 'object')
          out[key] = deepExtend(out[key], obj[key]);
        else
          out[key] = obj[key];
      }
    }
  }

  return out;
};

deepExtend({}, objA, objB);
```

## Extend

> ALTERNATIVES: [lo-dash](http://lodash.com/docs#assign) [underscore](http://underscorejs.org/#extend) [ECMA6](http://www.2ality.com/2014/01/object-assign.html)

```js
// jQuery
$.extend({}, objA, objB);

// IE8+
var extend = function(out) {
  out = out || {};

  for (var i = 1; i < arguments.length; i++) {
    if (!arguments[i])
      continue;

    for (var key in arguments[i]) {
      if (arguments[i].hasOwnProperty(key))
        out[key] = arguments[i][key];
    }
  }

  return out;
};

extend({}, objA, objB);
```

## Index Of

```js
// jQuery
$.inArray(item, array);

// IE9+
array.indexOf(item);
```

## Is Array

```js
// jQuery
$.isArray(arr);

// IE9+
Array.isArray(arr);
```

## Map

```js
// jQuery
$.map(array, function(value, index){

});

// IE9+
array.map(function(value, index){

});
```

## Now

```js
// jQuery
$.now();

// IE9+
Date.now();
```

## Parse Html

```js
// jQuery
$.parseHTML(htmlString);

// IE9+
var parseHTML = function(str) {
  var tmp = document.implementation.createHTMLDocument();
  tmp.body.innerHTML = str;
  return tmp.body.children;
};

parseHTML(htmlString);
```

## Parse Json

```js
// jQuery
$.parseJSON(string);

// IE8+
JSON.parse(string);
```

## Trim

```js
// jQuery
$.trim(string);

// IE9+
string.trim();
```

## Type

```js
// jQuery
$.type(obj);

// IE8+
Object.prototype.toString.call(obj).replace(/^\[object (.+)\]$/, '$1').toLowerCase();
```
