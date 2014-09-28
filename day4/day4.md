class: center, middle

# Day 4

PHP Basics

&

WordPress Template Functions

---

# Play along!

http://codepad.viper-7.com/

---

layout: true
class: center, middle

---

# Hypertext Pre-Processor

## index.html
``` html
<html>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

---

# Hypertext Pre-Processor

## index.php
``` php
<html>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

---

# Pure PHP

## functions.php
``` php
<?php
    /**
     * Twenty Fourteen only works in WordPress 3.6 or later.
     */
    if ( version_compare( $GLOBALS['wp_version'], '3.6', '<' ) ) {
        require get_template_directory() . '/inc/back-compat.php';
    }
?>
```

---

# Pure PHP

## functions.php
``` php
*<?php
    /**
     * Twenty Fourteen only works in WordPress 3.6 or later.
     */
    if ( version_compare( $GLOBALS['wp_version'], '3.6', '<' ) ) {
        require get_template_directory() . '/inc/back-compat.php';
    }
*?>
```

Everything between the `<?php` ... `?>` must be __valid__ PHP.

---

# PHP Language

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
    function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
    }
    
    wrap_name_in_html( $my_name );
?>
```  

---

## PHP Delimiters

``` php
*<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
    function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
    }
    
    wrap_name_in_html( $my_name );
*?>
``` 

---

## Comments

``` php
<?php
*    // Define a variable
    $my_name = "Tom";
    
*    /*  Use echo to put the contents of the variable
*        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
    function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
    }
    
    wrap_name_in_html( $my_name );
?>
``` 

---

## Variable assignment

``` php
<?php
    // Define a variable
*    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
    function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
    }
    
    wrap_name_in_html( $my_name );
?>
```

---

# Variable Assignment

.ch[`$`]`my_name` `=` `"`Tom`";`

Scalar variable indicator.

---

# Variable Assignment

`$`.ch[`my_name`] `=` `"`Tom`";`

Variable name. 

a-z A-Z "-" "_" and 0-9 (after 1st character)

---

# Variable Assignment

`$my_name` .ch[`=`] `"`Tom`";`

Assignment _operator_.

---

# Variable Assignment

`$my_name` `=` .ch[`"`]Tom.ch[`"`]`;`

Matching quotes.

---

# Variable Assignment

`$my_name` `=` `"`.ch[Tom]`";`

String _literal_.

---

# Variable Assignment

`$my_name` `=` `"`Tom`"`.ch[`;`]

Required to end the line.

---

# Keywords

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
*    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
    function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
    }
    
    wrap_name_in_html( $my_name );
?>
```  

---

# A PHP Statement

.ch[`echo`] _a bunch of code here_`;`

PHP keyword.

---

# An expression

`echo` .ch[_a bunch of code here_]`;`

``` php
echo $my_name;
echo "Joseph";
echo 5;
echo 5 + 10 * 25 / (3 + 2);

```

---

# Variable substitution

``` php
$my_name = "Tom";
echo $my_name;
```

## Result:

Tom

---

# Control Blocks

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
*    if ( $my_name == "Tom" ){
*        $my_name = $my_name . " " . "Auger";
*    }
    
*    function wrap_name_in_html ( $name ){
*        if ( ! empty ( $name ) ){
*            echo "<p>" . $name . "</p>";
*        }
*    }
    
    wrap_name_in_html( $my_name );
?>
```  

---

# Braces define blocks

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
*    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
*    }
    
     function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
     }
    
    wrap_name_in_html( $my_name );
?>
``` 

---

# Nested blocks

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
*    function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
*    }
    
    wrap_name_in_html( $my_name );
?>
``` 

---

# Nested blocks

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
    function wrap_name_in_html ( $name ){
*        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
*        }
    }
    
    wrap_name_in_html( $my_name );
?>
```

---

# Function definition

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
*    function wrap_name_in_html ( $name ){
*        if ( ! empty ( $name ) ){
*            echo "<p>" . $name . "</p>";
*        }
*    }
    
    wrap_name_in_html( $my_name );
?>
``` 

---

# Using a function

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
    function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
    }
    
*    wrap_name_in_html( $my_name );
?>
```

---

# Calling a function

`my_function( $argument_1, $argument_2 );`

---

# Calling a function

.ch[`my_function`]`( $argument_1, $argument_2 );`

Function name.

---

# Parentheses

`my_function`.ch[`(`] `$argument_1, $argument_2` .ch[`)`]`;`

---

# Argument list

`my_function(` .ch[`$argument_1, $argument_2`] `);`

---

# Don't forget  ;-)

`my_function( $argument_1, $argument_2 )`.ch[`;`]

---

# Code review

``` php
<?php
    // Define a variable
    $my_name = "Tom";
    
    /*  Use echo to put the contents of the variable
        onto the web page. (Output the variable) */
    echo $my_name;
    
    if ( $my_name == "Tom" ){
        $my_name = $my_name . " " . "Auger";
    }
    
    function wrap_name_in_html ( $name ){
        if ( ! empty ( $name ) ){
            echo "<p>" . $name . "</p>";
        }
    }
    
    wrap_name_in_html( $my_name );
