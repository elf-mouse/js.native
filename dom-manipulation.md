## DOM Manipulation

- [3.1](#3.1) <a name='3.1'></a> Remove

  Remove the element from the DOM.

  ```js
  // jQuery
  $el.remove();

  // Native
  el.parentNode.removeChild(el);
  ```

- [3.2](#3.2) <a name='3.2'></a> Text

  + Get text

    Get the combined text contents of the element including their descendants,

    ```js
    // jQuery
    $el.text();

    // Native
    el.textContent;
    ```

  + Set text

    Set the content of the element to the specified text.

    ```js
    // jQuery
    $el.text(string);

    // Native
    el.textContent = string;
    ```

- [3.3](#3.3) <a name='3.3'></a> HTML

  + Get HTML

    ```js
    // jQuery
    $el.html();

    // Native
    el.innerHTML;
    ```

  + Set HTML

    ```js
    // jQuery
    $el.html(htmlString);

    // Native
    el.innerHTML = htmlString;
    ```

- [3.4](#3.4) <a name='3.4'></a> Append

  Append child element after the last child of parent element

  ```js
  // jQuery
  $el.append('<div id="container">Hello World</div>');

  // Native (HTML string)
  el.insertAdjacentHTML('beforeend', '<div id="container">Hello World</div>');

  // Native (Element)
  el.appendChild(newEl);
  ```

- [3.5](#3.5) <a name='3.5'></a> Prepend

  ```js
  // jQuery
  $el.prepend('<div id="container">Hello World</div>');

  // Native (HTML string)
  el.insertAdjacentHTML('afterbegin', '<div id="container">Hello World</div>');

  // Native (Element)
  el.insertBefore(newEl, el.firstChild);
  ```

- [3.6](#3.6) <a name='3.6'></a> insertBefore

  Insert a new node before the selected elements

  ```js
  // jQuery
  $newEl.insertBefore(selector);

  // Native (HTML string)
  el.insertAdjacentHTML('beforebegin ', '<div id="container">Hello World</div>');

  // Native (Element)
  const el = document.querySelector(selector);
  if (el.parentNode) {
    el.parentNode.insertBefore(newEl, el);
  }
  ```

- [3.7](#3.7) <a name='3.7'></a> insertAfter

  Insert a new node after the selected elements

  ```js
  // jQuery
  $newEl.insertAfter(selector);

  // Native (HTML string)
  el.insertAdjacentHTML('afterend', '<div id="container">Hello World</div>');

  // Native (Element)
  const el = document.querySelector(selector);
  if (el.parentNode) {
    el.parentNode.insertBefore(newEl, el.nextSibling);
  }
  ```

- [3.8](#3.8) <a name='3.8'></a> is

  Return `true` if it matches the query selector

  ```js
  // jQuery - Notice `is` also works with a function, an existing jQuery object or a DOM element, which are not of concern here
  $el.is(selector);

  // Native
  el.matches(selector);
  ```
- [3.9](#3.9) <a name='3.9'></a> clone

  Create a deep copy of an element: it copies the matched element as well as all of its descendant elements and text nodes.

  ```js
  // jQuery. Sets parameter as `true` to indicate that event handlers should be copied along with the element.
  $el.clone();

  // Native
  el.cloneNode();

  ```

- [3.10](#3.10) <a name='3.10'></a> empty

  Remove all child nodes

  ```js
  // jQuery
  $el.empty();

  // Native
  el.innerHTML = '';
  ```

- [3.11](#3.11) <a name='3.11'></a> wrap

  Wrap an HTML structure around each element

  ```js
  // jQuery
  $('.inner').wrap('<div class="wrapper"></div>');

  // Native
  Array.prototype.forEach.call(document.querySelectorAll('.inner'), (el) => {
    const wrapper = document.createElement('div');
    wrapper.className = 'wrapper';
    el.parentNode.insertBefore(wrapper, el);
    el.parentNode.removeChild(el);
    wrapper.appendChild(el);
  });
  ```

- [3.12](#3.12) <a name='3.12'></a> unwrap

  Remove the parents of the set of matched elements from the DOM

  ```js
  // jQuery
  $('.inner').unwrap();

  // Native
  Array.prototype.forEach.call(document.querySelectorAll('.inner'), (el) => {
    let elParentNode = el.parentNode;

    if(elParentNode !== document.body) {
        elParentNode.parentNode.insertBefore(el, elParentNode);
        elParentNode.parentNode.removeChild(elParentNode);
    }
  });
  ```

- [3.13](#3.13) <a name='3.13'></a> replaceWith

  Replace each element in the set of matched elements with the provided new content

  ```js
  // jQuery
  $('.inner').replaceWith('<div class="outer"></div>');

  // Native
  Array.prototype.forEach.call(document.querySelectorAll('.inner'), (el) => {
    const outer = document.createElement('div');
    outer.className = 'outer';
    el.parentNode.insertBefore(outer, el);
    el.parentNode.removeChild(el);
  });
  ```

- [3.14](#3.14) <a name='3.14'></a> simple parse

  Parse a string into HTML/SVG/XML

  ```js
  // jQuery
  $(`<ol>
    <li>a</li>
    <li>b</li>
  </ol>
  <ol>
    <li>c</li>
    <li>d</li>
  </ol>`);

  // Native
  range = document.createRange();
  parse = range.createContextualFragment.bind(range);

  parse(`<ol>
    <li>a</li>
    <li>b</li>
  </ol>
  <ol>
    <li>c</li>
    <li>d</li>
  </ol>`);
  ```
