class: center, middle

# Day 5

Arrays and Loops

---

layout: true
class: center, middle

---

# Play along!

http://codepad.viper-7.com/

---

# Arrays

Arrays are variables that can hold more than one value.

This allows you to create "collections" of data in the same way that databases do.

---

# array()

``` php
$grades = array( 85, 76, 88, 95, 65, 50 );

// Use white space and line breaks for legibility
$names = array( 
    "Tom", 
    "Joe", 
    "Dan", 
    "Bob", 
    "Jim", 
    "Tim", 
    "Some other guy with a really long name!" 
);
```

---

# Outputting arrays

``` php
// WRONG!
echo $names, "<br>";
```

```
Notice: Array to string conversion in /code/4oVIvQ on line 5
Array
```

---

# Outputting arrays

``` php
// This works for DEBUGGING purposes
print_r( $names ); // but is never used in production code
```

```
Array ( [0] => Tom [1] => Joe [2] => Dan [3] => Bob [4] => Jim  
        [5] => Tim [6] => Some other guy with a really long name! )
```

Or even more (possibly confusing) details:

``` php
var_dump( $names );
```

```
array(7) { [0]=> string(3) "Tom" [1]=> string(3) "Joe"  
           [2]=> string(3) "Dan" [3]=> string(3) "Bob"  
           [4]=> string(3) "Jim" [5]=> string(3) "Tim"  
           [6]=> string(39) "Some other guy with a really long name!" }
```

---

# Accessing array data

``` php
// Subscript $names
echo "0: " . $names[0], "<br>";
echo "1: " . $names[1], "<br>";
echo "5: " . $names[5], "<br>";
```

```
0: Tom
1: Joe
5: Tim
```

0-indexed arrays means the 1st element is at index 0 (_not_ 1).

---

# Array length

``` php
echo "Length of 'names': " . count( $names ), "<br>";

// WRONG! This is the 8th element (which doesn't exist).
echo "Index 7: " . $names[7], "<br>";
```

```
Length of 'names': 7

Notice: Undefined offset: 7 in /code/0Sg67H on line 5
Index 7: 
```

Index **7** subscripts the **8**th element!

---

# Accessing last element

``` php
// Access the last element of $names
$last_item_index = count( $names ) - 1;
echo "$last_item_index: " . $names[$last_item_index], "<br>";

// Do it in a more compact way:
echo "Last item: " . $names[count( $names ) - 1], "<br>";

// Or, try end()
echo "End: " . end( $names ), "<br>";
// Consider reset() afterward.
```

```
6: Some other guy with a really long name!
Last item: Some other guy with a really long name!
End: Some other guy with a really long name!
```

---

# Valid data types

Arrays can store anything a variable can store

``` php
$mixed_array = array(
	"Some text",
	1,
	1.3475,
	false,
	true
);

print_r( $mixed_array );
```

```
Array ( [0] => Some text [1] => 1 [2] => 1.3475 [3] => [4] => 1 ) 
```

---

# Side note: Booleans

``` php
// What's up with "false" and "true"?
echo true, "<br>"; // Echoes 1
echo false, "<br>"; // Echoes nothing (empty line)
```

In most cases 0 and "" are `false`  
and any string and any other number are `true`

Movin' on...

---

# Multidimensional arrays


An array can even contain another array! This is called a "multi-dimensional" array

``` php
$triangle = array(
	array( 50, 0 ),
	array( 100, 100 ),
	array( 0, 100 )
);

print_r( $triangle );
```

```
Array ( [0] => Array ( [0] => 50 [1] => 0 )
        [1] => Array ( [0] => 100 [1] => 100 ) 
        [2] => Array ( [0] => 0 [1] => 100 ) )
```

---

# 1st dimension is array

``` php
// WRONG generates notice
echo $two_dee[0], "<br>";

// Right, $two_dee[0] is an array!
print_r( $two_dee[0] );
```

