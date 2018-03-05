# EVENTS

## Off

```js
// jQuery
$(el).off(eventName, eventHandler);

// IE9+
el.removeEventListener(eventName, eventHandler);
```

## On

```js
// jQuery
$(el).on(eventName, eventHandler);

// IE9+
el.addEventListener(eventName, eventHandler);
```

## Ready

```js
// jQuery
$(document).ready(function(){

});

// IE9+
function ready(fn) {
  if (document.readyState != 'loading'){
    fn();
  } else {
    document.addEventListener('DOMContentLoaded', fn);
  }
}
```

## Trigger Custom

> ALTERNATIVES: [EventEmitter](https://github.com/Wolfy87/EventEmitter) [Vine](https://github.com/arextar/Vine) [microevent](https://github.com/jeromeetienne/microevent.js)

```js
// jQuery
$(el).trigger('my-event', {some: 'data'});

// IE9+
if (window.CustomEvent) {
  var event = new CustomEvent('my-event', {detail: {some: 'data'}});
} else {
  var event = document.createEvent('CustomEvent');
  event.initCustomEvent('my-event', true, true, {some: 'data'});
}

el.dispatchEvent(event);
```

## Trigger Native

```js
// jQuery
$(el).trigger('change');

// IE9+
// For a full list of event types: https://developer.mozilla.org/en-US/docs/Web/API/document.createEvent
var event = document.createEvent('HTMLEvents');
event.initEvent('change', true, false);
el.dispatchEvent(event);
```
