# Animate Helper

[![npm version](https://badge.fury.io/js/animate-helper.svg)](https://badge.fury.io/js/animate-helper)
[![DragsterJS gzip size](http://img.badgesize.io/https://raw.githubusercontent.com/fluidweb-co/animate-helper/master/dist/animate-helper.min.js?compression=gzip
)](https://raw.githubusercontent.com/fluidweb-co/animate-helper/master/dist/animate-helper.min.js)

Provide functions to handle animations and transitions gracefully. Execute a function before or after playing a css animation on an element.



## Installation

Setting up is pretty straight-forward. Just download the script from __dist__ folder and include it in your HTML:

```html
<script type="text/javascript" src="path/to/dist/animate-helper.min.js"></script>
```

### NPM

Animate Helper is also available on NPM:

```sh
$ npm install animate-helper
```



## Basic Usage

### 1. Execute a function BEFORE playing a css animation

Call the function `AnimateHelper.doThenAnimate( element, animationClass, callbackFn );` passing the parameters:
- `element`: The element to which the animation class will be added and the animation played on
- `animationClass`: The class name for the animation which should have the css property `animation:` set to a css keyframe animation definition.
- `callbackFn`: The function to execute before the animation is played, accepts the parameters `element` and `animationClass`.

```js
// Set element open then play openning animation
AnimateHelper.doThenAnimate( document.querySelector( '.flyout-menu' ), 'slide-up', function( element, animationClass ) {
    element.style.display = 'block';
    document.body.classList.add( 'flyout-menu--open' );
} );
```

### 2. Execute a function AFTER playing a css animation

Call the function `AnimateHelper.animateThenDo( element, animationClass, callbackFn );` passing the parameters:
- `element`: The element to which the animation class will be added and the animation played on
- `animationClass`: The class name for the animation which should have the css property `animation:` set to a css keyframe animation definition.
- `callbackFn`: The function to execute after the animation is played (`animationend` event), accepts the parameters `element` and `animationClass`.

```js
// Play closing animation then set element hidden
AnimateHelper.animateThenDo( document.querySelector( '.flyout-menu' ), 'slide-down', function( element, animationClass ) {
    element.style.display = 'none';
    document.body.classList.remove( 'flyout-menu--open' );
} );
```



## Contributing to Development

This isn't a large project by any means, but you are definitely welcome to contribute.

### Development environment

Clone the repo and run [npm](http://npmjs.org/) install:

```
$ cd path/to/animate-helper
$ npm install
```

Run the build command:

```
$ gulp build
```

Build on file save:

```
$ gulp
$ gulp watch
```


## License

Licensed under MIT.
