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
$two_dee = array(
	array( "Tom", "boy" ),
	array( "Amy", "girl" ),
	array( "Pat", "???" )
);

print_r( $two_dee );
```

```
Array ( [0] => Array ( [0] => Tom [1] => boy )
        [1] => Array ( [0] => Amy [1] => girl ) 
        [2] => Array ( [0] => Pat [1] => ??? ) )
```

---

# Top-level elements are Arrays

``` php
// WRONG generates notice
echo $two_dee[0], "<br>";

// Right, $two_dee[0] is an array!
print_r( $two_dee[0] );
```

```
Notice: Array to string conversion in /code/ChSya3 on line 10
Array
Array ( [0] => Tom [1] => boy )
```

---

# Subscripting 2D arrays

``` php
echo "[0,0] " . $two_dee[0][0], "<br>";
echo "[0,1] " . $two_dee[0][1], "<br>";
echo "[2,0] " . $two_dee[2][0], "<br>";
echo "[2,1] " . $two_dee[2][1], "<br>";
```

```
[0,0] Tom
[0,1] boy
[2,0] Pat
[2,1] ???
```