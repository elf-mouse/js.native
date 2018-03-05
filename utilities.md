## Utilities

Most of jQuery utilities are also found in the native API. Other advanced functions could be chosen from better utilities libraries, focusing on consistency and performance. [Lodash](https://lodash.com) is a recommended replacement.

- [6.1](#6.1) <a name='6.1'></a> Basic utilities

  + isArray

  Determine whether the argument is an array.

  ```js
  // jQuery
  $.isArray(array);

  // Native
  Array.isArray(array);
  ```

  + isWindow

  Determine whether the argument is a window.

  ```js
  // jQuery
  $.isWindow(obj);

  // Native
  function isWindow(obj) {
    return obj !== null && obj !== undefined && obj === obj.window;
  }
  ```

  + inArray

  Search for a specified value within an array and return its index (or -1 if not found).

  ```js
  // jQuery
  $.inArray(item, array);

  // Native
  array.indexOf(item) > -1;

  // ES6-way
  array.includes(item);
  ```

  + isNumeric

  Determine if the argument passed is numerical.
  Use `typeof` to decide the type or the `type` example for better accuracy.

  ```js
  // jQuery
  $.isNumeric(item);

  // Native
  function isNumeric(value) {
    return !isNaN(parseFloat(n)) && isFinite(n);
  }
  ```

  + isFunction

  Determine if the argument passed is a JavaScript function object.

  ```js
  // jQuery
  $.isFunction(item);

  // Native
  function isFunction(item) {
    if (typeof item === 'function') {
      return true;
    }
    var type = Object.prototype.toString(item);
    return type === '[object Function]' || type === '[object GeneratorFunction]';
  }
  ```

  + isEmptyObject

  Check to see if an object is empty (contains no enumerable properties).

  ```js
  // jQuery
  $.isEmptyObject(obj);

  // Native
  function isEmptyObject(obj) {
    return Object.keys(obj).length === 0;
  }
  ```

  + isPlainObject

  Check to see if an object is a plain object (created using “{}” or “new Object”).

  ```js
  // jQuery
  $.isPlainObject(obj);

  // Native
  function isPlainObject(obj) {
    if (typeof (obj) !== 'object' || obj.nodeType || obj !== null && obj !== undefined && obj === obj.window) {
      return false;
    }

    if (obj.constructor &&
        !Object.prototype.hasOwnProperty.call(obj.constructor.prototype, 'isPrototypeOf')) {
      return false;
    }

    return true;
  }
  ```

  + extend

  Merge the contents of two or more objects together into a new object, without modifying either argument.
  object.assign is part of ES6 API, and you could also use a [polyfill](https://github.com/ljharb/object.assign).

  ```js
  // jQuery
  $.extend({}, object1, object2);

  // Native
  Object.assign({}, object1, object2);
  ```

  + trim

  Remove the white-space from the beginning and end of a string.

  ```js
  // jQuery
  $.trim(string);

  // Native
  string.trim();
  ```

  + map

  Translate all items in an array or object to new array of items.

  ```js
  // jQuery
  $.map(array, (value, index) => {
  });

  // Native
  array.map((value, index) => {
  });
  ```

  + each

  A generic iterator function, which can be used to seamlessly iterate over both objects and arrays.

  ```js
  // jQuery
  $.each(array, (index, value) => {
  });

  // Native
  array.forEach((value, index) => {
  });
  ```

  + grep

  Finds the elements of an array which satisfy a filter function.

  ```js
  // jQuery
  $.grep(array, (value, index) => {
  });

  // Native
  array.filter((value, index) => {
  });
  ```

  + type

  Determine the internal JavaScript [Class] of an object.

  ```js
  // jQuery
  $.type(obj);

  // Native
  function type(item) {
    const reTypeOf = /(?:^\[object\s(.*?)\]$)/;
    return Object.prototype.toString.call(item)
      .replace(reTypeOf, '$1')
      .toLowerCase();
  }
  ```

  + merge

  Merge the contents of two arrays together into the first array.

  ```js
  // jQuery
  $.merge(array1, array2);

  // Native
  // But concat function doesn't remove duplicate items.
  function merge(...args) {
    return [].concat(...args)
  }

  // ES6-way, doesn't remove duplicate items.
  array1 = [...array1, ...array2]

  // Set version, can remove duplicate items
  function merge(...args) {
    return Array.from(new Set([].concat(...args)))
  }
  ```

  + now

  Return a number representing the current time.

  ```js
  // jQuery
  $.now();

  // Native
  Date.now();
  ```

  + proxy

  Takes a function and returns a new one that will always have a particular context.

  ```js
  // jQuery
  $.proxy(fn, context);

  // Native
  fn.bind(context);
  ```

  + makeArray

  Convert an array-like object into a true JavaScript array.

  ```js
  // jQuery
  $.makeArray(arrayLike);

  // Native
  Array.prototype.slice.call(arrayLike);

  // ES6-way
  Array.from(arrayLike);
  ```

- [6.2](#6.2) <a name='6.2'></a> Contains

  Check to see if a DOM element is a descendant of another DOM element.

  ```js
  // jQuery
  $.contains(el, child);

  // Native
  el !== child && el.contains(child);
  ```

- [6.3](#6.3) <a name='6.3'></a> Globaleval

  Execute some JavaScript code globally.

  ```js
  // jQuery
  $.globaleval(code);

  // Native
  function Globaleval(code) {
    const script = document.createElement('script');
    script.text = code;

    document.head.appendChild(script).parentNode.removeChild(script);
  }

  // Use eval, but context of eval is current, context of $.Globaleval is global.
  eval(code);
  ```

- [6.4](#6.4) <a name='6.4'></a> parse

  + parseHTML

  Parses a string into an array of DOM nodes.

  ```js
  // jQuery
  $.parseHTML(htmlString);

  // Native
  function parseHTML(string) {
    const context = document.implementation.createHTMLDocument();

    // Set the base href for the created document so any parsed elements with URLs
    // are based on the document's URL
    const base = context.createElement('base');
    base.href = document.location.href;
    context.head.appendChild(base);

    context.body.innerHTML = string;
    return context.body.children;
  }
  ```

  + parseJSON

  Takes a well-formed JSON string and returns the resulting JavaScript value.

  ```js
  // jQuery
  $.parseJSON(str);

  // Native
  JSON.parse(str);
  ```
