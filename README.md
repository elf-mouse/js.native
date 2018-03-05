## You Don't Need jQuery

Frontend environments evolve rapidly nowadays and modern browsers have already implemented a great deal of DOM/BOM APIs which are good enough for production use. We don't have to learn jQuery from scratch for DOM manipulation or event handling. In the meantime, thanks to the spread of frontend libraries such as React, Angular and Vue, manipulating the DOM directly becomes anti-pattern, so that jQuery usage has never been less important. This project summarizes most of the alternatives in native Javascript implementation to jQuery methods, with IE 10+ support.

## Browser Support

![Chrome][chrome-image] | ![Firefox][firefox-image] | ![IE][ie-image] | ![Opera][opera-image] | ![Safari][safari-image]
--- | --- | --- | --- | --- |
Latest ✔ | Latest ✔ | 10+ ✔ | Latest ✔ | 6.1+ ✔ |

## Table of Contents

1. [Query Selector](query-selector.md)
2. [CSS & Style](css--style.md)
3. [DOM Manipulation](dom-manipulation.md)
4. [Ajax](ajax.md)
5. [Events](events.md)
6. [Utilities](utilities.md)
7. [Promises](promises.md)
8. [Animation](animation.md)

## Alternatives

* [You Might Not Need jQuery](http://youmightnotneedjquery.com/) - Examples of how to do common event, element, ajax etc with plain javascript.
* [npm-dom](http://github.com/npm-dom) and [webmodules](http://github.com/webmodules) - Organizations you can find individual DOM modules on NPM

[chrome-image]: https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png
[firefox-image]: https://raw.github.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png
[ie-image]: https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png
[opera-image]: https://raw.github.com/alrra/browser-logos/master/src/opera/opera_48x48.png
[safari-image]: https://raw.github.com/alrra/browser-logos/master/src/safari/safari_48x48.png
