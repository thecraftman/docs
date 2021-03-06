<div class="axi-header">
  <h1>Virtual Fields</h1> 
</div>

**Virtual Fields allow you to derive new values from your data in real time**

One of the most powerful features of Axiom are Virtual Fields. With Virtual Fields, there is no need to do any up-front planning of how to structure or transform your data. Instead, send your data as-is and then use Virtual Fields to manipulate your data in real-time during queries.

The feature is also known has "derviced columns/fields", however Axiom's Virtual Fields have some unique properties that make them much more powerful.

In this guide, you'll be introduced to Virtual Fields, their features, how to manage them, and how to get the best out of them.

## Creating a Virtual Field

Once a dataset is selected in either the [Analytics](/usage/analyze) or [Stream](/usage/stream) views, clicking on the virtual fields icon in the toolbar will open the virtual field slide-out that displays all the virtual fields for a dataset:

<img class="axi-crop" src="/assets/shots/analyze-toolbar-vfields.png" alt="virtual fields tool button" />

<img class="axi-crop" src="/assets/shots/analyze-slideout-vfields.png" alt="virtual fields slideout" />

Click "Add Virtual Field" to open the virtual field editor dialog.

<img class="axi-crop" src="/assets/shots/vfields-editor.png" alt="virtual fields editor" />

The editor dialog has the following components:

* **Name** & **Description** - help your team understand what thie virtual field is doing
* **Alias** - this is the name of the field when used in visualizations, filters, and group-bys
* **Expression** - this the expression that is run on every event to derive the virtual field. The expression would produce some output (from a `boolean` check like the example, to `strings`, `numbeers`, `objects` or more)
* **Preview** - use the preview window to test your virtual field expression against live data

The power of virtual fields is in letting you manipulate data 'on read' ineas of 'on write', allowing you and your team members to adjust and update virtual fields over time as well as easily add new ones without worrying that the data has already been indexed.

## Usage
### Visualizations

Virtual Fields will be available as parameters to visualizations but, as the type of a virtual field can be any of the supported types, it is important to make sure that you are using a virtual field that produces the correct type of argument.
### Filters

Virtual Fields will be available in the filter menu and all filter options will be presented. It is important to ensure that you are using a supported filter operation for the type of result your virtual field produces.
## Group By

Virtual Fields can be used for segmentation in the same way as any standard field.
## Reference
Virtual Fields use a rich expression language that is easy to grasp but powerful in use. This section will 
### Examples

### Strings 

| **Functions** | **Description**                                            |
|----------------|---------------------------------------------------------------------------------------|
| **len** `(val: string): number`      | will return the length of an array, map, or string |
| **toLower** `(val: string): string`   | return the lowercase letter corresponding to the elements passed| 
| **replace** `(val: string, regex: string, replacement: string): string`    |  returns a new string with some or all elements replaced by a replacement |
| **trimLeft** `(val: string, trimChars: string): string`  |  Returns the string of elements trimmed from its left end |
| **trimRight** `(val: string, trimChars: string): string` |  Returns the string of elements trimmed from its right end |
| **trim** `(val: string, trimChars: string): string`      | Returns the string of elements trimmed from both end |
| **toUpper** `(val: string): string`     | Returns the string of elements in uppercase |
| **match** `(ELEMENT, "REGEX")`       |      Returns TRUE or FALSE based on whether REGEX matches ELEMENT         |
| **contains** ``(val: string): string` ` |  Returns true if sequence of char values are found in the string otherwise returns false.  |


### Arithmetic Operators

| **Functions**    | **Description**                                                |                                        
|--------------------|-----------------------------------------------------------------------------------------------|
| **abs**  `(val: number):number`        | returns the absolute value of the specified number |
| **ceil** `(val: string):number`        | returns the smallest integer that is greater than or equal to the element specified.|
| **exp** `(val: number): number)`        | returns the exponential function of the element. |
| **floor** `(val: number):number)`             | returns the largest integer less than or equal to a given element. |
| **ln** `(val: number): natural log of number)`            | returns the natural logarithm. |
| **log** `(val: number, base: number): number)`         | returns the logarithm of a number that is equal to its base.|
| **pi** `(): number`         | returns the mathematical constant “pi.” |
| **pow** `(val: number, exp: number): number`          | returns the base to the exponent power of the given element.|
| **round** `(val: number, precision: number): number`        | returns the rounded number with the specified version of decimals.|
| **sqrt** `(val: number): number`       | returns the square root of the element. |
| **acos** `(val: number): number`         | returns the inverse (arc) cosine of an element(number) in radians.|
| **acosh** `(val: number): number`         | returns the inverse hyperbolic cosine of an element(number).|
| **asin** `(val: number): number`      | returns the inverse (arc) sine of an element(number) in radians.| 
| **asinh** `(val: number): number`      | returns the inverse hyperbolic sine of an element(number).|
| **atan** `(val: number): number`         | returns the inverse (arc) tangent of an element.|
| **atan2** `(y: number, x: number): number`         | returns the inverse (arc) tangent of the two numbers (elements).|
| **cos** `(val: number): number`         | returns the cosine of an angle (radians).|
| **cosh** `(val: number): number`       | returns the hyperbolic cosine value.|
| **hypot** `(x: number, y: number): number`        | returns the hypotenuse of a right-angled triangle.|
|  **sin** `(val: number): number`         | returns the sine of an angle in radians.|
|  **sinh** `(val: number): number`       | returns the hyperbolic sine of an angle.| 
|  **tan** `(val: number): number`        | returns the tangent of the angle.| 
|  **tanh** `(val: number): number)`      |  returns the hyperbolic tangent of an angle.|   

