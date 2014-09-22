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

## SCSS

```
$padding: 10;

#fixed-box {
    padding: $padding;
    width: 300px - 2 * $padding;
}
```

---

# Math

## SCSS

```
*$padding: 10;

#fixed-box {
*    padding: $padding;
*    width: 300px - 2 * $padding;
}
```

---

# Math

## Generated CSS

``` css
#fixed-box {
    padding: 10;
    width: 260px;
}
```
