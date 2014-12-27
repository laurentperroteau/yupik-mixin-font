Yupik Mixin Font
================

### Mixins that simplified fonts declarations

> Is part of [Yupik collection of modules](https://github.com/laurentperroteau/yupik)

Work in all browser (using REM with optional pixel fallback).

Install using Bower:

    $ bower install --save yupik-mixin-font


Requirement : 
-------------
````scss
html {
    font-size: 62.5%; // allows 1em == 10px
}
````


Exemple : 
---------

"font-size" mixin display font-size in pixel (optional) and REM:
````scss
.font-size {
    @include font-size(15)
}
````

Easily create your own mixins for each type of font by copying this mixin:
````scss 
@mixin sans-italic($param: null) {

    // Set your parameters
    $fontFamily: 'Open Sans', sans-serif;
    $fontStyle : italic;
    $fontWeight: 600;
    
    @include construct-font-mixin($fontFamily, $param, $fontStyle, $fontWeight);
}

// Use: first param called "font-size" mixin and second param "line-height" mixin
.class {
    @include sans-italic(15 17);
}
````

Result:
````css
.class {
  font-family: "Open Sans", sans-serif;
  font-style: italic;
  font-weight: 600;
  font-size: 15px;
  font-size: 1.5rem;
  line-height: 17px;
  line-height: 1.7rem;
}
````

It's recommended use placeholders:
````scss
%font-15 { @include font-size(15) }

%sans-italic { @include sans-italic }
````

Disabled pixel if you don't need:
````scss
$yupik-fallback-rem: false;
````