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

---

# And there is more...

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

``` scss
h1 {
    font-size: 30px;
}
```

---

# Nesting

## SCSS

``` scss
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

``` scss
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

``` scss
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

``` scss
$font: Helvetica, Arial, sans-serif;
$red: #ff1f14;

body {
	font-family: $font;
	color: $red;
}
```

---

# Variables

``` scss
*$font: Helvetica, Arial, sans-serif;
$red: #ff1f14;

body {
*	font-family: $font;
	color: $red;
}
```

---

# Variables

``` scss
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

``` scss
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

``` scss
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

``` scss
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

``` scss
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

``` scss
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

``` scss
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

``` scss
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

``` scss
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

---

# It gets better...

``` scss
@mixin frutiger($style: 'normal'){
    @if $style == 'italic' {
        font-family:'FrutigerLTW01-56Italic';
    }
    
    @else {
        font-family:'FrutigerLTW01-55Roman';
    }
    
    font-weight: normal;
	font-style: normal;
}
```

``` scss
body {
    @include frutiger('italic');
}
```

---

# Mind blown yet?

## Generated CSS

``` css
body {
    font-family:'FrutigerLTW01-56Italic';
    font-weight: normal;
	font-style: normal;
}
```

---

# Okay.

# Take a deep breath.

# Don't panic.

---

# SASS in WordPress

## What you'll need:

* WordPress running locally
* A child theme of twentyfourteen
* A 'css' and a 'sass' (or 'scss') folder
* NetBeans, with its CSS preprocessor properly configured.

---

# Let's get started!

---

# Here's how things stand in WordPress Land

```
wp-content/
   |
   +--themes/
        |
        +-- twentyfourteen/
        |
        +-- day3/
              |
              +== style.css
              |
              +-- css
              |
              +-- sass
```

---

# day3/style.css

``` css
 /*
	Template:     twentyfourteen
 */

/* Bring in the styles from the parent theme */
@import "../twentyfourteen/style.css";
```

Typically, we would just start over-riding CSS as needed from this point onward.

---

# Create your first SASS (SCSS) file

```
sass/base.scss
```

You could call this anything you like. 

`base` sounds like a good name for your "base" stylesheet.

---

# Test out your SASS file

``` scss
// sass/base.scss

body {
    color: red;
}
```

Don't forget to save. 

This automatically creates `css/base.css`

``` css
body {
    color: red; }
```

---

# Import your CSS into your theme's stylesheet

``` css
 /*
	Template:     twentyfourteen
 */

/* Bring in the styles from the parent theme */
@import "../twentyfourteen/style.css";

/*	Bring in your own custom base styles. */
/*	Make sure you import the .css file and not the .scss file! */
@import "css/base.css"; 
```

---

# Let's make this more SASSy

``` scss
// sass/base.scss

$font: Helvetica, Arial, sans-serifx;
$red: #ff1f14;

body {
	font-family: $font;
	color: $red;
}
```

---

# Styling the Header.

* Use the Chrome Inspector or Firebug to locate the `<header>` tag
* Test your CSS right in the browser to save time.

``` css
.entry-header {
    background-color: red;
}
```

Wait... that didn't work?

---

# Specificity

Our rule is being over-ridden by a more specific rule.

Use the "Computed" styles tab in your favourite inspector to see this.

```
background-color	rgb(255,255,255)
*.site-content .entry-header     #fff
~~.entry-header                 red~~
```

---

# Specificity

http://css-tricks.com/specifics-on-css-specificity/

It's critical to understand the rules of specificity when you're over-riding styles from a parent theme.

---

# Specificity in a nutshell

1) If two rules are identical, the one defined last wins.

``` css
p {
    color: red;
}

p {
    color: green; /* wins! */
}
```

---

# Specificity in a nutshell

2) A `.class` wins over a `tag`

``` html
<p class="message">Hello World!</p>
```

``` css
.message {
    color: red; /* wins! */
}

p {
    color: green;
}
```

---

# Specificity in a nutshell

3) An `id` wins over a `.class`

``` html
<div id="primary" class="message">Hello World!</div>
```

``` css
#primary {
    font-size:24px; /* wins! */
}

.message {
    font-size:10px;
}
```

---

# Specificity in a nutshell

4) Rules can still combine

``` html
<div id="primary" class="message">Hello World!</div>
```

``` css
#primary {
    font-size:24px;
}

.message {
    font-size:10px; /* over-ridden */
    color: red; /* remains */
}
```

---

# Specificity in a nutshell

5) A more specific rules wins over a more general rule

* `#header.body-text` (most specific)
* `.main .body-text` (more general)
* `p.body-text` (even more general)
* `.body-text` (loses to `p.body-text`)
* `p` (most general)

---

# Specificity in a nutshell

6) `!important` always wins, but avoid using it.

---

# Putting specificity to work

``` scss
// base.scss (continued)

.site-content {
	.entry-header {
		background-color: red;
	}
}
```

But what if we wanted to span the entire content area?

---

