class: center, middle

# Day 3

First steps with SASS

---

layout: true
class: center, middle

---

# What is SASS?

Sass is CSS with superpowers.

http://sass-lang.com

---

# Major SASS features

* Nesting
* Extension
* Variables
* Math
* Imports
* Mixins

And there is more...

http://sass-lang.com/documentation/

---

# SASS or SCSS?

SCSS is valid CSS + Sass extensions.

SASS omits braces and semi-colons (;)

__We use SCSS because it is an easier transition__


---

# SCSS includes all of CSS

## CSS

``` css
h1 {
    font-size: 30px;
}
```   

## SCSS

``` sass
h1 {
    font-size: 30px;
}
```

---

# Nesting

## SCSS

```
body {
    font-size: 10px;
    
    .red {
        color: red;
    }
}
```

---

# Nesting

## Generated CSS

``` css
body {
    font-size: 10px;
}

body.red {
    color: red;
}
```

---

# Extension

## SCSS

```
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  @extend .message;
  border-color: green;
}

.error {
  @extend .message;
  border-color: red;
}
```

---

# Extension

## SCSS

```
.message {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
*  @extend .message;
  border-color: green;
}

.error {
*  @extend .message;
  border-color: red;
}
```

---

# Extension

## Generated CSS

``` css
*.message, .success, .error {
  border: 1px solid #cccccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}
```

---

# Variables

```
$font: Helvetica, Arial, sans-serif;
$red: #ff1f14;

body {
	font-family: $font;
	color: $red;
}
```

---

# Variables

```
*$font: Helvetica, Arial, sans-serif;
$red: #ff1f14;

body {
*	font-family: $font;
	color: $red;
}
```

---

# Variables

```
$font: Helvetica, Arial, sans-serif;
*$red: #ff1f14;

body {
	font-family: $font;
*	color: $red;
}
```

---

# Variables

## Generated CSS

``` css
body {
    font-family: Helvetica, Arial, sans-serif;
    color: #ff1f14;
}
```

---

# Math

## CSS

``` css
#fixed-box {
    padding: 10px;
*    width: 300px; /* really? */
}
```

This is probably an error, since padding gets added to the width, resulting in a width of 320px;

---

# Math

## SCSS

```
$padding: 10px;

#fixed-box {
    padding: $padding;
*    width: 300px - 2 * $padding;
}
```

---

# Math

## Generated CSS

``` css
#fixed-box {
    padding: 10px;
    width: 280px;
}
```

---

# Imports

Like CSS `@import` but doesn't create an additional HTTP request.

SCSS files starting with an underscore are assumed to be `@import` only and will not generate their own CSS.

---

# Imports

```
/* _colours.scss */
$red: #ff101f;
$green: #10ff1f;
$blue: #101fff;
```

```
/* style.scss */
@import "colours";

body {
    color: $red;
    background: $green;
    border: 1px solid $blue;
}
```

---

# Mixins

## CSS

``` css
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```

How repetitive!

---

# Mixins

## Define the Mixin

```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}
```

---

# Mixins

## Notice the variable

```
*@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}
```

---

# Mixins

## Notice the variable

```
@mixin border-radius($radius) {
*  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}
```

---

# Mixins

## Notice the variable

```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
*     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}
```

---

# Mixins

## Notice the variable

```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
*      -ms-border-radius: $radius;
          border-radius: $radius;
}
```

---

# Mixins

## Notice the variable

```
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
*          border-radius: $radius;
}
```

---

# Mixins

## Now use it

```
.box { @include border-radius(10px); }
```

## Generated CSS

``` css
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```