?>
```

---

# Result

``` html
<p>Tom Auger</p>
```

---

# <?php ?>

``` html
<html>
    <body>
        <h1>This is Heading One</h1>
        <p>
            <?php
                echo "Hello World";
            ?>
        </p>
    </body>
</html>
```

---

# <?php ?>

Only code within `<?php ... ?>` blocks are interpreted as PHP. Everything else is HTML.

``` php
<html>
    <body>
        <h1>This is Heading One</h1>
        <p>
            <?php
                echo "Hello World";
            ?>
        </p>
    </body>
</html>
```

---

# Result

By the time it reaches your browser, it's all just plain ol' HTML.
``` html
<html>
    <body>
        <h1>This is Heading One</h1>
        <p>
            Hello World
        </p>
    </body>
</html>
```

The browser never sees the PHP.

---

# Wherever and as often

``` php
<html>
    <body>
        <h1><?php echo $the_title; ?></h1>
        <p><?php echo $the_content; ?></p>
        <?php
            if ( is_admin() ){
                echo "<p>";
                echo $the_author;
                echo "</p>";
            }
        ?>
    </body>
</html>
```

---

# Wherever and as often

``` php
<html>
    <body>
*        <h1><?php echo $the_title; ?></h1>
*        <p><?php echo $the_content; ?></p>
*        <?php
            if ( is_admin() ){
                echo "<p>";
                echo $the_author;
                echo "</p>";
            }
*        ?>
    </body>
</html>
```

---

# PHP can output HTML

``` php
echo "<h1>Big Heading</h1>";
echo "<p>Some other text</p>";
```

---

# A matter of style

``` php
<html>
    <body>
        <h1><?php echo $the_title; ?></h1>
        <p><?php echo $the_content; ?></p>
        <?php
            if ( is_admin() ){
*                echo "<p>";
                echo $the_author;
*                echo "</p>";
            }
        ?>
    </body>
</html>
```

---

# A matter of style

``` php
<html>
    <body>
        <h1><?php echo $the_title; ?></h1>
        <p><?php echo $the_content; ?></p>
        <?php
            if ( is_admin() ){
        ?>
*        <p>
        <?php
            echo $the_author;
        ?>
*        </p>
        <?php
            }
        ?>
    </body>
</html>
```

---

# A few PHP tags...

``` php
<html>
    <body>
        <h1><?php echo $the_title; ?></h1>
        <p><?php echo $the_content; ?></p>
*        <?php
            if ( is_admin() ){
                echo "<p>";
                echo $the_author;
                echo "</p>";
            }
*        ?>
    </body>
</html>
```

---

# Or a lot...

``` php
<html>
    <body>
        <h1><?php echo $the_title; ?></h1>
        <p><?php echo $the_content; ?></p>
*        <?php
            if ( is_admin() ){
*        ?>
        <p>
*        <?php
            echo $the_author;
*        ?>
        </p>
*        <?php
            }
*        ?>
    </body>
</html>
```

---

# Before you decide...

``` php
<?php
    if ( is_admin() ){
        echo "<div class='admin-only'><ul><li>";
        echo $the_author;
        echo "</li><li>";
        echo $author_biography;
        echo "</li><li>";
        echo "<a href='";
        echo $author_url;
        echo "'>Author website</a>";
        echo "</li></ul>";
        echo "</div>";
    }
?>
```

---

# ... or HTML

``` html
<?php
    if ( is_admin() ){
?>

    <div class="admin-only">
        <ul>
            <li>
                <?php echo $the_author; ?>
            </li>
            <li>
                <?php echo $author_biography; ?>
            </li>
            <li>
                <a href="<?php $author_url ?>">Author website</a>
            </li>
        </ul>
    </div>
    
<?php
    }
