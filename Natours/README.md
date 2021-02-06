##### The best way to perform a basic reset using the universal selector:

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

##### How to set project-wide font definitions and selection style:

```css
body {
  font-family: "Lato", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.7;
  color: #777777;
}

::selection {
  background-color: green;
  color: white;
}
```

##### How to clip parts of elements using `clip-path`:

```css
.header {
  height: 95vh;
  background-image: linear-gradient(
    to right bottom,
    rgba(126, 213, 111, 0.801),
    rgba(40, 180, 133, 0.801)),
    url(../img/hero.jpg);
  background-size: cover;
  background-position: top;
  position: relative;
  -webkit-clip-path: polygon(0 0, 100% 0, 100% 75vh, 0 100%);
  clip-path: polygon(0 0, 100% 0, 100% 75vh, 0 100%)
}
```

##### The easiest way to center anything with the `transform` `top` and `left` properties:

```css
.text-box {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

##### How to create CSS animations using `@keyframes` and the `animation` property:

```css
.heading-primary-main {
  animation-name: moveInLeft;
  animation-duration: 1s;
  animation-timing-function: ease-out;
}

@keyframes moveInLeft{
  0% {
    opacity: 0;
    transform: translateX(-100px);
  }

  80% {
    transform: translateX(20px);
  }

  100% {
    opacity: 1;
    transform: translate(0);
  }
}
```

##### What pseudo-elements and pseudo-classes are:

```html
<a href="#" class="btn btn-white">Discover our tours</a>
```

```css
.btn:link,
.btn:visited {
    text-transform:
}
```

Pseudo-classes are a special state of a selector. Similar to hover, the link and visited are a special state of the .btn selector. Since the default styling for anchor tags is blue and a visited anchor tag purple is something that we don't want, we can override it and make the unvisited and visited links look the same using comma.

Pseudo-elements allow us to style certain parts of elements.

##### How and why to use the `::after` pseudo-element:

The `::after` pseudo element adds a virtual element right after the selected element.

```css
.btn::after{
  content: "";
  display:inline-block;
  height: 100%;
  width: 100%;
  border-radius: 100px;
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  transition: all .4s;
}
```

##### How to create a creative hover animation effect using the `transition` property:

```css
.btn::after {
    ...
    transition: all .4s;
}

.btn:hover::after {
  transform: scaleX(1.4) scaleY(1.6);
  opacity: 0;
}

.btn-animated {
  animation-name: moveInBottom;
  animation-duration: 0.5s;
  animation-timing-function: ease-out;
  animation-delay: 0.75s;
  animation-fill-mode: backwards;
}
```

##### How and why to use `rem` units in our project:

It is easier to change all measurements on the page when rem is used, for example when a breakpoint is reached. A great starting point is to set the root font-size to 10px, so that **1 rem = 10px**. Using rem is much preferable for a responsive design rather than hard-coding px's.

```css
html {
  font-size: 10px;
}
```

Setting the font-size to pixels however is a bad idea for accessibility reasons (poor eyesight, etc.). A better alternative is to use percentage. A simple solution is if we want 10 px, we can just divide 10 by 16 (default font size).

```css
html {
  font-size: 62.5%;
}
```

##### A great workflow for converting px to rem:

As in the previous example, since we used a font-size of 10px (or 62.5% of the default 16), 1 rem would be equal to 10px. This makes converting all the px to rem much easier and precise.

```css
body {
  padding: 30px;
}
```

into

```css
body {
  padding: 3rem;
}
```

##### Nesting in scss:

[Sass variables and nesting](https://codepen.io/demiglace0505/pen/YzpPLyQ)

```scss
.navigation {
  list-style: none;
  
  li {
    display: inline-block;
    margin-left: 30px;
    
    &:first-child {
      margin:0px;
    }
  }
}
```

[Mixins, Extends and Functions](https://codepen.io/demiglace0505/pen/XWNJqgX)

##### Compiling sass:

```
npm run node-sass sass/main.scss css/style.css -w
```

##### 7-1 folder architecture

```
sass
|_ main.scss
|_base/
  |_ _animations.scss
  |_ _base.scss
  |_ _typography.scss
  |_ _utilities.scss
|_components/
  |_ _button.scss
|_layout/
  |_ _header.scss
|_pages/
  |_ _home.scss
|_themes/  -> dark theme etc.
|_abstracts/
  |_ _functions.scss
  |_ _mixins.scss
  |_ _variables.scss
|_vendors/   -> third party css
```

##### clearfix mixin

```
@mixin clearfix {
  &::after {
    content: "";
    display: table;
    clear: both;
  }
}
```

##### How the attribute selector works:

To select all elements with an attribute of class that starts with `col-`:

```scss
[class^="col-"]
```

^- starts with

$- ends with

*- contains

##### `background-clip` property to make a gradient text:

```
  background-image: linear-gradient(to right, $color-primary-light, $color-primary-dark);
  display: inline-block;
  -webkit-background-clip: text;
  color: transparent;