```
Notice: Array to string conversion in /code/ChSya3 on line 10
Array
Array ( [0] => 50 [1] => 0 )
```

---

# Subscripting 2D arrays

``` php
echo "[0,0] " . $triangle[0][0], "<br>";
echo "[0,1] " . $triangle[0][1], "<br>";
echo "[2,0] " . $triangle[2][0], "<br>";
echo "[2,1] " . $triangle[2][1], "<br>";
```

```
[0,0] 50
[0,1] 0
[2,0] 0
[2,1] 100
```

---

# Array Iteration

"Iterating through an array" refers to doing something with each element of the array.

This is useful for outputting results, searching, calculating totals, or even transforming the contents of the array itself.

This is most often accomplished through "loops".

---

# foreach

``` php
$names = array( "Tom", "Joe", "Dan", "Bob", "Jim", "Tim",  
                "Some other guy with a really long name!" );

// Let's iterate through this array.
foreach( $names as $name ){
	echo $name, "<br>";
}
```

```
Tom
Joe
Dan
Bob
Jim
Tim
Some other guy with a really long name!
```

---

# Anatomy of "foreach"

`foreach( $names as $name ){ // code ... }`

---

# Anatomy of "foreach"

.ch[`foreach`]`( $names as $name ){ // code ... }`

"foreach" loop keyword

---

# Anatomy of "foreach"

`foreach`.ch[`( $names as $name )`]`{ // code ... }`

Loop expression

---

# Anatomy of "foreach"

`foreach( $names as $name )`.ch[`{ // code ... }`]

Code block, executed once per element

---

# Anatomy of "foreach"

`foreach( `.ch[`$names`] ` as $name ){ // code ... }`

The array we're looping through

---

# Anatomy of "foreach"

`foreach( $names` .ch[`as`] `$name ){ // code ... }`

Required keyword `as`

---


# Anatomy of "foreach"

`foreach( $names as ` .ch[`$name`] ` ){ // code ... }`

Variable to which we're assigning each element of the array 

---

# Anatomy of "foreach"

`foreach( $names as $name ){` .ch[`$name`] `}`

`$name` changes for every iteration of the loop.

---

# Better HTML output

``` php
// We can do better. Let's wrap some HTML.
echo "<ul>";
foreach( $names as $name ){
	echo "<li>Name: $name</li>";
}
echo "</ul>";
```

``` html
<ul>
    <li>Name: Tom</li>
    <li>Name: Joe</li>
    <li>Name: Dan</li>
    <li>Name: Bob</li>
    <li>Name: Jim</li>
    <li>Name: Tim</li>
    <li>Name: Some other guy with a really long name!</li>
</ul>
```

---

# Passing by reference

``` php
// Edit "in place" - pass by reference
foreach( $names as &$name ){ // <-- note the "&" in front of $name
	$name = strtolower( $name );
}
print_r( $names );
```

```
Array ( [0] => tom [1] => joe [2] => dan [3] => bob [4] => jim  
        [5] => tim [6] => some other guy with a really long name! )
```

`&$name` points to the __actual element__ inside `$names`. Changing it inside the loop changes the array (permanently).

---

# "for" loops

``` php
// There's another way to loop.
for ( $i = 0; $i < 10; $i = $i + 1 ){
	echo "$i", "<br>";
}
```

```
0
1
2
3
4
5
6
7
8
9
```

---

# "for" loop expression

`for ( $i = 0; $i < 10; $i = $i + 1 ){}`

* Starting with $i at 0
* If $i < 10, execute the block
* Then add 1 to $i
* If $i is 10 or more, stop the loop

---

# Anatomy of a "for" loop

`for ( $i = 0; $i < 10; $i = $i + 1 ){}`

---

# Anatomy of a "for" loop

.ch[`for`] `( $i = 0; $i < 10; $i = $i + 1 ){}`

"for" loop keyword

