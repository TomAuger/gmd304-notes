class: center, middle

# Day 4

PHP Basics

&

WordPress Template Functions

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