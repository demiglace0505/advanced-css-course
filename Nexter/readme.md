##### Creating a grid:

```html
<div class="container">
    <div class="header">Header</div>
    <div class="box-1">Small box 1</div>
    <div class="box-2">Small box 2</div>
    <div class="box-3">Small box 3</div>
    <div class="sidebar">Sidebar</div>
    <div class="main">Main content</div>
    <div class="footer">Footer</div>
</div>
```

```scss
.container {
  display: grid;
  grid-gap: 30px;
  grid-template-rows: 100px 200px 400px 100px;
  grid-template-columns: repeat(3, 1fr) 200px;
}
```

##### Naming grid lines

```scss
.container {
    display: grid;
    grid-gap: 30px;
    grid-template-rows: [header-start] 100px [header-end box-start] 200px [box-end main-start] 400px [main-end footer-start] 100px [footer-end];
	grid-template-columns: repeat(3, [col-start] 1fr [col-end]) 200px [grid-end]; 
} 
// Repeat will create: col-start 1 col-start 2 col-start 3 col-end 1 col-end 2 col-end 3

.header{
  grid-column: col-start 1 / grid-end;
}
```

##### Naming grid areas

```scss
.container {
  width: 1000px;
  margin: 30px auto;
  
  display: grid;
  grid-gap: 30px;
  grid-template-rows: 100px 200px 400px 100px;
  grid-template-columns: repeat(3, 1fr) 200px;
  
  grid-template-areas: ". head head ." // dot signifies empty cell
                       "box-1 box-2 box-3 side"
                       "main main main side"
                       "foot foot foot foot";
}
```

##### Using grid areas:

```
.header{
  grid-area: head;
}

.sidebar {
  grid-area: side;
}

.main {
  grid-area: main;
}

.footer {
  grid-area: foot;
}

.box-1 {
  grid-area: box-1;
}
.box-2 {
  grid-area: box-2;
}
.box-3 {
  grid-area: box-3;
}
```

##### Using `auto-fit` to fill entire width of the container dynamically for responsive layouts:

```scss
grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
```

