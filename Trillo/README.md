##### How to use custom CSS properties (CSS variables):

```scss
:root {
  --color-grey-light-1: #faf9f9;
  --color-grey-light-2: #f4f2f2;
  --color-grey-light-3: #f0eeee;
  --color-grey-light-4: #cccccc;
    
  --shadow-dark: 0 2rem 6rem rgba(0, 0, 0, .3)
}
```

##### How to use SVG sprites in HTML:

Resource: icomoon

```html
<button class="search__button">
  <svg class="search__icon">
    <use xlink:href="img/sprite.svg#icon-magnifying-glass"></use>
  </svg>
</buton>
```

##### How to change color of SVG icon in CSS:

```scss
  &__icon {
    fill: #ffffff;
  }
```

##### Inheriting color using `currentColor`:

```scss
  &__link:link,
  &__link:visited {
    color: var(--color-grey-light-1);
    text-decoration: none;
    text-transform: uppercase;
    display: inline-block;
    padding: 1.5rem 3rem;
  }

  &__icon {
    height: 1.75rem;
    width: 1.75rem;
    margin-right: 2rem;
    fill: currentColor;
  }
```

##### How to create an infinite animation:

```
.btn-inline {
  &:focus {
    animation: pulsate 1s infinite;
  }

}
```



```scss
@keyframes pulsate {
  0% {
    transform: scale(1);
    box-shadow: none;
  }

  50% {
    transform: scale(1.05);
    box-shadow: 0 1rem 4rem rgba(0,0,0,.25);
  }

  100% {
    transform: scale(1);
    box-shadow: none;
  }
}
```