---

# Anatomy of a "for" loop

`for` .ch[`( $i = 0; $i < 10; $i = $i + 1 )`]`{}`

Loop expression

---

# Anatomy of a "for" loop

`for ( $i = 0; $i < 10; $i = $i + 1 )`.ch[`{}`]

Loop block. All code in this block is executed once per loop iteration.

---

# Anatomy of a "for" loop

`for (` .ch[`$i = 0;`] `$i < 10; $i = $i + 1 ){}`

Loop initializer. Called only once before the loop is started.

---

# Anatomy of a "for" loop

`for ( $i = 0;` .ch[`$i < 10;`] `$i = $i + 1 ){}`

Loop condition. If "true", the loop block is executed. If "false" the loop block is skipped and the loop is terminated.

---

# Anatomy of a "for" loop

`for ( $i = 0; $i < 10;` .ch[`$i = $i + 1`] `){}`

Post-loop expression. Evaluated at the end of every loop. Usually used to change the loop variable so it eventually fails the test condition.

(Otherwise you get an "infinite loop")

---

# Anatomy of a "for" loop

`for ( $i = 0; $i < 10; $i = $i + 1 ){` .ch[`$i`] `}`

`$i` changes for each iteration of the loop.

---

# Autoincrement

``` php
for ( $i = 0; $i < 10; $i++ ){
	echo "$i", "<br>";
}
```

`$i++` is just a snappier version of `$i = $i + 1;`

---

# For loops and arrays

``` php
// Now, let's try it on our array.
for ( $i = 0; $i < count( $names ); $i++ ){
	echo "[$i] " . $names[$i], "<br>"; 
}
```

```
[0] Tom
[1] Joe
[2] Dan
[3] Bob
[4] Jim
[5] Tim
[6] Some other guy with a really long name!
```

---

# For loops and arrays

``` php
// Now, let's try it on our array.
for ( $i = 0; $i < count( $names ); $i++ ){
	echo "[$i] " . $names[$i], "<br>"; 
}
```

Since we're using `<` for our condition, we don't have to do `count( $names ) - 1`

This is one of the reasons why a zero-indexed array is useful.

---

# Complex variables

``` php
// Don't like having $names[i] outside the quotes?
for ( $i = 0; $i < count( $names ); $i++ ){
	echo "[$i] {$names[$i]}", "<br>"; 
}
```

When subscripting an array within double quotes, help the parser out by surrounding the expression in `{}`

---

# Changing the "step"

``` php
// Every other element
for ( $i = 0; $i < count( $names ); $i = $i + 2 ){
	echo "[$i] {$names[$i]}", "<br>"; 
}

// Backward?
for ( $i = count( $names ) - 1; $i > -1; $i -= 1 ){
	echo "[$i] {$names[$i]}", "<br>"; 
}
```

---

# Better backward

``` php
// Less awkward, once you're used to it
for ( $i = count( $names ); $i--; ){
	echo "[$i] {$names[$i]}", "<br>"; 
}
```

The condition is evaluated _before_ the `--` is applied to $i, but the `--` happens _before_ we enter the loop, so the first item is `count( $names ) - 1` after all.

`0` is considered `false` so when we hit `0`, the test fails and the loop terminates.

---

# Quick exercises

1. Loop through some names, displaying each name in a random colour (use inline CSS `rgb()`)
2. Loop backward, displaying the last name and only every third name after that.

---

# Not-so-quick exercises
1. Modify your names array, swapping any two vowels (like "i" and "o") using `str_ireplace()`. Use `print_r()` to prove you've altered the array.
2. Loop through your names array, and, using either `str_shuffle()` or `strrev()`, scramble the letters of each name, and then output them with proper capitalization.

---

# Associative Arrays

Associative arrays are a lot like databases - they allow us to _associate_ a __value__ with a __key__.

This is very useful for quickly accessing a specific piece of data.

---

