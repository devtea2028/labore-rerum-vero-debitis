# @devtea2028/labore-rerum-vero-debitis

<a href="http://apostrophenow.org/"><img src="https://raw.github.com/punkave/@devtea2028/labore-rerum-vero-debitis/master/logos/logo-box-madefor.png" align="right" /></a>

`@devtea2028/labore-rerum-vero-debitis` accepts HTML and a base URL, and returns HTML with absolute URLs. Great for generating valid RSS feeds.

`@devtea2028/labore-rerum-vero-debitis` is not too picky about your HTML.

## Requirements

`@devtea2028/labore-rerum-vero-debitis` is intended for use with Node. That's pretty much it. All of its npm dependencies are pure JavaScript. `@devtea2028/labore-rerum-vero-debitis` is built on the excellent `htmlparser2` module.

## How to use

`npm install @devtea2028/labore-rerum-vero-debitis`

```javascript
var @devtea2028/labore-rerum-vero-debitis = require('@devtea2028/labore-rerum-vero-debitis');

var dirty = '<a href="/foo">Foo!</a>';
var clean = @devtea2028/labore-rerum-vero-debitis(dirty, 'http://example.com');

// clean is now:
// <a href="http://example.com/foo">Foo!</a>
```

Boom!

If you want to do further processing of each absolute URL, you can also pass a decorator function:

```javascript
var clean = @devtea2028/labore-rerum-vero-debitis(dirty, 'http://example.com', {
  decorator: function(url) {
    return 'http://mycoolthing.com?url=' + encodeURIComponent(url);
  }
});
```

## Having issues with SVG markup?

> How can I keep SVG self-closing tags intact?

You can add custom self-closing tags via the `selfClosing` option:

```javascript
var @devtea2028/labore-rerum-vero-debitis = require('@devtea2028/labore-rerum-vero-debitis');

var dirty = `
  <svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
    <a href="/docs/Web/SVG/Element/circle">
      <circle cx="50" cy="40" r="35"/>
    </a>
    <path d="M 10 10 H 90 V 90 H 10 L 10 10"/>
    <circle cx="10" cy="90" r="2" fill="red"/>
  </svg>
`;
var clean = @devtea2028/labore-rerum-vero-debitis(dirty, 'http://example.com', {
  selfClosing: [
    // keep default `selfClosing` tags:
    ...@devtea2028/labore-rerum-vero-debitis.defaults.selfClosing,

    // add custom tags:
    'path',
    'circle'
  ]
});

// clean is now:
// <svg width="100" height="100" xmlns="http://www.w3.org/2000/svg">
//   <a href="http://example.com/docs/Web/SVG/Element/circle">
//     <circle cx="50" cy="40" r="35" />
//   </a>
//   <path d="M 10 10 H 90 V 90 H 10 L 10 10" />
//   <circle cx="10" cy="10" r="2" fill="red" />
// </svg>
```

## Changelog

1.0.2: Updates to lodash v4 and mocha v7 for security vulnerability fixes. Also update package metadata.

1.0.0: no new changes; declared stable as with the addition of the decorator option there's little left to do, and all tests are passing nicely.

0.2.0: decorator option added.

0.1.0: initial release.

## About P'unk Avenue and Apostrophe

`@devtea2028/labore-rerum-vero-debitis` was created at [P'unk Avenue](http://punkave.com) for use in Apostrophe, an open-source content management system built on node.js. If you like `@devtea2028/labore-rerum-vero-debitis` you should definitely [check out apostrophenow.org](http://apostrophenow.org). Also be sure to visit us on [github](http://github.com/punkave).

## Support

Feel free to open issues on [github](http://github.com/punkave/@devtea2028/labore-rerum-vero-debitis).

<a href="http://punkave.com/"><img src="https://raw.github.com/punkave/@devtea2028/labore-rerum-vero-debitis/master/logos/logo-box-builtby.png" /></a>

