##### The best way to perform a basic reset using the universal selector:

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

##### How to set project-wide font definitions:

```css
body {
  font-family: "Lato", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.7;
  color: #777777;
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