# Associative array construction

``` php
// Use the => to separate key => value
$favourite_colours = array(
	"Tom" => "green",
	"Ben" => "blue",
	"Joe" => "yellow",
	"May" => "pink",
	"Amy" => "orange"
);

echo $favourite_colours["Tom"];
```

```
green
```

---

# Complex variables again

``` php
echo "Tom's favourite colour is {$favourite_colours['Tom']}";
```

```
Tom's favourite colour is green
```

---

# Associative foreach

``` php
// Let's loop through these items
foreach( $favourite_colours as $key => $value ){
    // use {} to help separate $key from 's
	echo "{$key}'s favourite colour is $value", "<br>";
}
```

```
Tom's favourite colour is green
Ben's favourite colour is blue
Joe's favourite colour is yellow
May's favourite colour is pink
Amy's favourite colour is orange
```

---

# Accessing just the keys

``` php
// Can I just access the names (keys)?
print_r( array_keys( $favourite_colours ) );
```

```
Array ( [0] => Tom [1] => Ben [2] => Joe [3] => May [4] => Amy )
```

`array_keys()` returns a (regular) array.

---

# Looping through keys

``` php
// We can use this in a loop, too!
$names = array_keys( $favourite_colours );
for ( $i = 0; $i < count( $names ); $i = $i + 2 ){
	echo "$i: {$names[$i]}: {$favourite_colours[$names[$i]]}", "<br>";
}
```

```
0: Tom: green
2: Joe: yellow
4: Amy: orange
```

---

# Looping through values

``` php
// Can we access just the colours?
print_r( array_values( $favourite_colours ) );
```

```
Array ( [0] => green [1] => blue [2] => yellow  
        [3] => pink [4] => orange )
```

---

# Values can be arrays

``` php
$users = array(
	"tauger" => array( "Tom Auger", "green", "admin",  
                        "teach.me.tom@outlook.com" ),
                        
	"smelly_92" => array( "Dan Brown", "brown", "editor",  
                        "dbrown@gmail.com" ),
                        
	"ninjat" => array( "Michael Boren", "yellow", "contributor",  
                        "pizzadude@yahoo.ca" )
);
```

---

# Or associative arrays

``` php
$users = array(
	"tauger" => array( 
		"full_name" => "Tom Auger", 
		"fav_colour" => "green", 
		"access_level" => "admin", 
		"email" => "teach.me.tom@outlook.com"
	),
	"smelly_92" => array( 
		"full_name" => "Dan Brown", 
		"fav_colour" => "brown", 
		"access_level" => "editor", 
		"email" => "dbrown@gmail.com"
	),
	"ninjat" => array( 
		"full_name" => "Michael Boren", 
		"fav_colour" => "yellow", 
		"access_level" => "contributor", 
		"email" => "pizzadude@yahoo.ca"
	)
);
```

---

# Or associative arrays

``` php
echo $users['tauger']['access_level'];
```

```
admin
```

Associative arrays used this way are often called "records", just like database entries.

---

# Logic and Conditionals

---

# Booleans review

``` php
// Boolean review
$true = true;
$false = false;

echo $true, "<br>"; // Echoes "1"
echo $false, "<br>"; // Echoes nothing
```

```
1
```

---

# Testing with "if"

``` php
if ( true ){
	echo "Yes, it's true!", "<br>";
}

if ( false ){
	echo "You will never see this message."; // Doesn't execute
}
```

```
Yes, it's true!
```

---

# Evaluating other values

When testing with `if()` a number of surprising things can be evaluated as Booleans for "truth" or "falsity".

* Numbers other than 0 are `true`.
* 0 evaluates to `false`
* Strings all evaluate to `true`
* Empty strings evaluate to `false`
* Non-empty arrays evaluate to `true`
* Empty arrays are `false`

---

# Strings

``` php
if ( "something" ){ // true
	echo "I got something", "<br>";
}

if ( "" ){ // false
	echo "This will never show up";
}
```