?>
```

---

# Avoid shortcuts

`<? ?>`

`<?= ?>`

`<% %>`

---

# Scalar variables

`$variable_name =` _expression_`;`

``` php
$string = "Some text";
$height = 640;
$true_or_false = true;
$something = my_function();
```

---

# Strings

``` php
*$string = "Some text";
$height = 640;
$true_or_false = true;
$something = my_function();
```

---

# Numeric

``` php
$string = "Some text";
*$height = 640;
$true_or_false = true;
$something = my_function();
```

---

# Boolean

``` php
$string = "Some text";
$height = 640;
*$true_or_false = true;
$something = my_function();
```

---

# Function result

``` php
$string = "Some text";
$height = 640;
$true_or_false = true;
*$something = my_function();
```

---

# Strings

``` php
// These all do the same thing
echo "Tom";

echo 'Tom';

$my_name = 'Tom';
echo $my_name;

$my_name = "Tom";
echo $my_name;
```

---

# Quotes matter

``` php
// These are not the same
$my_name = "Tom";

echo "Hello $my_name";
echo 'Hello $my_name';
```

## Results

1. `Hello Tom`

2. `Hello $my_name`

---

# Quotes always match

``` php
// WRONG!!!!
echo "<a href="page2.html">Jump to Page 2</a>";
     ^        ^          ^                   ^
```

`page2.html` is not valid PHP!

---

# Quotes always match

``` php
// One way...
echo '<a href="page2.html">Jump to Page 2</a>';
     ^                                       ^
```

---

# Quotes always match

``` php
// Another way...
echo "<a href='page2.html'>Jump to Page 2</a>";
              ^          ^
```

---

# Escaping quotes

``` php
// Escape with a backslash
echo "<a href=\"page2.html\">Jump to Page 2</a>";
              ^           ^
```

---

# String operators

Concatenation

``` php
echo "Tom" . " " . "Auger";
```

Result

```
Tom Auger
```

---

# Variable re-assignment

``` php
$my_name = "Tom";
$my_name = $my_name . " " . "Auger";
```

Result

```
Tom Auger
```

---

# Variable re-assignment

``` php
$my_name = "Tom Auger";
$my_name = "The " . $my_name;
```

Result

```
The Tom Auger
```

---

# String Functions

http://php.net/manual/en/ref.strings.php

* `trim()` Trims whitespace

* `strstr()` Returns everything after (or before) a string

* `substr()` Return a part of a string

---

# Trim

``` php
$messy_name = "  Tom Auger   ";
$clean_name = trim($messy_name);

echo $clean_name;
```

Returns

```
Tom Auger
```

No extra spaces.

---

# String search

``` php
$email = "teach.me.tom@outlook.com";
echo strstr($email, "@");
echo strstr($email, "@", true);
```

Returns

```
@outlook.com
teach.me.tom
```

---

# Substring

``` php
$text = "The quick brown fox";
echo substr($text, 0, 1);
echo substr($text, 4);
echo substr($text, 4, 5);
echo substr($text, -1);
echo substr($text, -3);
echo substr($text, -3, 1);
```

Returns

```
T
quick brown fox
quick
x
fox
f
```

---

# Substring

``` php
$text = "The quick brown fox";
*echo substr($text, 0, 1);
echo substr($text, 4);
echo substr($text, 4, 5);
echo substr($text, -1);
echo substr($text, -3);
echo substr($text, -3, 1);
```

Returns

```
*T
quick brown fox
quick
x
fox
f
```

---

# Substring

``` php
$text = "The quick brown fox";
echo substr($text, 0, 1);
*echo substr($text, 4);
echo substr($text, 4, 5);
echo substr($text, -1);
echo substr($text, -3);
echo substr($text, -3, 1);
```

Returns

```
T
*quick brown fox
quick
x
fox
f
```

---

# Substring

``` php
$text = "The quick brown fox";
echo substr($text, 0, 1);
echo substr($text, 4);
*echo substr($text, 4, 5);
echo substr($text, -1);
echo substr($text, -3);
echo substr($text, -3, 1);
```

Returns

```
T
quick brown fox
*quick
x
fox
f
```

---

# Substring

``` php
$text = "The quick brown fox";
echo substr($text, 0, 1);
echo substr($text, 4);
echo substr($text, 4, 5);
*echo substr($text, -1);
echo substr($text, -3);
echo substr($text, -3, 1);
```

Returns

```
T
quick brown fox
quick
*x
fox
f
```

---

# Substring

``` php
$text = "The quick brown fox";
echo substr($text, 0, 1);
echo substr($text, 4);
echo substr($text, 4, 5);
echo substr($text, -1);
*echo substr($text, -3);
echo substr($text, -3, 1);
```

Returns

```
T
quick brown fox
quick
x
*fox
f
```

---

# Substring

``` php
$text = "The quick brown fox";
echo substr($text, 0, 1);
echo substr($text, 4);
echo substr($text, 4, 5);
echo substr($text, -1);
echo substr($text, -3);
*echo substr($text, -3, 1);
```

Returns

```
T
quick brown fox
quick
x
fox
*f
```

---

# Putting it together

``` php
$email = "teach.me.tom@outlook.com";
$name = strstr($email, "@", true);

