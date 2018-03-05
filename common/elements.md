# ELEMENTS

> ALTERNATIVES: [bonzo](https://github.com/ded/bonzo) [$dom](https://github.com/julienw/dollardom)

## Add Class

```js
// jQuery
$(el).addClass(className);

// IE8+
if (el.classList)
  el.classList.add(className);
else
  el.className += ' ' + className;
```

## After

```js
// jQuery
$(el).after(htmlString);

// IE8+
el.insertAdjacentHTML('afterend', htmlString);
```

## Append

```js
// jQuery
$(parent).append(el);

// IE8+
parent.appendChild(el);
```

## Before

```js
// jQuery
$(el).before(htmlString);

// IE8+
el.insertAdjacentHTML('beforebegin', htmlString);
```

## Children

```js
// jQuery
$(el).children();

// IE9+
el.children
```

## Clone

```js
// jQuery
$(el).clone();

// IE8+
el.cloneNode(true);
```

## Contains

```js
// jQuery
$.contains(el, child);

// IE8+
el !== child && el.contains(child);
```

## Contains Selector

```js
// jQuery
$(el).find(selector).length;

// IE8+
el.querySelector(selector) !== null
```

## Each

```js
// jQuery
$(selector).each(function(i, el){

});

// IE9+
var elements = document.querySelectorAll(selector);
Array.prototype.forEach.call(elements, function(el, i){

});
```

## Empty

```js
// jQuery
$(el).empty();

// IE9+
el.innerHTML = '';
```

## Filter

```js
// jQuery
$(selector).filter(filterFn);

// IE9+
Array.prototype.filter.call(document.querySelectorAll(selector), filterFn);
```

## Find Children

```js
// jQuery
$(el).find(selector);

// IE8+
el.querySelectorAll(selector);
```

## Find Elements

> ALTERNATIVES: [qwery](https://github.com/ded/qwery) [sizzle](http://sizzlejs.com/)

```js
// jQuery
$('.my #awesome selector');

// IE8+
document.querySelectorAll('.my #awesome selector');
```

## Get Attributes

```js
// jQuery
$(el).attr('tabindex');

// IE8+
el.getAttribute('tabindex');
```

## Get Html

```js
// jQuery
$(el).html();

// IE8+
el.innerHTML
```

## Get Outer Html

```js
// jQuery
$('<div>').append($(el).clone()).html();

// IE8+
el.outerHTML
```

## Get Style

```js
// jQuery
$(el).css(ruleName);

// IE9+
getComputedStyle(el)[ruleName];
```

## Get Text

```js
// jQuery
$(el).text();

// IE9+
el.textContent
```

## Has Class

```js
// jQuery
$(el).hasClass(className);

// IE8+
if (el.classList)
  el.classList.contains(className);
else
  new RegExp('(^| )' + className + '( |$)', 'gi').test(el.className);
```

## Matches

```js
// jQuery
$(el).is($(otherEl));

// IE8+
el === otherEl
```

## Matches Selector

```js
// jQuery
$(el).is('.my-class');

// IE9+
var matches = function(el, selector) {
  return (el.matches || el.matchesSelector || el.msMatchesSelector || el.mozMatchesSelector || el.webkitMatchesSelector || el.oMatchesSelector).call(el, selector);
};

matches(el, '.my-class');
```

## Next

```js
// jQuery
$(el).next();

// IE9+
el.nextElementSibling
```

## Offset

```js
// jQuery
$(el).offset();

// IE8+
var rect = el.getBoundingClientRect();

{
  top: rect.top + document.body.scrollTop,
  left: rect.left + document.body.scrollLeft
}
```

## Offset Parent

```js
// jQuery
$(el).offsetParent();

// IE8+
el.offsetParent || el
```

## Outer Height

```js
// jQuery
$(el).outerHeight();

// IE8+
el.offsetHeight
```

## Outer Height With Margin

```js
// jQuery
$(el).outerHeight(true);

// IE9+
function outerHeight(el) {
  var height = el.offsetHeight;
  var style = getComputedStyle(el);

  height += parseInt(style.marginTop) + parseInt(style.marginBottom);
  return height;
}

outerHeight(el);
```

## Outer Width

```js
// jQuery
$(el).outerWidth();

// IE8+
el.offsetWidth
```

## Outer Width With Margin

```js
// jQuery
$(el).outerWidth(true);

// IE9+
function outerWidth(el) {
  var width = el.offsetWidth;
  var style = getComputedStyle(el);

  width += parseInt(style.marginLeft) + parseInt(style.marginRight);
  return width;
}

outerWidth(el);
```

## Parent

```js
// jQuery
$(el).parent();

// IE8+
el.parentNode
```

## Position

```js
// jQuery
$(el).position();

// IE8+
{
  left: el.offsetLeft,
  top: el.offsetTop
}
```

## Position Relative To Viewport

```js
// jQuery
var offset = el.offset();

{
  top: offset.top - document.body.scrollTop,
  left: offset.left - document.body.scrollLeft
}

// IE8+
el.getBoundingClientRect()
```

## Prepend

```js
// jQuery
$(parent).prepend(el);

// IE8+
parent.insertBefore(el, parent.firstChild);
```

## Prev

```js
// jQuery
$(el).prev();

// IE9+
el.previousElementSibling
```

## Remove

```js
// jQuery
$(el).remove();

// IE8+
el.parentNode.removeChild(el);
```

## Remove Class

```js
// jQuery
$(el).removeClass(className);

// IE8+
if (el.classList)
  el.classList.remove(className);
else
  el.className = el.className.replace(new RegExp('(^|\\b)' + className.split(' ').join('|') + '(\\b|$)', 'gi'), ' ');
```

## Replace From Html

```js
// jQuery
$(el).replaceWith(string);

// IE8+
el.outerHTML = string;
```

## Set Attributes

```js
// jQuery
$(el).attr('tabindex', 3);

// IE8+
el.setAttribute('tabindex', 3);
```

## Set Html

```js
// jQuery
$(el).html(string);

// IE8+
el.innerHTML = string;
```

## Set Style

```js
// jQuery
$(el).css('border-width', '20px');

// IE8+
// Use a class if possible
el.style.borderWidth = '20px';
```

## Set Text

```js
// jQuery
$(el).text(string);

// IE9+
el.textContent = string;
```

## Siblings

```js
// jQuery
$(el).siblings();

// IE9+
Array.prototype.filter.call(el.parentNode.children, function(child){
  return child !== el;
});
```

## Toggle Class

```js
// jQuery
$(el).toggleClass(className);

// IE9+
if (el.classList) {
  el.classList.toggle(className);
} else {
  var classes = el.className.split(' ');
  var existingIndex = classes.indexOf(className);

  if (existingIndex >= 0)
    classes.splice(existingIndex, 1);
  else
    classes.push(className);

  el.className = classes.join(' ');
}
```