```
I got something
```

---

# Strings

This is a useful pattern. Consider the following:

``` php
<p>Written by: 
<?php echo get_the_author_link(); ?></p>
```

If the results of `get_the_author_link()` are empty, you will still see "Written by:" with nothing after it!

---

# Strings

Now, try wrapping this in a conditional:

``` php
<?php
$link = get_the_author_link();
if ( $link ){
    echo "<p>Written by: $link</p>";
}
?>
```

Only outputs the line if the author actually supplied a link URL.

---

# Numbers

``` php
// Numbers
if ( 1 ){ //true
	echo "Any number is true", "<br>";
}

if ( 42 ){ //true
	echo "This is very true", "<br>";
}

if ( -1 ){ //true
	echo "Surprisingly, this is true too", "<br>";
}

if ( 0 ){ //false
	echo "Except for 0.";
}
```

```
Any number is true
This is very true
Surprisingly, this is true too
```

---

# Numbers

This can be a useful pattern too. Consider:

``` php
<p><?php echo get_comments_number( get_the_ID() ); ?> comments:</p>
(list comments...)
```

Or

``` php
<?php
$num_comments = get_comments_number( get_the_ID() );
if ( $num_comments ){
    echo "<p>$num_comments comments:</p>";
    // list comments...
}
?>
```

---

# Arrays

``` php
$some_array = array( "a", "b", "c" );
if ( $some_array ){ // true
	echo "Yes, there are items in this array", "<br>";
}

$empty_array = array();
if ( $empty_array ){ // false
	echo "No, this array is empty";
}
```

```
Yes, there are items in this array
```

---

# Arrays

Very useful:

``` php
$comments = get_comments(); // Returns an array
if ( $comments ){
    // Only show comments list if there actually are comments
}
```

---

# Negation

``` php
if ( $show_it ){
	echo "Yes!"; // Doesn't execute
}

// Negation

if ( ! $show_it ){
	echo "No!", "<br>"; // Executes
}
```

```
No!
```

`!` is the "not" operator.

(Read: "if not $show_it")

---

# Else

``` php
$show_it = true;

if ( $show_it ){
	echo "Showing it", "<br>"; // Displays
} else {
	echo "Not showing it", "<br>"; // Doesn't execute
}
```

```
Showing it
```

---

# Else

``` php
$show_it = false; // switch it up!

if ( $show_it ){
	echo "Showing it", "<br>"; // Doesn't execute
} else {
	echo "Not showing it", "<br>"; // Displays
}
```

```
Not showing it
```

---

# Numeric expressions

``` php
$number = 5;
if ( $number < 10 ){
	echo "Less than 10!", "<br>";
}

if ( $number > 2 ){
	echo "Greater than 2!", "<br>";
}

if ( $number >= 5 ){
	echo "Greater or equal to 5!", "<br>";
}

if ( $number == 5 ){
	echo "Is equal to 5!", "<br>";
}

if ( $number != 4 ){
	echo "Is not equal to 4!", "<br>";
}
```

---

# Scope

"Scope" refers to the accessibility of variables in different contexts within your program.

---


# Function scope

Variables defined in functions are not accessible outside those functions

``` php
function get_name( $user ){
    $name = $user['full_name'];
    return $name;
}

echo $name; // undefined
```

---

# Outer scope

Variables defined outside functions are not accessible in the functions unless passed as an argument or declared with the `global` keyword.

``` php
$names = array ( "Tom", "Dick", "Harry" );

function get_random_name(){
    // Fail. Doesn't have access to $names
    return $names[rand(0, count( $names ) - 1];
}
```

---

# Global scope

``` php
$names = array ( "Tom", "Dick", "Harry" );

function get_random_name(){
    // Grant access to $names for this function
    global $names;
    return $names[rand(0, count( $names ) - 1];
}
```