### Create Drop DownMenu in HTML

```html
<input name="country" list="countries" placeholder="Country">
<datalist id="countries">
    <option value="iran">
    <option value="iraq">
    <option value="USA">
</datalist>
```

---

### Specificity

```
1. inline
2. id
3. class
4. type
```

---

### CSS Selector

```
a, b   --->  Multiple Element Selector
a b    --->  Descendant Selector
a > b  --->  Child Selector
a + b  --->  Adjacent Sibiling Selector
[a=b]  --->  Attribute Selector
a:b    --->  Pseudoclass Selector
a::b   --->  Pseudoelement Selector
```

---

## Responsive

### Viewport

```html
<meta name="viewport" content="width=device-width; initial-scale=1.0">
```

### Media Queries

```css
@media (min-width:500)
{
    body {
        background-color: red;
    }
}

@media (max-width: 499)
{
    body {
        background-color: blue;
    }
}
```

### Flexbox

```html
<style>
    .container {
        display: flex;
        flex-wrap: wrap;
    }

    .container > div {
        background-color: green;
        font-size: 20px;
        margin: 20px;
        padding: 20px;
        width: 200px;
    }
</style>

<div class="container">
    <div>test 1</div>
    <div>test 2</div>
    <div>test 3</div>
    <div>test 4</div>
    <div>test 5</div>
</div>
```

### Grids

```html
<style>
    .grid {
        background-color: green;
        display: grid;
        padding: 20px;
        grid-column-gap: 20px;
        grid-row-gap: 10px;
        /* grid-template-columns: 200px 200px auto; */
        grid-template-columns: auto auto auto;
    }

    .grid-item {
        background-color: white;
        font-size: 20px;
        padding: 20px;
        text-align: center;
    }
</style>

<div class="grid">
    <div class="grid-item">1</div>
    <div class="grid-item">2</div>
    <div class="grid-item">3</div>
    <div class="grid-item">4</div>
    <div class="grid-item">5</div>
    <div class="grid-item">6</div>
    <div class="grid-item">7</div>
    <div class="grid-item">8</div>
    <div class="grid-item">9</div>
    <div class="grid-item">10</div>
    <div class="grid-item">11</div>
    <div class="grid-item">12</div>
</div>
```

## Bootstrap

```html
<div class="container">
    <div class="row">
        <!-- lg = large -->
        <!-- sm = small -->
        <div class="col-lg-3 col-sm-6">1</div>
        <div class="col-lg-3 col-sm-6">2</div>
        <div class="col-lg-3 col-sm-6">3</div>
        <div class="col-lg-3 col-sm-6">4</div>
    </div>
</div>
```

---
## SASS

sass file format : ```.scss```

### Compile

Compile SASS file
```bash
sass style.scss:style.css
```

Compile SASS file automatic
```bash
sass --watch style.scss:style.css
```

### Variable
```scss
$color: red;

ul {
    font-size: 18px;
    color: $color;
}
```

### Nesting
```scss
div {
    font-size: 18px;

    p {
        color: blue;
    }

    ul {
        color: green;
    }
}

         =

div {
    font-size: 18px;
}

div > p {
    color: blue;
}

div > ul {
    color: green;
}

```

### Inheritance
```scss
%message {
    font-family: sans-serif;
    font-size: 18px;
    font-weight: bold;
    border: 1px solid black;
    padding: 20px;
    margin: 20px;
}

.success {
    @extend %message;
    background-color: green;
}

.warning {
    @extend %message;
    background-color: orange;
}

.error {
    @extend %message;
    background-color: red;
}
```

