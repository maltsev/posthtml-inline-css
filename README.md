# PostHTML CSS Inliner
[![npm version](https://badge.fury.io/js/posthtml-inline-css.svg)](http://badge.fury.io/js/posthtml-inline-css)

[PostHTML](https://github.com/posthtml/posthtml) plugin for inlining CSS to style attrs

## Usage
### Plain CSS
```js
var posthtml = require('posthtml'),
    css = 'div { color: red }';

posthtml([require('posthtml-inline-css')(css)])
    .process('<div style="font-size: 14px">Hello!</div>')
    .then(function (result) {
        console.log(result.html);
    });

// <div style="font-size: 14px; color: red">Hello!</div>
```

### PostCSS
```js
var posthtml = require('posthtml'),
    postcss = require('postcss'),
    postcssObj = postcss(/* some PostCSS plugins */).process('div { color: white }');


posthtml([require('posthtml-inline-css')(postcssObj)])
    .process('<div style="font-size: 14px">Hello!</div>')
    .then(function (result) {
        console.log(result.html);
    });

// <div style="font-size: 14px; color: white">Hello!</div>
```