### General Utility Functions

|**Functions** |        **Description**                  |
|-----------------|-----------------------------------------------------------|
|**isBool** `(val: any): bool`           |         Returns TRUE if the element is a Boolean. |
|**isInt**  `(val: any): bool`           |   	Returns TRUE if the element is an integer.    |
|**isNull** `(val: any): bool`           |      Returns TRUE if the element is NULL.           |
|**isNotNull** `(val: any): bool`        |    	Returns TRUE if the element is not NULL.       |
|**isNumber** `(val: any): bool`         |        Returns TRUE when value is numeric and FALSE when not.  |
|**isString** `(val: any): bool`        |      Returns TRUE if the field value is a string.     |
|**isArray** `(val: any): bool`          |                Returns true if the object is an array. |
|**isObject** `(val: any): bool`          |    Returns True if expression is a variable of Object subtype. |
| **typeof** `(val: any): string`          |   Returns the type of a variable when you call it.|
| **decodeBase64** `(val: string): string`  |    computes elements in base 64           |
|  **decodeHex** `(val: string): number`  | Returns the bytes represented by the hexadecimal strings.  |  
| **decodeURI** `(val: string): string`   | Returns a decoded URI by replacing each elements with the characters it represents.|    
| **encodeHexString** `(val: number): string` | Converts an array of bytes into a String representing the hexadecimal elements of each byte in order.|   
| **encodeURI** `(val: string): string`   |   returns the encoded string.  |     
|  **isCC** `(value: string): bool` |     |      
|  **isIMEI** `(value: string): bool`       |                   |    
|  **md5**`(value: string): string`     |   calculates the md5 hash for the given value.          |   
|  **sha1** `(value: string): string`    | Calculates the sha1 hash for the given value.   |  
|  **sha256** `(value: string): string]`   |  Calculates the sha256 hash for the given value.| 
|  **sha512** `(value: string): string`     |   Calculates the sha512 hash for the given value.    |    
|  **matchCIDR** `(cidrIpRange: string, ipAddress: string): boolean`  | Returns TRUE or FALSE based on if an IP address matches a CIDR notation.|  
|  **normalizeIPV6** `(address: string): string`  | Returns the IP address or prefix normalized to the NetDB internal format.|  
|  **sprint** `(format: string, val ...any): string`  | Returns the number of characters written to **str**, excluding the null character|

### Literals

* `strings` - single and double quotes are supported
* `numbers` - `101`, `101.1`
* `booleans` - `true` and `false`
* `arrays` - `["one", "two", "three"]`
* `maps` - `{ region: "us-east-1" }
* `nil` - `nil`

### Arithmetic Operators

* `+` - addition
* `-` - subtraction
* `*` - multiplication
* `/` - division
* `%` - modulus
* `**` - pow

### Comparison Operators

* `==` - equal
* `!=` - not equal
* `<` - less than
* `>` - greater than
* `<=` - less than or equal to
* `>=` - greater than or equal to

### Logical Operators

* `and` or `&&`
* `or` or `||`
* `not` or `!`
* `success ? 'yes' : 'no'` - ternary

### String Operators

* `+` - concatenation
* `matches` - regex match
* `contains` - string contains
* `startsWith` - has prefix
* `endsWith` - has suffix

!!! info
    To test the negative case of not matching, wrap the operator in a `not()` operator:
    
    `not ("us-east-1" contains "us")`

    You must use parentesis because the unary operator `not` has precedence over the binary operator `contains`.


### Numeric Operators

In addition to the [arithmetic operators](#arithmetic-operators):

* `..` - numeric range

!!! example
    `age in 18..45`  

!!! tip    
    The range is inclusive: `1..3 == [1, 2, 3]`


### Membership Operators

* `in` - contains
* `not in` - does not contain

!!! example
    Arrays: `metadata.region in ["us-east-1", "us-east-2"]`  
    Maps: `'region' in { region: 'us-east-1 }` // true


### Builtins

* `len` - length of an array, map, or string
* `all` - will return true if all element satisfies the predicate
* `none` - will return true if all element does NOT satisfies the predicate
* `any` - will return true if any element satisfies the predicate
* `one` - will return true if exactly ONE element satisfies the predicate
* `filter` - filter array by the predicate
* `map` - map all items with the closure
* `count` - returns number of elements what satisfies the predicate

!!! example "Ensure all comments are less than 280 chars"
    all(comments, {.Size < 280})

!!! example "Ensure there is exactly one private repo"
    one(repos, {.private})


### Closures

* `{...}` - closure

Closures allowed only with builtin functions. To access the current item, used the `#` symbol.

!!! Example
    `map(0..9, {# / 2})`

If the item of array is struct, it's possible to access fields of struct with omitted `#` symbol (`#.Value` becomes `.Value`).

!!! Example
    filter(comments, {len(.body) > 280})


### Slices

* `myArray[:]` - slice

Slices can work with arrays or strings

!!! Example
    The variable `myArray` is `[1, 2, 3, 4, 5]`  
    ```
    myArray[1:5] == [2, 3, 4]
    myArray[3:] == [4, 5]
    myArray[:4] == [1, 2, 3]
    myArray[:] == myArray
    ```