# Python-basics

## Python data types

| Type | Description | Data <br>Type | Example | Conversion <br>function |
|---|---|---|---|---|
| int | integer: a number without a fractional part. | Numeric | 100 | int() |
| float | floating point: a number that has both an integer <br>and fractional part, separated by a point. | Numeric | 1.1 | float() |
| str | string: a type to represent text. | Text | string, text | str() |
| bool | boolean: a type to represent logical values.<br>Can only be True or False (Capital are important) | Boolean | True; False | bool() |

You can use the type() function to inspect the type of a value or a variable.

## Python list

List: a list is a compound data type, a collection of values that can contain any data type, and different data types including other lists.

### Subsetting List

Python use zero-indexing (all list start at zero). You can subset a list as follow:<br>

Example<br>

list = [a, b, c, d, e, f, g]<br><br>

list[0]   = It will return from index 0 (i.e., a)<br>
list[3]   = It will return from index 3 (i.e., d)<br>
list[5]   = It will return from index 5 (i.e., f)<br>
list[-1]   = It will return from index 5 (i.e., f)<br>
list[-3]   = It will return from index 4 (i.e., e)<br>

#### List Slicing 

Syntax:<br> 
list[ Start(Inclusive):End(Exclusive) ]

list[:4]   = It will return from index 0 to 3 (i.e., a, b, c, d)<br>
list[2:]   = It will return from index 2 to 7 (i.e., c, d, e, f, g)<br>
list[2:4]  = It will return from index 2 to 3 (i.e., c, d)<br>