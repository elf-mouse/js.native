# EFFECTS

> ALTERNATIVES: [animate.css](http://daneden.github.io/animate.css/) [move.js](https://github.com/visionmedia/move.js)

## Fade In

```js
// jQuery
$(el).fadeIn();

// IE9+
function fadeIn(el) {
  el.style.opacity = 0;

  var last = +new Date();
  var tick = function() {
    el.style.opacity = +el.style.opacity + (new Date() - last) / 400;
    last = +new Date();

    if (+el.style.opacity < 1) {
      (window.requestAnimationFrame && requestAnimationFrame(tick)) || setTimeout(tick, 16);
    }
  };

  tick();
}

fadeIn(el);
```

## Hide

```js
// jQuery
$(el).hide();

// IE8+
el.style.display = 'none';
```

## Show

```js
// jQuery
$(el).show();

// IE8+
el.style.display = '';
```
