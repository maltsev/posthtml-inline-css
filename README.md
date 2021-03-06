# posthtml-inline-css [![npm version](https://badge.fury.io/js/posthtml-inline-css.svg)](http://badge.fury.io/js/posthtml-inline-css) [![Build Status](https://travis-ci.org/posthtml/posthtml-inline-css.svg?branch=master)](https://travis-ci.org/posthtml/posthtml-inline-css)

[PostHTML](https://github.com/posthtml/posthtml) plugin for inlining CSS to style attrs.

Many modern email clients nowadays support CSS in a `<style>`, so you might not need to inline CSS.
See [that discussion](https://github.com/posthtml/posthtml-inline-css/issues/14).

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


### &lt;style&gt;
```js
var posthtml = require('posthtml'),
    html = '<style>div { color: red }</style><div>Hello!</div>';

posthtml([require('posthtml-inline-css')()])
    .process(html)
    .then(function (result) {
        console.log(result.html);
    });

// <style>div { color: red }</style><div style="color: red">Hello!</div>
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