```

##### How to include and use an icon font:

[linea.io](linea.io)

Copy icon-font.css and _ICONFONT folder to css folder of project. Then add to html head.

```html
<link rel="stylesheet" href="css/icon-font.css">
```

To use:

```html
<i class="feature-box__icon icon-basic-world"></i>
```

##### Another way of creating the "skewed" section design:

```scss
.section-features {
  padding: 20rem 0;

  transform: skewY(-7deg);

// direct child selector
  & > * {
    transform: skewY(7deg);
  }
}
```

##### How to make text flow around shapes:

```scss
  &__shape {
    position: relative;
    width: 15rem;
    height: 15rem;
    float: left;
    -webkit-shape-outside: circle(50% at 50% 50%);
    shape-outside: circle(50% at 50% 50%);
    -webkit-clip-path: circle(50% at 50% 50%);
    clip-path: circle(50% at 50% 50%);
    transform: translateX(-3rem);
  }
```

##### How to apply `filter` to images:

```
  &:hover &__img {
    filter: blur(3px) brightness(90%);
  }
```

##### How to use the `<video>` HTML element:

```html
<video class="bg-video__content" autoplay muted loop>
    <source src="img/video.mp4" type="video/mp4">
    <source src="img/video.webm" type="video/webm">
        Your browser is not supported!
</video>
```

##### How to create a background  video covering an entire section:

```scss
.bg-video {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  z-index: -1;
  opacity: .15;

  &__content {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }
}
```

##### How to implement solid-color gradients:

```scss
  background-image: linear-gradient(105deg,
    rgba(white, .9) 0%,
    rgba(white, .9) 50%,
     orangered 50%),
```

##### How to create boxes with equal height using `display: table-cell`:

```scss
.container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: table;
}

.left {
    width: 33.3333%
    display: table-cell;
}

.right {
    width: 66.6667%;
    display: table-cell;
}
```

##### How to create CSS text columns

```
column-count: 2;
column-gap: 4rem;
column-rule: 1px solid gray;
hyphens: auto;
```

##### Writing a Sass mixin for all media queries using if directives

```scss
//media query manager
/*
0-600px phone
600-900px tab portrait
900-1200px tab landscape
1200-1800 normal styles (desktop first)
1800+ big desktop

$breakpoint argument choices:
phone
tab-port
tab-land
big-desktop

1em = 16px
*/

@mixin respond($breakpoint) {
  @if $breakpoint == phone {
    @media (max-width: 37.5em) { @content }; //600px
  }
  @if $breakpoint == tab-port {
    @media (max-width: 56.25em) { @content }; //900px
  }
  @if $breakpoint == tab-land {
    @media (max-width: 75em) { @content }; //1200px
  }
  @if $breakpoint == big-desktop {
    @media (min-width: 112.5em) { @content }; //1800px
  }
}
```

applying to html document's font size:

```scss
html {
    // This defines what 1rem is (default 16px)
    font-size: 62.5%; //1 rem = 10px; 10px/16px = 62.5%

    @include respond(tab-land) { // width < 1200?
        font-size: 56.25%; //1 rem = 9px, 9/16 = 50%
    }

    @include respond(tab-port) { // width < 900?
        font-size: 50%; //1 rem = 8px, 8/16 = 50%
    }
    
    @include respond(big-desktop) {
        font-size: 75%; //1rem = 12, 12/16
    }
}
```

##### How to perform density switching using srcset attribute with density descriptors:

```html
<img srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x" alt="Full logo">
```

##### How to perform art direction according to screen width:

In case the viewport width is smaller than 37.5em, the image used will be the one from source. Inside each srcset is density switching according to screen resolution.

```html
<picture class="footer__logo">
  <source srcset="img/logo-green-small-1x.png 1x, img/logo-green-small-2x.png 2x" media="(max-width: 37.5em)">
  <img srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x" alt="Full logo">
</picture>
```

##### How to perform resolution switching using width descriptors:

```html
<img srcset="img/nat-1.jpg 300w, img/nat-1-large.jpg 1000w" sizes="(max-width: 900px) 20vw, (max-width: 600px) 30vw, 300px">
```

##### How to implement responsive images in CSS:

Note that comma acts like an OR operator. 192 dpi is apple retina screen

37.5em = 600px / 16, 125em = 2000px / 16

```scss
  @media (min-resolution: 192dpi) and (min-width: 37.5em), (min-width: 125em) { 
    background-image: linear-gradient(
    to right bottom,
    rgba($color-primary-light, 0.801),
    rgba($color-primary-dark, 0.801)), 
    url(../img/hiresimg.jpg);
  }
```

##### How to use `@supports` feature queries and how to use `backdrop-filter`:

```scss
  @supports (-webkit-backdrop-filter: blur(10px)) or (backdrop-filter: blur(10px)) {
    -webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);
    background-color: rgba($color-black, .3);
  }
```

##### Build process with npm:

dependencies:

```
autoprefixer@7.1.4
concat@1.0.3
node-sass@5.0.0
npm-run-all@4.1.5
postcss-cli@4.1.1
```

scripts:

```json
"compile:sass": "node-sass sass/main.scss css/style.comp.css ",
"concat:css": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css",
"prefix:css": "postcss --use autoprefixer -b \"last 10 versions\" css/style.concat.css -o css/style.prefix.css",
"compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
"build:css": "npm-run-all compile:sass concat:css prefix:css compress:css",
```

##### Dev process with npm:

```json
"watch:sass": "node-sass starter/sass/main.scss starter/css/style.css -w",
"devserver": "live-server",
"start": "npm-run-all --parallel devserver watch:sass",
```