$domain = strstr($email, "@");
echo $domain;

$domain = substr($domain, 1);
echo $domain;

echo "Name: $name, Domain: $domain";
```

Result

```
@outlook.com
outlook.com
Name: teach.me.tom, Domain: outlook.com
```

---

# Putting it together

``` php
$email = "teach.me.tom@outlook.com";
$name = strstr($email, "@", true);

*$domain = strstr($email, "@");
*echo $domain;

$domain = substr($domain, 1);
echo $domain;

echo "Name: $name, Domain: $domain";
```

Result

```
*@outlook.com
outlook.com
Name: teach.me.tom, Domain: outlook.com
```

---

# Putting it together

``` php
$email = "teach.me.tom@outlook.com";
$name = strstr($email, "@", true);

$domain = strstr($email, "@");
echo $domain;

*$domain = substr($domain, 1);
*echo $domain;

echo "Name: $name, Domain: $domain";
```

Result

```
@outlook.com
*outlook.com
Name: teach.me.tom, Domain: outlook.com
```

---

# Putting it together

``` php
$email = "teach.me.tom@outlook.com";
$name = strstr($email, "@", true);

$domain = strstr($email, "@");
echo $domain;

$domain = substr($domain, 1);
echo $domain;

*echo "Name: $name, Domain: $domain";
```

Result

```
@outlook.com
outlook.com
*Name: teach.me.tom, Domain: outlook.com
```

---

# Function as argument

``` php
$email = "teach.me.tom@outlook.com";
*$domain = strstr($email, "@");
*$domain = substr($domain, 1);
```

... more compact

``` php
$email = "teach.me.tom@outlook.com";
*$domain = substr(strstr($email, "@"), 1);
```

---

# Numeric variables

``` php
$x = 25;
$y = -1;
$pi = 3.14159265359;
$half = 1/2;
echo $half
```

Result

```
0.5
```

---

# Mathematical operators

* `+` Addition

* `-` Subtraction

* `*` Multiplication

* `/` Division

---

# Mathematical operators

``` php
$height = 10;
$width = 15;

$area = $height * $width;

echo $area;
```

Result

```
150
```

---

# Mathematical operators

``` php
$a = 3;
$b = 4;

$hypotenuse = $a * $a + $b * $b;

echo $hypotenuse;
```

Result

```
25
```

---

# Order matters!

``` php
echo 10 / 2 + 8;
echo 10 / (2 + 8);
```

Result

```
13
1
```

---

# Mathematical functions

http://php.net/manual/en/ref.math.php

* `abs()` Absolute (positive) value

* `sin()`, `cos()`, `tan()` Trig functions

* `round()` Rounding

* `max()`, `min()` Maximum and minimum values

---

# Positive values

``` php
$x1 = 200;
$x2 = 400;

$distance = abs($x1 - $x2);
echo $distance;

$distance = abs($x2 - $x1);
echo $distance;
```

Result

```
200
200
```

---

# Rounding
``` php
echo round(0.25);
echo round(0.75);
echo round(-0.25);
echo round(0.5);
```

Result

```
0
1
-0
1
```

---

# Maximum and minimum values

``` php
echo max(-3, 5, 10, 20);
echo min(-3, 5, 10, 20);
echo max(min(-3, 5), min(10, 20));
```

Result
```
20
-3
10
```

---

# Random numbers!

``` php
echo rand(1, 10);
echo rand(1, 10);
echo rand(1, 10);
echo rand(1, 10);
echo rand(1, 10);
```

Result

```
5
1
7
10
5
```

---

# Functions

``` php
function double($value){
    return $value * 2;
}

