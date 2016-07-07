# AJAX

> ALTERNATIVES: [reqwest](https://github.com/ded/Reqwest) [then-request](https://github.com/then/request) [superagent](https://github.com/visionmedia/superagent)

## JSON

```js
// jQuery
$.getJSON('/my/url', function(data) {

});


// IE9+
var request = new XMLHttpRequest();
request.open('GET', '/my/url', true);

request.onload = function() {
  if (request.status >= 200 && request.status < 400) {
    // Success!
    var data = JSON.parse(request.responseText);
  } else {
    // We reached our target server, but it returned an error

  }
};

request.onerror = function() {
  // There was a connection error of some sort
};

request.send();
```

## Post

```js
// jQuery
$.ajax({
  type: 'POST',
  url: '/my/url',
  data: data
});

// IE8+
var request = new XMLHttpRequest();
request.open('POST', '/my/url', true);
request.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded; charset=UTF-8');
request.send(data);
```

## Request

```js
// jQuery
$.ajax({
  type: 'GET',
  url: '/my/url',
  success: function(resp) {

  },
  error: function() {

  }
});

// IE9+
var request = new XMLHttpRequest();
request.open('GET', '/my/url', true);

request.onload = function() {
  if (request.status >= 200 && request.status < 400) {
    // Success!
    var resp = request.responseText;
  } else {
    // We reached our target server, but it returned an error

  }
};

request.onerror = function() {
  // There was a connection error of some sort
};

request.send();
```