echo double(2);
echo double(10);
echo double(-5);
```

Result

```
4
20
-10
```

---

# Functions

``` php
function square($value){
    return $value * $value;
}

echo square(2);
echo square(10);
echo square(-5);
```

Result

```
4
100
25
```

---

# Anatomy of a Function

`function` `square(` `$value` `){ ... return ... }`

---

# Anatomy of a Function

.ch[`function`] `square(` `$value` `){ ... return ... }`

Function declaration keyword.

---

# Anatomy of a Function

`function` .ch[`square`]`(` `$value` `){ ... return ... }`

Function name.

---

# Anatomy of a Function

`function` `square`.ch[`(`] `$value` .ch[`)`]`{ ... return ... }`

Arguments list.

---

# Anatomy of a Function

`function` `square(` .ch[`$value`] `){ ... return ... }`

Argument.

---

# Anatomy of a Function

`function` `square(` `$value` `)`.ch[`{`] `... return ...` .ch[`}`]

Function block.

---

# Anatomy of a Function

`function` `square(` `$value` `){ ... `.ch[`return`]` ... }`

(Optional) return statement.

---

# Calling a function

`square(` `4` `);`

---

# Calling a function

.ch[`square`]`(` `4` `);`

Matches function name.

---

# Calling a function

`square`.ch[`(`] `4` .ch[`)`]`;`

Arguments list.

---

# Calling a function

`square(` .ch[`4`] `);`

Arguments should match function signature.

---

# Calling a function

`square(` `4` `)`.ch[`;`]

Don't forget the ;-^

---

# Arguments

``` php
function no_arguments(){
    echo "Hello World!";
}

function one_argument($name){
    echo "Hello $name!";
}

function many_arguments($greeting, $name, $noun){
    echo "$greeting, $name's $noun!";
}

no_arguments();
one_argument("class");
many_arguments("Hi", "Joe", "friend");
```

```
Hello World!
Hello class!
Hi Joe's friend!
```

---

# Required arguments

``` php
function many_arguments($greeting, $name, $noun){
    echo "$greeting, $name's $noun!";
}

many_arguments("Hi", "Joe");
```

---

# Required arguments

``` php
*function many_arguments($greeting, $name, $noun){
    echo "$greeting, $name's $noun!";
}

*many_arguments("Hi", "Joe");
```

---

# Result

```
Warning: Missing argument 3 for many_arguments(), called in  
/code/wY9Iu3 on line 7 and defined in /code/wY9Iu3 on line 3

Notice: Undefined variable: noun in /code/wY9Iu3 on line 4
Hi, Joe's ! PHP Warning: Missing argument 3 for many_arguments(),  
called in /code/wY9Iu3 on line 7 and defined in /code/wY9Iu3 on line 3  
PHP Notice: Undefined variable: noun in /code/wY9Iu3 on line 4
```

Yuck-a-doo.

---

# Default (optional) arguments

``` php
function many_arguments($greet = "Hello", $name = "Tom", $noun = "class"){
    echo "$greet, $name's $noun!";
}

many_arguments();
many_arguments("Hi");
many_arguments("Hi", "Joe");
many_arguments("Dave");
```

Result

```
Hello, Tom's class!
Hi, Tom's class!
Hi, Joe's class!
Dave, Tom's class!
```

---

# Default (optional) arguments

``` php
function many_arguments($greet = "Hello", $name = "Tom", $noun = "class"){
    echo "$greet, $name's $noun!";
}

many_arguments();
many_arguments("Hi");
many_arguments("Hi", "Joe");
*many_arguments("Dave");
```

Result

```
Hello, Tom's class!
Hi, Tom's class!
Hi, Joe's class!
*Dave, Tom's class!
```

---

# Return exits the function

``` php
function early_return(){
    echo "One";
    return;
    echo "Two";
}

early_return();
```

Result

```
One
```

---

# Return is optional

``` php
function do_something(){
    echo "Doing lots of stuff."
}
```

---

# Return a single result

``` php
function this_is_bad(){
    return "one", "two", "three";
}
```

Error

```
Parse error: syntax error, unexpected ',' in /code/EkeCxb on line 4
```

---

# WordPress functions

http://codex.wordpress.org/Function_Reference

---