# <center><ins>Python Quick Reference

<div class="alert alert-success alertsuccess" style="margin-top: 20px">
    <font size="5">Authors Note</font><br><br>This notebook is an <strong>ongoing project</strong>, and as such, while every effort has been made to ensure the accuracy and completeness of the information, no guarantee is given nor responsibility taken for errors or omissions.<br><br>The notebook is designed for <strong>rapidly finding information regarding correct syntax and structure.</strong><br>No examples are included in this notebook for cleaner and easier reading. Please see my other notebooks (Start with "Python_basics") which contains examples.<br><br>I hope this comes in useful to whoever finds it.<br>Andy Taison 28/04/2022
</div>

[Python3 cheat sheet](https://perso.limsi.fr/pointal/_media/python:cours:mementopython3-english.pdf)

|<td colspan=3> <center><bold><h3>**Table of contents**<center>|||
|---|:---|:---:|
|**1.**|[**Useful information**](#Useful-information:)||
|**2.**|[**Operator precedence rule in Python**](#Operator-precedence-rule-in-Python:)||
|**3.**|[**Mutable or Immutable**](#Mutable-or-Immutable:)||
|**4.**|[**Strings/Variables, Operators and Basics**](#Strings/Variables-and-Basics:)|types, operators, comparisons,<br>escape sequences, basic methods,<br>user input,<br>formatting strings, f-strings, formatting types,<br>zfill( )|
|**5.**|[**Regular Expressions (Regex)**](#Regular-Expressions-(Regex):)|Metacharacters<br>Special Sequences, sets<br>RegEx functions<br>Match objects, flags|
|**6.**|[**Tuples**](#Tuples:)|( )<br>immutable, ordered|
|**7.**|[**Lists**](#Lists:)|[ ]<br>mutable, ordered|
|**8.**|[**Dictionaries**](#Dictionaries:)|{ : , }<br>keys are mutable and unique|
|**9.**|[**Sets**](#Sets:)|{ }<br>unordered and unique elements,<br>mutable|
|**10.**|[**Branching**](#Branching:)|if( ): else( ): elif( ):|
|**11.**|[**Logic Operators**](#Logic-Operators:)|not or and|
|**12.**|[**Loops**](#Loops:)|for :<br>parallel iteration<br>[ list comprehension ], { dictionary comprehension }<br>while :<br>break, continue, pass|
|**13.**|[**Exception Handling**](#Exception-Handling:)|built-in exceptions,<br>try except statement,<br>raise exception<br>custom exception<br>traceback<br>assert|
|**14.**|[**Useful Built-in Functions**](#-Useful-Built-in-Functions:)|range( ), enumerate( ),<br> .count( ), sum( ),<br>isnumeric( ), isinstance( ),<br>zip( ),<br>map( )|
|**15.**|[**Building Functions**](#-Building-Functions:)|define, call and help on functions,<br>global / local scopes,<br>lambda functions|
|**16.**|[**Classes, Objects and Methods**](#Classes,-Objects-and-Methods:)|define class, create objects,<br>inheritance,<br>access / change attributes,<br>create / call methods,<br>special methods,<br>get/set with @property decorator<br>dir command,<br>duck typing|
|**17.**|[**Command line arguments**](#Command-line-arguments:)|using sys<br>argparse|
|**18.**|[**PIP**](#PIP:)|list installed packages,<br>install / uninstall packages|
|**19a.**|[**Working with Files<br>Opening and Reading Files**](#Opening-and-Reading-Files:)|open function,<br> .name, .mode, .closed, .close( ) methods,<br> with statement,<br> .read( ), .readline( ), .readlines( ) methods|
|**19b.**|[**Working with Files<br>Writing to Files**](#Writing-to-Files:)|.write( ) method,<br>with statement,<br> .seek( ), .tell( ) methods,<br>writting from a list, copying files|
|**20.**|[**CSV Library**](#CSV-Library:)|reading csv files<br>reading to a dataset<br>using csv library<br>writting to csv files|
|**21.**|[**Excel files**](#Excel-Files:)|read Excel files to dataframe<br>ExcelFile<br>sheet_names, parse( )<br>writting to Excel from dataframe<br>ExcelWriter<br>writting formula to Excel|
|**22.**|[**Pandas**](#Pandas:)|import library,<br>create df from file / dictionary / columns,<br>saving df,<br>head / tail / take / info / describe / columns / index / shape / loc / iloc / unique methods,<br>selecting data,<br>rename / reorder columns, set index / index name<br>drop function<br>groupby( ) method|
|**23.**|[**NumPy**](#NumPy:)|import library,<br>cast list to numpy,<br>numpy matrix objects,<br>largest element in array or matrix,<br>zeros( ), ones( ), eye( ), empty( ) functions<br>cast dataset to ndarray<br>index / slice arrays,<br>dtype / size / ndim / shape / unique methods,<br>array addition / subtraction / multiplication,<br>add axis to array<br>hadamard / dot product,<br>matrix multiplication,<br>norm of a matrix or vector,<br>transpose a matrix,<br>trace of a matrix,<br>determinant of a matrix,<br>inverse of a matrix,<br>Moore-Penrose pseudoinverse,<br>eig function (eigenvalues/vectors),<br>min, max, square root, mean, variance, standard deviation, pi,<br>random numbers with Numpy, int / float / seed<br>random binomial / uniform / poisson / normal / gassian distributions<br>linspace,<br>matplotlib| 
|**24.**|[**Working with Images**](#Working-with-Images:)|RGB colour space<br>set array for image channel<br>Pillow, Image modules<br>open( ), show( ), imshow( ) functions<br> size, format, mode attributes<br> resize an image<br>save image<br>create ndarray from image<br>clipping images<br>broadcasting to an image|
|**25.**|[**Basic Statistics**](#Basic-Statistics:)|statistical types of data<br>types of probability distribution<br>expected value<br>mode, variance, median<br>pearson correlation coefficient (PCC)|
|**26.**|[**Data Processing**](#Data-Preprocessing:)|data scaling<br>data normalisation<br>ordinal encoding<br>one-hot encoding<br>concatenate arrays|
|**27.**|[**Simple APIs**](#Simple-APIs:)||  
|**End**|[**End of Notebook / Notes**](#Notes:)||

## <center>Useful information:</center>


```python
# Check the Python Version

import sys
print(sys.version)
```

>Python is an interpreted, object-orientated, high-level programming language with dynamic semantics. It interprets script line by line as it executes and will stop the entire program when it encounters an error unless error was expected and handled by the programmer.  
Python is coded in C/C++ meaning C/C++ code can be created and used within Python.   

<div class="alert alert-success alertsuccess" style="margin-top: 20px">
    [Tip:] When learning a <code>new library</code>, always start by checking out the developers website and begin with the quick start.
</div>

---

**Help** on operations, types, methods and functions

**`help(A)`**
* Would give help on a list and variable `A`

---

**print all variables and function names of a module**  

**`print(dir(moduleName))`**  
* This will print all the variables and function names from the module given  

---

**Get Unicode code**  

**`ord(character)`**  
* Returns the unicode of given character  

---

**tab prompt**  

* Use tab to autocomplete when typing variable names and functions  
* Can also be used after **"."** to get a prompt list of availiable functions and methods  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Operator precedence rule in Python:</center>

|||
|---|---|
|()| Parentheses|
|**| Exponent|
|+x, -x, ~x| Unary plus, Unary minus, Bitwise NOT|
|*, /, //, % |Multiplication, Division, Floor Division, Modulus|
|+, - |Addition, Subtraction|
|<<, >> |Bitwise shift operators|
|& |Bitwise AND|
|^ |Bitwise XOR|
|\|| Bitwise OR|
|==, !=, >, >=, <, <=, is, is not, in, not in       |Comparisions, Identity, Membership operators|
|not |Logical NOT|
|and |Logical AND|
|or |Logical OR|

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Mutable or Immutable:</center>

|**Mutable:**|**Immutable:**|
|:---|:---|
|List|Int|
|Dictionary|Float|
|Set|Long|
|User-Defined Classes<br>(depending on the defined attributes by the user)|Complex|
|Byte Array|Boolean|
||String|
||Tuple|
||Frozenset|
||Unicode|

**Python** is Pass by **object reference**  

Pass by **reference** = The variable is passed directly (by reference) to a function. Any operation performed by the function on the variable will change the original object as it is the same object.  

Pass by **value** = A copy of the object is passed to the function. Any operation performed by the function will not affect the original object.  

Pass by **object reference** = A reference to the original object is passed, however the function will create a new variable. In essence, the object is the same, but now has two names in which to reference the object. If contents of the object is changed by the function (modified in place and can only be done with mutable objects), the contents of the original are updated too (similar to pass by reference). However if the reference/variable name is changed in the function, then the original object will not be affected (similar to pass by value).  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Strings/Variables and Basics:</center>

**Types and Typecasting**  

**`print(type(var))` or `type(var)`**  
* Type function used to view or print the type of a variable or data type  

**`None`**  - absence of data  

**`dataType_toConvertTo(var)`**  
* Converts a datatype or variable into another  
* Convert to the following:
  * **`float(var)`** - converts to float
  * **`int(var)`**   - converts to integer (if converting a boolean to int, true will give "1", false will give "0")
  * **`complex(var)`** - converts to complex number
  * **`str(var)`**   - converts to string
  * **`bool(var)`**  - converts to boolean ("1" will give true, "0" will give false)
  * **`tuple(var)`** - converts to tuple
  * **`list(var)`**  - converts to a list
  * **`set(var)`**   - converts to a set
  * **Note all of the above must be assigned a variable to save change**

**Type hinting**:  

**`variable/parameter: type`**  
**`-> output type`**  
* Used to **hint** at what types are expected  
* Note this is **not enforced**  

---

**Operators**

**`/`** **divide** gives result as **float** even when both inputs and output are whole numbers   
**`//`** **floor division** gives result as **int**  
**`*`** **multiply**  
**`**`** **Exponentiation** will give the **power of**  
**`%`** **modulus** will give **remainder of a division**  

**`+=`** **increment assignment** adds a value and a variable and assigns it to the variable  
**`-=`** **decrement assignment** subtracts a value from a variable and assigns it to the variable  
**`/=`** **division assignment** divides the variable by a value and assigns it to that variable  
**`*=`** **multiplication assignment** multiplies the variable by a value and assigns it to that variable  
**`%=`** **modulus assignment** computes the modulus of the variable and a value and assigns result to that variable  
**`//=`** **floor division assignment** floor divides the variable by a value and assigns result to that variable  
**`**=`** **power assignment** raises the variable to a specified power and assigns result to the variable  
  

---

**Comparison Operators**  
* Compares some values, operands or variables including strings

**`==`** **Equality operator** Gives result "True" when both sides are equal  
**`!=`** **Inequality operator** Gives result "True" when both sides are **Not** equal  
**`<`** **Less than operator** Gives result "True" when operand on left side is less than operand on right side  
**`>`** **Greater than operator** Gives result "True" when operand on left side is greater than operand on right side  
**`<=`** **Less than or equal to operator** Gives result "True" when operand on left side is less than or equal to the right side  
**`>=`** **Greater than or equal to operator** Gives result "True" when operand on left side is greater than or equal to the right side  

---

**Escape sequences**

**`\`** proceeds the escape sequence - This will allow you to spread lines of code over multipul lines  

**`\n`** for new line  
**`\t`** for tab  
**`\r`** for return  
**`\\`** to insert a single **`\`** in string    
**`r`** to display as raw string (placed before the quotation mark)  

**`pass`** can be used as a placeholder for future code. When the pass statement is executed, nothing happens, but you avoid getting an error when empty code is not allowed. Empty code is not allowed in loops, function definitions, class definitions, or in if statements  

**Line continuation in code**  

**`( )`**  parentheses is the prefered method  
**`\`**  backslash can sometimes look better, and with some lines of code is the only way for it to work  
* **ENSURE** to indent continuing line of code  

---

**Strings**  

* Strings are immutable 
* Contained within two quotes, either single 'a' or double "b" but not a mixture  
* **Multi line / long strings** are with **3 double or single quotes `"""`** before and after the string  
* Can contain characters, digits, spaces or special characters  
* Strings can be added when digits or characters, **beware** this will be done as text not numbers e.g., ="1" + "4" : "14"  
* Each element of a string can be accessed with an index represented by array of numbers, first character will be 0 and counting up to the right.
  Or from the end starting at -1 and counting down to the left 

---

**Indexing**

**`var[index]`**

* Accesses element of string/variable
* First character will be 0 and counting up to the right
* OR starting at the end, -1 and counting down to the left
* **Square brackets**

---

**Slice**  


**`var[start point : end point]`** 
* Will take section of variable from/to
* Think of points between the characters 

---

**Stride**  

**`var[start : end : places to jump]`**
* Will take elements of variable jumping given places
* If no start/end entered, will start from beginning

---

**Length** function  

**`len(var)`**
* Returns length of string  
* Starts at 1, **number of elements** NOT index numbers

---

**Concatenate** and combine strings

**`new_var = var1 + var2`**

---

**Replicate** strings

**`#timesToRep* var`**

---

**Upper**

**`var.upper()`**
* Makes everything upper case
* Must assign a variable to keep the change

---

**Replace**

**`var.replace("what", "with")`**
* Replaces elements of variable
* Assign new variable to save change 
* **Case sensitive**

---

**Find**

**`var.find("what")`**
* Outputs **first index** of sequence
* Returns **`-1`** if not found

---

**Strip** method  

**`var.strip()`**  
* **Removes white spaces** and **escape characters** at the **beginning** and **end** of a string  
* Ensure to save to a new variable to save the changes  

---

**split** method  

**`listVar = strVar.split(sep=None, maxsplit=-1)`**  
* Converts string to a list of words, standard delimiter is a **space**  
* **`sep`** is the delimiter, None = **default whitespaces**  
* **`maxsplit`** is the maximum number of splits to do, -1 = **default no limit**  

---

**join** method  

**`string.join(iterable)`**  
* Creates **strings** from iterable objects  
* Joins each **element** of an iterable (such as lists, strings, tuples, dictionaries and sets) by a **string separator**  

---

**User input**  

**`var = type(input("message to user"))`**  
* Keyword **"input"** used to provide input box to user  
* **Optional message**, however better practice to provide information on what to input  
* Defining **"type"** is **optional**, however note user inputs **default to strings**  

---

####  **Formatting Strings**  

**Place holders**  

**`placeHolderVar = "some string with placeholder a {}, and place holder b {}"`**  
**`placeHolderVar.format(a,b)`**


* **`{}`** can be used as place holders to insert variables later  
* Call the variable with the placeholders followed by **`.format`** to insert variables  
* Placeholders can be **positional**, or identified by a **given name**, or by **index numbers**, note this will be index **of the variables provided** and not of the placeholder position index numbers  
* Can also format using the **keys from a dictionary** and reference dictionary in format with double star **\*\*dictVar**  
* **Class members** can be used in place holders such as **{a.attribute}** and the class referenced in the formatting **.format(a=Class())**  
* Must save to a new variable to save  

**F-Strings**  

**`placeHolderVar = f"some string with placeholder a {var_a}, and placeholder b {var_b}"`**  

* Good for when you have a calculation to put inside the placeholder  
* F-strings do not require the use of "format"  
* Requires **f before string**, this can be **upper or lower** case  

**Formatting types**  

* Formatting types can be put in placeholders after the optional index/reference  

**`:<`**  Left aligns the result (within the available space)  
**`:>`**  Right aligns the result (within the available space)  
**`:^`**  Center aligns the result (within the available space)  
**`:=`**  Places the sign to the left most position  
**`:+`**  Use a plus sign to indicate if the result is positive or negative  
**`:-`**  Use a minus sign to show negative numbers minus sign  
**`: `**  Use a space to insert an extra space before positive numbers (and a minus sign before negative numbers)  
**`:,`**  Use a comma as a thousand separator  
**`:_`**  Use a underscore as a thousand separator  
**`:b`**  Binary format  
**`:c`**  Converts the value into the corresponding unicode character  
**`:d`**  Decimal format  
**`:e`**  Scientific format, with a lower case e  
**`:E`**  Scientific format, with an upper case E  
**`:f`**  Fix point number format  
**`:F`**  Fix point number format, in uppercase format (show inf and nan as INF and NAN)  
**`:g`**  General format  
**`:G`**  General format (using a upper case E for scientific notations)  
**`:o`**  Octal format  
**`:x`**  Hex format, lower case  
**`:X`**  Hex format, upper case  
**`:n`**  Number format  
**`:%`**  Percentage format  

**Decimal places, padding and truncating strings**  

**`f"{*index/ref : *padding(number of spaces in front).*decimal places to display or max chars from string}"`**  
* Note the **`.`** between the padding and decimal places/chars to display  
* When specifying **decimals**, must follow with **`f`** to denote number format  
* To add padding with **strings**, must specify **allignment** **OR** number of **TOTAL** characters to be displayed  
    * e.g. **`f"{*index/ref : totalNumberCharacters . decimalPlacesToDisplay f}"`**  
* Can add a **character before padding** and this will be used **instead of the default space**, when doing this, the padding number will represent the max **WIDTH including the passed variable length**    

---

**zfill** method  

**`strVar.zfill(len)`**  
* Adds zeros (0) at the beginning of the string, until it reaches the specified length  
* If the value of the len parameter is less than the length of the string, no filling is done  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Regular Expressions (Regex):</center>

**`import re`**  

**`text_to_search = "some string"`**  
**`patternVar = re.compile(r"patternToMatch")`**  
**`matchesVar = patternVar.RegExFunction(text_to_searchVar)`**  

**`for match in matchesVar:`**  
$\;\;\;\;$**`print(match)`**  

* Allow us to search for and match specific patterns of text  
* To use, we need to first import the **`re`** module  
* Compile method allows us to seperate out our patterns into a variable and easier to reuse that variable to perform multiple searches
* Use **`r`** before pattern to ensure string is treated as raw string  
* Try to make pattern to match as specific as possible, modify it as required to match further items  

**Metacharacters**  

* Characters with a special meaning  
* If searching for a **literal metacharacter** it **MUST** be **escaped**  

|**Character**|**Description**|**Example**|**Example meaning**|
|:---|:---|:---|:---|
|**[ ]**|Defines a set of characters|"[a-m]"|Find all lower case characters alphabetically between "a" and "m"|
|<b>\\<b>|Signals a special sequence (can also be used to escape special characters)|"\d"|Find all digit characters|
|**.**|Matches any character (**except** newline character)|"he..o"|Search for a sequence that starts with "he", followed by two (any(.)) characters, and an "o"|
|**^**|Starts with|"^hello"|Check if the string starts with 'hello'|
|**\$**|Ends with|"planet$"|Check if the string ends with 'planet'|
|**?**|Zero or one occurrences|"he.?o"|Search for a sequence that starts with "he", followed by 0 or 1  (any(.)) character, and an "o"|
|**\***|Zero or more occurrences|"he.*o"|Search for a sequence that starts with "he", followed by 0 or more  (any(.)) characters, and an "o"|
|**+**|One or more occurrences|"he.+o"|Search for a sequence that starts with "he", followed by 1 or more  (any (.)) characters, and an "o"|
|**{ }**|Exactly the specified number of occurrences<br>or range of number of occurences {min, max}|"he.{2}o"<br>"he.{2,5}o"|Search for a sequence that starts with "he", followed by exactly 2 (any) characters, and an "o"<br>"he" followed by between 2 and 5 (any (.)) characters, and an "o"|
|**\|**|Either or|"falls\|stays"|Check if the string contains either "falls" or "stays"|
|**( )**|Capture and group<br>A group of characters to match|"(com\|net\|gov)"|matches "com" OR "net" OR "gov"<br>**\|** means OR|
|**(?P\<name\>)**|Name a group which can then be accessed by name rather than index|"(?P\<first\>\w+) (?P\<last\>\w+)"|Matches words and groups them. Here called "first" and "last"|
|**(?P=name)**|Used within a pattern to match against a named group|"(?P\<first\>\w+) (?P=first)"|Matches a word which repeats|
|**(?=...)**|Lookahead assertion<br>Matches if ... **does matches next**, but doesn’t consume any of the string|"Isaac (?!Asimov)"|matches "Isaac " only if it **is** followed by 'Asimov'|
|**(?!...)**|Negative lookahead assertion<br>Matches if ... **doesn’t match next**|"Isaac (?!Asimov)"|Matches 'Isaac ' only if it’s **not** followed by 'Asimov'|
|**(?<=...)**|Positive lookbehind assertion<br>Matches if current position in the string **is preceded** by a match for ... that ends at the current position|"(?<=abc)def"|Matches "def" in the string "abcdef"|
|**(?<!...)**|Negative lookbehind assertion<br>Matches if current position in the string is **not preceded** by a match for ... that ends at the current position|"(?<!abc)def"|Will **not** find a match in the string "abcdef"|

**Special Sequences**  

* A special sequence is a \\ followed by one of the characters in the list below, and has a special meaning    
* Capitals negate the function of the lowercase special sequence  

|**Character**|**Description**|**Example**|**Example meaning**|
|:---|:---|:---|:---|
|**\A**|Returns a match if the specified characters are at the beginning of the string|"\AThe"|Check if the string starts with "The"|
|**\b**|Returns a match where the specified characters are at the beginning or at the end of a word|r"\\bain"<br>r"ain\b"|Check if "ain" is present at the beginning of a WORD<br>Check if "ain" is present at the end of a WORD<br>The "r" in the beginning is making sure that the string is being treated as a "raw string"|
|**\B**|Returns a match where the specified characters are present, but NOT at the beginning (or at the end) of a word|r"\Bain"<br>r"ain\B"|Check if "ain" is present, but NOT at the beginning of a word<br>Check if "ain" is present, but NOT at the end of a word<br>The "r" in the beginning is making sure that the string is being treated as a "raw string"|
|**\d**|Returns a match where the string contains digits (numbers from 0-9)|"\d"|Check if the string contains any digits (numbers from 0-9)|
|**\D**|Returns a match where the string DOES NOT contain digits|"\D"|Return a match at every non-digit character|
|**\s**|Returns a match where the string contains a white space character|"\s"|Return a match at every white-space character (space, tab, newline)|
|**\S**|Returns a match where the string DOES NOT contain a white space character|"\S"|Return a match at every NON white-space character (NOT spaces, tabs, newlines)|
|**\w**|Returns a match where the string contains any word characters (a-z, A-Z, 0-9, and underscore _ )|"\w"|Return a match at every word character (a-z, A-Z, 0-9, and underscore _ )|
|**\W**|Returns a match where the string DOES NOT contain any word characters|"\W"|Return a match at every NON word character (characters NOT between a and Z. Like "!", "?" white-space etc.)|
|**\Z**|Returns a match if the specified characters are at the end of the string|"Spain\Z"|Check if the string ends with "Spain"|

**Sets**  

* A set is a set of characters inside a pair of square brackets **`[]`** with a special meaning  
* Each set represents 1 character position to search for, not multiple, i.e. [1-5][a-z] means search for the numbers 1-5 which are followed by a lowercase a-z e.g. 5b    
* Note **`-`** if placed at the beginning or end of a set, then the literal **`-`** character will be searched for, however when placed between 2 characters it can denote a range e.g. **`1-9`**  

|**Set**|**Description**|
|:---|:---|
|**[arn]**|Returns a match where one of the specified characters (a, r, or n) are present|
|**[a-n]**|Returns a match for any lower case character, alphabetically between a and n|
|**[^arn]**|Returns a match for any character **EXCEPT** a, r, and n|
|**[0123]**|Returns a match where any of the specified digits (0, 1, 2, or 3) are present|
|**[0-9]**|Returns a match for any digit between 0 and 9|
|**[0-5][0-9]**|Returns a match for any two-digit numbers from 00 and 59|
|**[a-zA-Z]**|Returns a match for any character alphabetically between a and z, lower case OR upper case|
|**[+]**|In sets, **`+`** **`*`** **`.`** **`\|`** **`( )`** **`$`** **`{ }`** have no special meaning, so [+] means: return a match for any + character in the string|

#### **RegEx functions**  

* The **`re`** module offers a set of functions that allows us to search a string for a match  

**match** function  

**`re.match(searchFor, textToSearch)`**  
**OR**  
**`patternVar.match(textToSearch)`**  
* Checks only at the start of a string, will **NOT** find anything matching from the middle or end of the string  
* Returns a match object   
* This is **NOT** an **iterable**  

**findall** function  

**`re.findall(searchFor, textToSearch)`**  
**OR**  
**`patternVar.findall(textToSearch)`**  
* Returns a **list of strings** containing all matches  
* Returns an **empty list** if **no match**  
* If matching groups, will only return the groups matched, not entire pattern  

**finditer** function  

**`re.finditer(searchFor, textToSearch)`**  
**OR**  
**`patternVar.finditer(textToSearch)`**  
* Returns match objects with more information and functionality than findall  

**search** function  

**`re.search(searchFor, textToSearch)`**  
**OR**  
**`patterVar.search(textToSearch)`**  
* Returns a **match object** if there is a match anywhere in the string  
* Only returns the **first match**, is **NOT** an **iterable**  
* If there is more than one match, only the first occurrence of the match will be returned  
* If no match, **`None`** is returned  

**split** function  

**`re.split(splitAt, textToSearch, maxSplit)`**  
* Returns a **list** where the string has been split at each match  
* **`maxSplit`** is optional and is the number of splits to stop at **(not the number of elements in list)**  
* If no matches, returns the original string as a single element in a list  

**sub** function  

**`re.sub(replaceThis, withThis, textToSearch, count)`**  
* Replaces one or many matches with a string  
* **`count`** is optional and is the number of replacements to stop at  
* Returns a **string**  
* If no matches, returns the original string  
* when pattern matching using **groups**, the group numbers you wish to keep can be passed and this will replace the entire matched string with the found groups:  
$\;\;\;\;$**`newStringVar = patternWithGroupsVar.sub(r'\2\3', originalStringVar)`** 
    * This example replaces the matched string with the found groups with index 2 and 3  
    * If replacing with **named groups**, use **`\g<name>`** instead of the index  

#### **Match Objects**  

* A Match Object is an object containing information about the search and the result  
* If there is **no match**, the value **None will be returned**, instead of the Match Object  

**Match object** methods  

**span** method  

**`matchObj.span()`**  
* Returns a tuple containing the start and end positions of the match  

**string** function  

**`matchObj.string`**  
* Returns the string passed into the function initially to search  

**group** method  

**`matchObj.group()`**  
* Returns the part of the string where there was a match  
* If pattern has group matching **`( | )`** then these groups can be retrieved with **indexing** or by **name** (if named, see metacharacter table above), group(0) will return everything which was matched  
* The dictionary the groups are contained in can be retrieved using **`matchObj.groupdict()`**  

#### **Flags**  

[RegEx flags link](https://www.pythontutorial.net/python-regex/python-regex-flags/)

**ignorecase** flag  

**`re.compile(patternToMatch, re.IGNORECASE)`**  
* Can be added in with the pattern to be matched  
* Flag will match pattern regardless of upper or lower case characters  
* Shorthand **`re.I`** can be used too  

**dotall** flag  

**`re.compile(patternToMatch, re.DOTALL)`**  
* By default **`.`** matches any characters except a newline. The re.DOTALL makes the **`.`** match all characters **including a newline**  
* Shorthand **`re.S`** can be used too  

**multiline** flag  

**`re.compile(patternToMatch, re.MULTILINE)`**  
* The re.MULTILINE makes the **`^`** match at the beginning of a string and at the beginning of each line and $ matches at the end of a string and at the end of each line  
* Shorthand **`re.M`** can be used too  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>**Tuples:**</center>

**`tupVar = (ele1, ele2, ele3)`**
* **Round brackets**
* Compound data types
* **Ordered sequence**
* Comma separated elements within parenthesis, can contain **`str`**, **`int`** and **`float`**
* **Immutable**
* **Concatenate** tuples with round brackets **`newTupVar = tup1Var + (newEle1, newEle2)`**

---

**Sorted** function  

**`outListVar = sorted(tupVar, key=None, reverse=False)`**  
* Use function to sort a tuple, list or set, but note it will **output as a list**  
* **`Reverse`** is **optional** and set to False if not supplied  
* **`key`** is **optional** and is usually a function when passed, this will be used on each **value in the list** to determine the resulting order, Note this can be used to access values in a list of dictionaries for sorting    
* **`key`** will be used to determine sort order, but **original values** will be **used in output**  
* A new variable must be assigned to save change  
* **`sorted`** function does not work on **`int`** and **`str`** at the same time  
* **Beware** of typecasting a sorted list back to a set as a set by definition is **unordered**   

---

**sort** method  

**`tupVar.sort(reverse=False)`**  
* Similar to sorted function, however this **will affect original variable**
* Use method to sort a tuple or list but note it will **output as a list**  
* Reverse is **optional** and set to False if not supplied  
* **`sort`** method does not work on **`int`** and **`str`** at the same time  
* **Beware** of typecasting a sorted list back to a set as a set by definition is **unordered**   

---

**Join** method  

**`string.join(iterable)`**  
* Creates **strings** from iterable objects  
* Joins each **element** of an iterable (such as lists, strings, tuples, dictionaries and sets) by a **string separator**  

---

**Nest** tuples 

**`tupVar = (ele1, (nesTupVar), ele3)`**

---

**Indexing** nested tuples

**`var[outIndex][nextLayerIndex][...][lastLayerIndex]`**

---

**Unpacking** tuples  

**`var1, var2 = tupVar`**  
* Allows elements of a tuple to be assigned to variables in one line of code  
* Note there will need to be as many variables as elements or an error will occur  
* See lists for unpacking more elements than variables  
* Dictionary key-value pairs can be unpacked to tuples using the **`.items()`** method  

---

**Packing** tuples  

**`tupVar = ele1, ele2......`**  
* Packs elements into a tuple  
* See lists for packing leading/trailing elements into a single list  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Lists:</center>

**`listVar = [ele1, ele2, ele3]`**
* **Square brackets**
* Compound data types
* **Ordered sequence**
* **Mutable** --- each time a method is applied, **will change** original variable unless reassigned
* Can contain **`str`**, **`float`**, **`int`**
* Can **nest** other **lists**, **tuples** and **other data structures**
* **Concatenate** lists with square brackets **`newListVar = list1Var + [newEle1, newEle2]`**

---

**Sorted** function   

**`outListVar = sorted(listVar, key=None, reverse=False)`**  
* Use function to sort a tuple, list or set, but note it will **output as a list**  
* **`Reverse`** is **optional** and set to False if not supplied  
* **`key`** is **optional** and is usually a function when passed, this will be used on each **value in the list** to determine the resulting order, Note this can be used to access values in a list of dictionaries for sorting    
* **`key`** will be used to determine sort order, but **original values** will be **used in output**  
* A new variable must be assigned to save change  
* **`sorted`** function does not work on **`int`** and **`str`** at the same time  
* **Beware** of typecasting a sorted list back to a set as a set by definition is **unordered**   

---

**sort** method  

**`listVar.sort(reverse=False)`**  
* Similar to sorted function, however this **will affect original variable**
* Use method to sort a tuple or list but note it will **output as a list**  
* Reverse is **optional** and set to False if not supplied  
* **`sort`** method does not work on **`int`** and **`str`** at the same time  
* **Beware** of typecasting a sorted list back to a set as a set by definition is **unordered**   

---

**Extend** lists

**`listVar.extend([newEle1, newEle2])`**  
* Adds each element as individual elements
* Will **change original variable** unless reassigned

---

**Append**

**`listVar.append([newEle1, newEle2])`**  
* Adds all the new elements **as only one new element** (nested list)
* Will **change original variable** unless reassigned

---

**Insert**  

**`listVar.insert(indexToInsertAt, newEle)`**  
* Inserts a element provided at index given

---

**Change** a list element

**`listVar[indexOrSlice] = newEle`**  
* Will replace the indexed or sliced element with the new element

---

**Delete**

**`del(listVar[indexOrSlice])`**
* Deletes a list element

**`del(listVar)`**
* Deletes a list

---

**split** method:  

**`listVar = strVar.split(sep=None, maxsplit=-1)`**  
* Converts string to a list of words, standard delimiter is a **space**  
* **`sep`** is the delimiter, None = **default whitespaces**  
* **`maxsplit`** is the maximum number of splits to do, -1 = **default no limit**  

---

**Join** method  

**`string.join(iterable)`**  
* Creates **strings** from iterable objects  
* Joins each **element** of an iterable (such as lists, strings, tuples, dictionaries and sets) by a **string separator**  

---

**Copy list**

**`listVar1 = listVar2`**  
* **Beware** copying by reference, when one variable is set to another, changing one element in a list on one variable will affect the other

---

**Cloning list**

**`listVar1 = listVar2[:]`**  
* **Protects** against changes in one list affecting the other

---

**Unpacking** lists  

**`var1, var2 = listVar`**  
* Allows elements of a list to be assigned to variables in one line of code  
* Note there will need to be as many variables as elements or an error will occur  
* Variables proceeded with **`*`** will be an empty list unless there are remaining elements after the manditory variables (those without **`*`** ) in which case all remaining elements will be put in this list  

---

**Packing** lists  

**`*listVar, = ele1, ele2......`**  
* With exactly the same number of variables as elements will produce a **tuple** not a list  
* To pack elements into a list, proceed variable name with a **`*`** and follow it with **`,`**  
* Other vaiables can be added to assign other elements to variables at the same time  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Dictionaries:</center>

**`dictVar = {"key1" : val1, "key2" : [listVal1, listVal2], "key3" : (tupVal1, tupVal2)}`**
* **curley brackets**
* Keys and values separated with a **colon**
* Key/value pairs are separated with a **comma**
* Type of collection
* Dictionaries have keys and values as lists have indexes and elements, but the keys do not need to be integers, they are usually characters 
* **Keys** must be **mutable and unique**
* **Keys** can **only** be **strings, numbers or tuples**
* **Values** can be **any data type**
* Values can be immutable, mutable and duplicates 

---

**Lookup dictionary value**

**`dictVar[key]`**  
* Essentially the same as indexing

---

**Get** method    

**`dictVar.get(key)`**  
* This will return the value of the key given  
* Note this will **not raise an error** if key is not present  

---

**Add dictionary value**

**`dictVar[newKey] = "newVal"`**
* Will change original dictionary variable unless reassigned

---

**Delete dictionary entry**

**`del(dictVar[key])`**  
* Will delete the entered key and its associated values  
* Can also delete entire dictionary by just providing dictVar with no key  

---

**Clear** method  

**`dictVar.clear()`**  
* Removes all elements from a dictionary but **does not** delete dictionary itself  

---

**Pop** method  

**`dictVar.pop(keyOfValueToBeRemoved)`**  
* Will remove key and value from dictionary  
* At the same time, it will **"pop" and return** the **value**  

---

**Popitem** method  

**`dictVar.popitem()`**  
* Removes **last** key and value from dictionary  
* **Pops and returns** the key-value **pair**  

---

**Change value**  

**`dictVar[keyOfValueToBeChanged] = newVal`**  
* This will replace the old value with the new value  

---

**In** command

**`keyToSearch in dictVar`**  
* Used to search a dictionary if a **key** is present or not.  
* **Case sensitive**   
* If present, it'll return True, else it'll return False
* Can also be used for Sets to check for elements

---

**View all keys**

**`dictVar.keys()`**  
* Will return all keys in a dictionary as a list-like object (<class 'dict_keys'>)

---

**View all values**

**`dictVar.values()`**  
* Will return all values in a dictionary as a list-like object (<class 'dict_values'>)

---

**items( )** method  

**`dictVar.items()`**  
* Returns a **view object** containing the **key-value pairs as tuples in a list**  
* Note this **will change as the object it references does** even when saved to a variable previously  
* Can be used in loops and dictionary comprehension  

---

**Unpacking** dictionaries  

**`var1, var2 = dictVar`**  
* Allows **keys** of a dictionary to be assigned to variables in one line of code  
* To unpack **values** use **`dictVar.values()`**  
* To unpack **key-value pairs as tuples** use **`dictVar.items()`**  
* Note there will need to be as many variables as keys or an error will occur  
* Variables proceeded with **`*`** will be an empty list unless there are remaining keys after the manditory variables (those without **`*`** ) in which case all remaining keys will be put in this list  

---

**sorting** dictionaries in a list:  

**`outListVar = sorted(listOfDictVar, key=lambda itm: itm["dictKeyToSortBy"])`**  
* Usually used to sort a tuple, list or set, but note it will **output as a list**  
* **`Reverse`** is **optional** and set to False if not supplied  
* **`key`** is **optional** and is usually a function when passed, this will be used on each **value in the list** to determine the resulting order, Note this can be used to access values in a list of dictionaries for sorting    
* **`key`** will be used to determine sort order, but **original values** will be **used in output**  
* A new variable must be assigned to save change  
* **`sorted`** function does not work on **`int`** and **`str`** at the same time  
* **Beware** of typecasting a sorted list back to a set as a set by definition is **unordered**   

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Sets:</center>

**`setVar = {"ele1", "ele2", "ele3"}`**
* **Curley brackets** 
* Sets only have **unique elements**
* Type of collection   
* **Unordered** meaning element positions are not recorded     
* Duplicates can be present in the creation of a set, but there will only be one unique element once the set is created

---

**Set** function

**`set(listVar)`**  
* Will convert a list to a set (typecasting)

---

**Sorted** function  

**`outListVar = sorted(setVar, key=None, reverse=False)`**  
* Use function to sort a tuple, list or set, but note it will **output as a list**  
* **`Reverse`** is **optional** and set to False if not supplied  
* **`key`** is **optional** and is usually a function when passed, this will be used on each **value in the list** to determine the resulting order, Note this can be used to access values in a list of dictionaries for sorting    
* **`key`** will be used to determine sort order, but **original values** will be **used in output**  
* A new variable must be assigned to save change  
* **`sorted`** function does not work on **`int`** and **`str`** at the same time  
* **Beware** of typecasting a sorted list back to a set as a set by definition is **unordered**  

---

**Update** method  

**`setToBeUpdated.update(setToGetElementsFrom)`**  
* Updates a set by **adding** items from another set  

---

**Join** method  

**`string.join(iterable)`**  
* Creates **strings** from iterable objects  
* Joins each **element** of an iterable (such as lists, strings, tuples, dictionaries and sets) by a **string separator**  

---

**Add** method  

**`setVar.add(newEle)`**  
* Will add a new element to a set
* If same element is added twice, nothing will happen as cannont have duplicates

---

**Remove** method  

**`setVar.remove(ele)`**  
* Will remove element from a set  
* Note this **will raise an error** if element to be removed is not present  

---

**Discard** method    

**`setVar.discard(ele)`**  
* This will remove element from a set  
* Note this will **not raise an error** if element to be removed is not present  

---

**In** command  

**`eleToSearch in setVar`**  
* Can be used to search a set if an **element** is present or not.  
* **Case sensitive**   
* If present, it'll return True, else it'll return False
* Can also be used on Dictionaires to check for keys

---

1. **Union:** $C=A\cup B$. $C$ is the set obtained by merging $A$ and $B$: $a,b \in C$
1. **Intersection:** $D=A\cap B$. $D$ is the set obtained by taking the common elements from A and B. This means that if $a\in A, b\in B$, then $a \in D$ if and only if $a=b$

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/86/A_union_B.svg/1280px-A_union_B.svg.png" width="20%" style="background-color:white">

If $A$ and $B$ do not have elements in common, then they are said _disjoint_: $A\cap B = \emptyset$, where $\emptyset$ denotes the empty set (the set with no elements).

If $A\cap B = A$, this means that all the elements in $A$ are contained in $B$. Therefore, if $B$ contains $A$, then it is denoted as $A\subset B$ (or $A\subseteq B$ depending on the case).

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/Venn_A_subset_B.svg/1024px-Venn_A_subset_B.svg.png" width="20%" style="background-color:white">

---

**Intersection** method  

**`intersection_SetVar = set1_Var & set2_Var`**  
* Uses ampersand operator **`&`**  
* Compares set1 and set2 elements, returning the common elements in the new variable

---

**Union** method  

**`union_setVar = set1_Var.union(set2_Var)`**  
* Combines all of set1 and set2 elements into a new set variable

---

**Difference** method  

**`difference_setVar = set1_Var.difference(set2_Var)`**  
* Elements that are **only in set1** are returned in a new set variable

---

**Symmetric Difference** method  

**`symmetric_differenceSetVar = set1.symmetric_difference(set2)`**  
* Returns **all** elements that **only** appear in one or other of the sets

---

**Issubset** method  

**`set_to_check.issubset(against_this_set)`**  
* Checks if a set is a subset and all of its elements are contained in another set
* Returns True or False

---

**Issuperset** method  

**`set_to_check.issuperset(against_this_set)`**  
* Checks if a set is a superset and contains a minimum of all elements of another set
* Returns True or False

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Branching:</center>

* Has <ins>**OPTIONAL**</ins> **round brackets** followed by <ins>**COMPULSARY**</ins> **colon**  
* Must use comparison operator in test argument, **Not** just regular operator e.g., **`=`**  
* Variable to be tested must be defined **prior** to "if statement"  

---

**If** statement  

**`if(test_argument):`**  
    **`    when_true_do_this_and_continue (note indent)`**  
**`when_false_continue_from_here (note no indent)`**  
* When "True", **both** true and false branches will be actioned
* When "False", **only false** branch will be actioned
* **Must Not** indent false branch or it will be deemed part of true branch


---

**Else** statement  

**`if(test_argument):`**  
    **`    when_true_do_this_and_continue (note indent)`**   
**`else:`**  
    **`    when_false_do_this_and_continue (note indent)`**  
**`then_continue_from_here (note no indent)`**  
* "Else" branch will **only** be done when "if" argument is "False"  
* Program will continue from line after "else" branch that is **Not** indented after completing relevant branch

---

**Elif** statement  

**`if(test_argument):`**  
    **`    when_true_do_this_and_continue (note indent)`**  
**`elif(test_argument_when_false):`**  
    **`    when_true_for_second_argument_do_this_and_continue (note indent)`**  
**`else:`**  
    **`    when_false_do_this_and_continue (note indent)`**  
**`then_continue_from_here (note no indent)`**  
* Continues "if" statement without ending code block as would happen with a further "if" statement
* "Elif" branch will **only** be done when previous "if" argument and previous "elif" arguments in block are "false"   
* Program will continue from line after "else" branch that is **Not** indented after completing relevant branch

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Logic Operators:</center>

* Takes boolean values and produces different boolean values  
* Can be combined with branching

---

**not** operator  

**`not(test_argument)`**   
* Returns opposite boolean value to test argument

---

**or** operator  

**`(test_argument_1) or (test_argument_2)`**  
* Returns "True" when **either or both** arguments are **"True"**  
* **Inclusive** or  

---

**and** operator  

**`(test_argument_1) and (test_argument_2)`**  
* Returns "True" when **Both** arguments are **"True"**

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Loops:</center>

* Must include **colon**  
* Must **indent** loop "block" ("do_this") section 

---

**for** loop  

**`for var in sequence :`**  
    **`    do_this_with_var`**  
* Used when number of times loop is to be executed is **known** or **fixed** 
* "Var" is a variable that is used for iterating over a "sequence", on every iteration it takes the next value from "sequence"  until the end of "sequence" is reached  
* "Var" is **not required** to be defined prior to loop as loop will automatically increase incrementally as per sequence given   

---

**Parallel iteration**  

**`for a,b..... in zip(iterableA, iterableB.....):`**  
    **`    do something with a, b etc.`**  
* **zip** can be used to **iterate** over **multiple iterables in parallel** when used with **for loop**  

---

**List comprehension**  

**`[eleToReturn for var in sequence condition]`**  
* Keywords **for** and **in** are compulsary  
* List comprehensions are given in **square brackets**  
* Must assign to a new variable to save changes  
* `sequence` is the **sequence** to **extract each variable** from, can be a range or a list etc  
* `var` is the **variable** to test against the condition given from the sequence
* `eleToReturn` will usually be the same as `var`....this is what will be **entered in the return list if condition is met**  

---

**Dictionary comprehension**  

**`{elementToReturn for key,value in dictVar.items() condition}`**  
* Similar to list comprehension, but contained in **`{}`** brackets  
* **elementToReturn** will usually be **key:value**, or maybe just **key**  
* **.items()** method is used to **obtain key:value pair** to carry out condition check on  
* **value** can be used in the **condition** statement  

---

**while** loop  
  
**`while condition_statement :`**  
    **`    do_this`**  
* Used when number of times loop will need to be executed is **unknown**  
* "While" loop will continue whilst condition_statement remains "True"     
* Ensure to **define** any variable used in "condition_statement" **prior** to loop to "get into loop"  
* Ensure to **adjust the value** of any variable used in "condition_statement" **within** loop, otherwise may create an infinite loop  

---

**break** statement

**`for var in sequence:`**  
    **`    if (test argument):`**  
    **`        break  (exit loop when condition is True)`**  
    **`    else:`**  
    **`        do_this`**  
* Break statement in Python is used to **bring the control out of the loop** when some external condition is triggered  
* Statement is put inside the loop body (generally after if condition)  

---

**continue** statement  
  
**`for var in sequence:`**  
    **`    if (test argument):`**  
    **`        continue (do next iteration when condition is True)`**  
    **`    else:`**  
    **`        do_this`**  
* Continue statement is opposite to that of break statement, instead of terminating the loop, it **forces the program to execute the next iteration of the loop**  
* Statement is put inside the loop body (generally after if condition)  

---

**pass** statement  
  
**`for var in sequence:`**  
    **`    pass (do nothing and continue program)`**  
* Generally used as a **placeholder for future code**  
* When the pass statement is executed, nothing happens, but you avoid getting an error when empty code is not allowed  
* Difference between pass and comment is that comment is ignored by the interpreter whereas pass is not ignored  
* Empty code is not allowed in **loops, function definitions, class definitions, or in if statements**   

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Exception Handling:</center>

**exceptions:**  
* Exceptions are a Python object that represents an **error**  
* When a Python script raises an exception, it must either **handle the exception immediately otherwise it terminates and quits**  

---

[**List of Built-in Exceptions**](https://docs.python.org/3/library/exceptions)

---

**try except (else finally)** statement:  

**`# potential code before try catch`**

**`try:`**  
    **`    try_this`**  
**`except exception_name:`**  
    **`    run_this_if_named_exception_occurs`**  
**`except (another_exception_name, a_further_exception_name):`**  
    **`    run_this_if_any_named_exception_occurs`**  
**`except:`**  
    **`    run_this_if_any_other_exception_occurs`**  
**`else:`**  
    **`    run_this_if_no_exceptions`**  
**`finally:`**  
    **`    run_this_regardless_of_exceptions`**  
* All **colons** are **manditory**  
* Using **"except"** statement **without specifying exceptions** can be **bad practice** as will catch all error without notifying programmer of root cause of problems that may occur  
* **Multiple exception names** can be entered into one except branch in **round brackets seperated by comma**
* **Else** branch will run **if no errors** are encountered   
* **Finally** branch will run **regardless of errors** encountered  
* Can have 1 or many except branchs, if including except branch without specifying exceptions, this must be **last of the except branchs**  
* **else** branch is **optional**  
* **finally** branch is **optional**  
* Can use further indented "try" branches instead of "else" branch, **however is not good practice**

---

**raise** exception  

**`raise Exception_Name ("info on why exception raised")`**  
* **Bad practice** to handle all Exceptions with a **single statement, better to be specific**  
* Can manually raise or cause an exception to be thrown with keyword **"raise"**  
* "exception_name" should be a built in exception  
* **Optional** information can be provided in **round brackets** but ideally should provide more information on why exception was raised  
* **Different errors** can be raised, note has **capital letter** at beginning. These include (but not limited to):  
    * **ValueError** 
    * **TypeError**  
    * **Exception**  

---

**Create custom exception**  

**`class ExceptionName(Exception):`**       # inherits from Exception  
$\;\;\;\;$ **`def __init__(self,*args,**kwargs):`**  
$\;\;\;\;\;\;\;\;$**`super().__init__(*args,**kwargs)`**  
* Creates custom Exception that can be raised the same as any other  
* Only benefits of having your own exception is to make code more readable and to write for aimed error handling  

---

**Traceback**  

A python module that provides a standard interface to extract, format and print stack traces of a python program  
When it prints the stack trace it exactly mimics the behaviour of a python interpreter  
Useful when you want to print the stack trace at any step, usually seen when an exception occurs  
Since a traceback gives all the information regarding the exception it becomes easier to track one and fix it  

**`import traceback`**  

**`try:`**  
$\;\;\;\;$**`some code`**  
**`except:`**  
$\;\;\;\;$**` traceback.print_exc()`**  

---

**assert**  

**`try:`**  
$\;\;\;\;$**`assert condition, errorMessage`**  
**`except AssertionError as ae:`**  
$\;\;\;\;$**`other code`**  
$\;\;\;\;$**`raise ae`**  
* **Keyword** **`assert`** lets you test if a condition in your code returns True, if not, the program will raise an AssertionError  
* assert **does nothing when** condition returns **True**  
* assert can be done outside of a try, except, but shown here to show calling AssertionError created  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center> Useful Built-in Functions:</center>

**range** function    

**`range(start,stop,step)`**  
* Represents a range of immutable sequence of numbers  
* "stop" **IS required**, will stop at and **NOT** include that value   
* "start" is **NOT required**, set to "0" if not given  
* "step" is **NOT required**, set to "1" if not given  
* Will print as a **"range"** unless typecasted  

---

**enumerate** function  

**`enumerate(iterable, start=0)`**
* Outputs **(index value + start value)** with each element stored as a tuple, whilst the entire object is stored as an **enumerate** list  
* "iterable" can be any object that supports iteration  
* "start" is **NOT** required, it is the value from which the counter is to be started, by default it is "0"   

---

**count** method  

**`var.count(object)`**  
* Counts number of times "object" occurs in "var"  

---

**sum** function  

**`sum(iterable, start=0)`**  
* Sum of elements in "iterable"  
* Starts at **value** given for start, if no value given, defaults to "0"  

---

**isnumeric( )** function  

**`var.isnumeric()`**  
* Checks variable to see if it is a number and returns a boolean  
* Useful for checking input before converting to an int  

---

**isinstance( )** function  

**`isinstance(var, typeToCheckFor)`**  
* Checks given variable if it is of type given, returns **boolean**  
* Considers **subclasses** too unlike type(x) == .....  

---

**zip** function  

**`zip(iterable1, iterable2)`**  
* **Combines** items one at a time taking **first from iterable1, then from iterable2**  
* **Iterable with** the **least** items **defines** the **length of output** zip object  
* If iterables are **tuples** and **one** has **exactly 1 object** whilst the other has multiple, it will be **elements** from that object which will be used  
* **NOTE** zip objects can **ONLY** be **iterated** over **ONCE before it is exhaused** and the zipped object will be **empty**   
* Can **avoid exhausting** the zipped object by **typecasting** to a list for example **when assigning to a variable** rather than when using the zipped object.  

**Create tuples from zip object**  

**`tupVar1, tupVar2, tupVar3... = zip(*zippedObject)`**  
* The **`*`** defines splitting function  
* As long as the zippedObject has not been iterated over already, this will **split each zipped elements into defined tuples**  
* Must define same number of **tuples as components in each zippedObject elements**  

---

**map** function  

**`map(function, iterables)`**  
* Executes a specified function for each item in an iterable  
* **`iterables`** are a sequence, collection or an iterator object  
* Can send as many iterables as you like, just make sure the function has one parameter for each iterable  
* Outputs as a **map object**  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center> Building Functions:</center>

Build functions to replace **repeating lines of code**  

**functions**  

* Functions are a block of code that is also called by its name (**independent**)
* The function can have different parameters or may not have any at all. If any data is passed, they are **passed explicitly**  
* It **may or may not** return any data  
* Function does not deal with class and its instance concept  

**difference between methods and functions**:  

* Functions and Methods both look similar as they perform in almost similar ways, but the key difference is the concept of ‘Class and its Object‘  
* Functions can be called only by its name, as it is defined independently  
* Methods can’t be called by its name only, we need to invoke the class by a reference of that class in which it is defined, i.e., method is defined within a class and hence they are dependent on that class and so methods need to be called on an object    
* A method may alter an object’s state, but Python function usually only operates on it, and then prints something or returns a value  

**typical function**:  
**`func_name(arguments)`**  
  
**typical method**:  
**`obj.meth_name(arguments)`**  

---

**define function**  

**`def funcName(para1, para2, *variadicPara, keywordArg=value, **kwargs):`**  
$\;\;\;\;$**`"""description of func for help()"""`**  
$\;\;\;\;$**`code block`**  
$\;\;\;\;$**`return "this"`**  
* Function name should be descriptive and begin with a lower case letter with words separated by underscores  
* Parameters ("para") is what will be taken from program and applied in code block, these are **optional**   
* Must include **colon**  
* **Optional** help description is in **triple quotes**  
* Code block is **indented**  
* Can have **single or multiple "positional" parameters** seperated with a **comma**  
* Positional arguments are defined by **name only**  
* **Positional** arguments can be passed in a **different order** by **assigning to parameter name when calling function**  
* **Positional arguments** can have **multiple argument entries** when parameter is preceded with a **`*`** allowing unlimited number of arguments, this is defined in description as **`*args`**  
* **Positional arguments** are implemented as a **tuple**  
* Keyword arguments are defined by **name and default value** (after the assignment operator). These must be **after** any **positional arguments**  
* **Keyword arguments** can take **unlimited keyword arguments** when parameter is preceded with **`**`**. These must be **after** any **positional arguments**. This is defined in description as **`**kwargs`**
* **Keyword arguments** are implemented as **dictionaries**  
* **Beware** of functions where code contains **multiplication** **`*`**, if a string is passed to function, could cause unexpected errors  
* **Return** statement exits a function, optionally passing back a value. It is not required in some circumstances, however without it can cause errors in passing data back to the main program  
* Functions that perform no task will return "none" 

---

**calling** a function    

**`funcName(argument)`**  
* Argument value is sent to function parameter  
* Function result can be assigned to a variable or printed in usual way  
* **Without parentheses** will return function **parameter format**  

---

**help** on a function   

**`help(funcName)`**  
* Will return "help description" part of function and module function is in  

---

**global and local scope variables**  

* Variables can be **local** to the function, requires no defining as such, these will **not have name conflicts** with variables already defined in main program, they will be seperate allowing them to have same variable names with different stored values which are deleted after function is executed  
* Variables can be **global**, define variable name preceded by **"global"** in the function, in this case they will not be deleted after function is executed, **alternatively** do not define variable inside function requiring it to be defined prior to function being run in the main program  

---

**Lambda functions**  

**`functionName = lambda arguments : expression`**  
* Lambda functions are small anonymous functions.  
* Can take **any** number of **arguments**  
* Can **only** have **one expression**  
* Can be used inside another function  
* If, else in expression **does not** contain colon **`:`**  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Classes, Objects and Methods:</center>

**classes**  

* Classes are **user-defined types** or blueprint from which objects are created  
* They provide a means of bundling data and functionality together  
* Creating a new class creates a **new type of object**, allowing new instances (objects) of that type to be made  
* Each class instance can have **attributes** attached to it for **maintaining its state**  
* Class instances can also have **methods (defined by its class) for modifying its state**

---

**define class**  

**`class ClassName(object):`**  
$\;\;\;\;$**`"""help() description in triple quotes"""`**  

$\;\;\;\;$**`attribbute1 = None`**  ---- Good practice to add attributes at top and assign them None for better readability  
$\;\;\;\;$**`attribute2 = None`**  

$\;\;\;\;$**`# constructor to initialize the object`**  
$\;\;\;\;$**`def __init__(self,attribute1,attribute2 = optionalDefautValue):`**  
$\;\;\;\;\;\;\;\;$**`self.attribute1 = attribute1`**  
$\;\;\;\;\;\;\;\;$**`self.attribute2 = attribute2`**  
        
$\;\;\;\;$**`# method(s) to access and modify the objects argument state values`**  
$\;\;\;\;$**`def meth_Name(self, parameter):`**  
$\;\;\;\;\;\;\;\;$**`self.attribute1 = code_to_modify_attribute1 (e.g.; self.attribute1 = self.attribute1 + parameter)`**  
$\;\;\;\;\;\;\;\;$**`return(self.attribute1)`**   
* Created by keyword **class**  
* Class names should be **Capitalised**  
* Must include **colon**  
* Must include the term **object**  
* **`__init__`** is a special method which is called as a constructor when an object is created from a class and it allows the class to **initialize the attributes** of the class, has **double underscores** either side  
* **`self`** is a parameter in function and the user can use another parameter name in place of it, however it is advisable to use self because it increases the readability of code  
* **`self`** represents the instance of the class. By using the **`self`** keyword we can access the attributes and methods of the class in Python. It binds the attributes with the given arguments  
* Can include **default values** for attributes by setting them with **`=`** in the constructor  
* **Attribute** = variable of any type that belongs to or is declared directly in a class  
* Attributes are always public and accessed by using dot (.) operator e.g.; className.attribute1  
* **Parameter** = temporary variable names within functions, placeholders for the argument it is passed  
* **Argument** = value that is assigned to that temporary variable

---

**objects**  

* An object is an instance of a class. A class is like a blueprint while an instance is a copy of the class with actual values. It’s not an idea anymore  
* An object consists of :  
    **Identity** : It gives a **unique name** to an object and enables one object to interact with other objects  
    **State** : It is represented by **attributes** of an object. It also reflects the properties of an object  
    **Behavior** : It is represented by **methods** of an object. It also reflects the response of an object with other objects  

---

**creating** an object  

**`objVar_Name = ClassName(attribute1_value, attribute2_value)`**  
* Object constructor consists of the name of the class as well as the parameters to be passed  

---

**Inheritance**  

* Unlike other languages, Python can inherit from **multiple classes**  
* Python **does not** have **method overloading** (several methods with same name but different signature)  

**`class ChildClassName(ParentClassName1, ParentClassName2):`**  
$\;\;\;\;$**`pass`**  
* Inheriting from multiple classes is defined after class name in parentheses  
* Keyword pass will allow child class to inherit all parent classes properties and methods when you do not want to add any new ones  

**`class ChildClassName(ParentClassName):`**  
$\;\;\;\;$**`def __init__(self, attribute1, attribute2):`**  
$\;\;\;\;\;\;\;\;$**`# add properties etc.`**  
* When the \_\_init\_\_ function is used, it will automatically **override the parents \_\_init\_\_ function**  

**`class ChildClassName(ParentClassName):`**  
$\;\;\;\;$**`def __init__(self, attribute1, attribute2):`**  
$\;\;\;\;\;\;\;\;$**`ParentClassName.__init__(self, attribute1, attribute2)`** 
* A call to the parents \_\_init\_\_ function will allow the child class to **inherit the \_\_init\_\_ function**  
* Note the **.** before the \_\_init\_\_ call  
* Note **no parentheses** after ParentClassName  

**`class ChildClassName(ParentClassName):`**  

$\;\;\;\;$**`def __init__(self, attribute1, attribute2):`**  
$\;\;\;\;\;\;\;\;$**`super().__init__(attribute1, attribute2)`**  
* The super() function will allow the child class to **inherit all the properties and methods** of the parent class  
* When wanting to **modify the output** of a parent method when **overriding a method**, use super() call in the method  
* Further attributes for the child class can be passed in its own \_\_init\_\_ and set in the normal way (along with further methods) after and below the super call  
* Note Python 2.x and earlier requires calls to the super class be defined as  
    **`super(Derived_Class_Name, self).__init__(Parameters_of_Super_Class_Constructor)`**  

---

**Method Resolution Order (MRO)**:  

**`ClassName.mro()`**  
**OR**  
**`ClassName.__mro__`**  
* Defines the order in which the base classes are searched when executing a method  
* Old style (Python 2.x and older) classes use DLR or depth-first left to right algorithm (depth first, then left to right) whereas new style classes use Linearization. Child classes are preceeded before their parents, and left to right is searched for each depth level before proceeding to the next parent  

A  &emsp;&emsp;&emsp;&emsp;&ensp;&nbsp;&nbsp; **5th:** Base class is searched last  
|&ensp;\  
|&emsp;B  &emsp;&emsp;&emsp;&emsp; **4th:** Next level up parent is searched (again left to right if more than one)  
|&emsp;&ensp;&nbsp;\  
C&emsp;&emsp;D  &emsp;&emsp;&ensp; **2nd & 3rd:** Immediate parent classes are searched left to right after child class    
|&emsp;&ensp;&nbsp;/  
|&emsp;/  
&nbsp;E  &emsp;&emsp;&emsp;&emsp;&emsp; **1st:** Child class is searched first  

---

**accessing attribute** values  

**`objVar_Name.attributeName`**  
* This will display the current value of the attribute stored for the object  

---

**changing data attributes** directly  

**`objVar_Name.attributeName = new_AttributeValue`**  
* This will set a new value of the attribute for the object  

---

**methods**  

* Methods are called by its name, but it's associated to an object (**dependent**)  
* A method is **implicitly passed to the object** on which it is invoked  
* It **may or may not** return any data  
* Methods can operate on the data (instance variables) that is contained by the corresponding class

---

**difference between methods and functions**:  

* Functions and Methods both look similar as they perform in almost similar ways, but the key difference is the concept of ‘Class and its Object‘  
* Functions can be called only by its name, as it is defined independently  
* Methods can’t be called by its name only, we need to invoke the class by a reference of that class in which it is defined, i.e., method is defined within a class and hence they are dependent on that class and so methods need to be called on an object    
* A method may alter an object’s state, but Python function usually only operates on it, and then prints something or returns a value  

**typical function**:  
**`func_name(arguments)`**  
  
**typical method**:  
**`obj.meth_name(arguments)`**  

---

**calling** a method  

**`objVar_Name.meth_Name(argument)`**  
* This will call the method named and change or interact with the data attributes stored for the object as denoted by the method code block  
* **Without parentheses** will return method **parameter format**  

---

**Method and attribute types (access modifiers)**  

* Python **does not** implement access modifiers as such, **everything is visible to everyone always**  
* Access to variables or functions can be limited in python, but note **above**  

**Public**:  
Attribues and methods defined without any underscores, these are accessible from outside the Class through an object of the class.  

**Protected**:  
Attributes and methods defined with **1 leading underscore**  
The members declared as Protected are accessible from outside the class but only in a class derived from it that is in the child or subclass.  

**Private**:  
Attributes and methods defined with **2 leading underscores**  
These members are only accessible from within the class. No outside Access is allowed.  


Though note **Python internally renames** the property's and method's names starting with **`__`** with   
**`_CLASSNAME__PROPERTYNAME/METHODNAME`**  
This means they **can actually be accessed** (see above)  

**Special Methods aka Dunder Methods**:  
Methods defined with **2 leading AND 2 trailing underscores**  
These are typically reserved for Python built in and predefined methods and it is **discouraged to create your own** to avoid clashes  

---

**Special methods**  

**<center>Arithmetic:<center>**  

|**Operator**|**Description**|**Special Method**|
|:---:|:---|:---|
|+|Addition|\_ \_add_ _(self,other)|
|-|Subtraction|\_ \_sub_ _(self,other)|
|\*|Multiplication|\_ \_mul_ _(self,other)|
|/|Division|\_ \_div_ _(self,other)|
|%|Modulus|\_ \_mod_ _(self,other)|
|\*\*|Exponentiation|\_ \_pow_ _(self,other)|
|+=|In-place addition|\_ \_iadd_ _(self,other)|
|-=|In-place subtraction|\_ \_isub_ _(self,other)|
|\*=|In-place multiplication|\_ \_imul_ _(self,other)|
|/=|In-place division|\_ \_idiv_ _(self,other)|
|%=|In-place modulus|\_ \_imod_ _(self,other)|
|\*\*=|In-place exponentiation|\_ \_ipow_ _(self,other)|  

**<center>Comparison Operators:<center>**  

|**Operator**|**Description**|**Special Method**|
|:---:|:---|:---|
|==|Equal|\_ \_eq_ _(self,other)|
|!=|Not Equal|\_ \_ne_ _(self,other)|
|>|Greater than|\_ \_gt_ _(self,other)|
|>=|Greater or equal than|\_ \_ge_ _(self,other)|
|<|Less than|\_ \_lt_ _(self,other)|
|<=|Less or equal than|\_ \_le_ _(self,other)|

**<center>Type Conversion Operators:<center>**  

|**Operator**|**Description**|**Special Method**|
|:---:|:---|:---|
|str( )|String representation|\_ \_str_ _(self)|
|repr( )|Printable representation (very similar to str())|\_ \_repr_ _(self)|
|int( )|Integer representation|\_ \_int_ _(self)|
|float( )|Float representation|\_ \_float_ _(self)|

**<center>Sequence Operators<center>**  
    
|**Operator**|**Usage**|**Description**|**Special Method**|
|:---:|:---|:---|:---|
|[ ]|myObj [ key ]|Get an item from myObj|\_ \_getitem_ _(self, key)|
|[ ]=|[ key ] = value|Set an item in myObj|\_ \_setitem_ _(self, key, value)|
|del|del myObj[ key ]|Deletes an item in myObj|\_ \_delitem_ _(self, key)|
|[ : ]|myObj[ i : j ]|Get a slice from myObj|\_ \_getslice_ _(self, i, j)|
|[ : ]=|myObj[ i : j ]=values|Set a slice in myObj|\_ \_setslice_ _(self, i, j, values)|
|in|value in myObj|Returns True if value is in myObj|\_ \_contains_ _(self, value)|
|len|len(myObj)|Returns the length of myObj|\_ \_len_ _(self)|

---

**Getters and Setters**:  

**Getter:**  
**`@property`**  
**`def attributeName(self):`**  
$\;\;\;\;$**`return self.__privateAttribute`**  

**Call with:**  
**`obj.attributeName`**  

**Setter:**  
**`@attributeName.setter`**  
**`def attributeName(self, newVal):`**  
$\;\;\;\;$**`validataion checks prior to setting...`**  
$\;\;\;\;$**`self.__privateAttribute = newVal`**  

**Set with:**  
**`obj.attributeName = newVal`**  

* **`attributeName`** is the name of the method or attribute to set using the decorator and should not be private here, however ensure to call the private attribute and set accordingly within the method  
* Can be done in a similar way to Java with seperate methods for getting and setting attributes, however this means methods will need to be explicitly called otherwise relevant validation checks will not be carried out, or even the wrong attribute may be changed  
* In Python, we can use the **@property** decorator as the getter, and **@attributeName.setter**  

---

**dir** function  

**`dir(objVar_Name)`**  
* This returns a list of the attributes and methods of the named object  

---

**Duck typing**  

* In Python, an object or classes type is of lesser importance than the methods or attributes it defines  
* If two or more classes contains a certain attribute or method, they can all be passed to the same function which makes use of that attribute or method without issue  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Command line arguments:</center>

**Using sys**  

**`import sys`**  
**`for i,v in enumerate(sys.argv):`**  
$\;\;\;\;$**`print("Parameter #{}: {}".format(i,v))`**  
* Iterates over command line parameters  
* **`argv[0]`** is the **script name** (it is operating system dependent whether this is a full pathname or not)  

**argparse**  

**`import argparse`**  


**`parser = argparse.ArgumentParser(prog=None, description=None)`**  
* **`prog`** = name of program (default: sys.argv[0])  
* **`description`** = Description of what the program does  


**`parser.add_argument('--parameterFullName', '-p', dest='var', type=str, help='Some help info', required=False, default='defaultValue', choices
=['ele1','ele2'], nargs=intNumberOfArgs, metavar='nameOfExpectedValue', action='append')`**  
* **`-p`** is an abreviation (leading with a single **`-`** ) of **`parametersFullName`** ( leading with double **`--`** ) and either can be used to provide the input  
* **`dest`** is the variable name you want to save the parameter to (accessed: args.var), if none given, name is inferred from the option  
* **`choices`** option limits arguments to the given list  
* **`nargs`** specifies the exact number of command-line arguments that should be provided, **`'*'`** specifies variable  
* **`metavar`** option gives a name to the expected value in error and help outputs  
* **`action`** allows grouping of repeating inputs  



**`args = parser.parse_args()`**  
* Adds arguments to a variable  

**`argVar = args.dest`**  
* Access variable 'dest' and saves to variable, other parameters can be accessed in a similar way  

**exit codes**  

**`import sys`**  

**`{code}`**  

**`sys.exit(intExitCode)`**  
* Usually used after an if statement  
* If no exit code provided, then system exit code **`0`** is used which is considered **successful termination**  
* A string can also be passed as an exit code message, and will have the exit code **`1`**  
* In Windows, the exit code from the last program run can be obtained in PowerShell using command **`echo $lastexitcode`**  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>PIP:</center>

* PIP is a package manager for Python that allows you to install and manage additional libraries and dependencies that are not distributed as part of the standard library  
* A package is a unit of distribution that can contain a library or an executable or both  
* a library is a set of modules which makes sense to be together and that can be used in a program or another library  

---

**get pip version**  

**`!pip --version`** 
* Returns version of PIP

---

**list installed packages**  

**`!pip list`**  
* Returns a list of installed packages  

---

**install PIP package**  

**`!pip install package_name`**  
* Will install package named  
* Once installed, packages / modules can be imported  

---

**uninstall PIP packages**  

**`!pip uninstall package_name`**  
* Will uninstall package named  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Working with files</center>

### <center>Opening and Reading Files:</center>

**open** function  

**`open("file", "mode")`**  
* Built in function  
* Opens a file and returns a corresponding file object  
* Both **"file" and "mode"** must be entered as a **string within parentheses**  
* "file" is a path-like object made up of **file name and directory**  
* "mode" is an **optional** string which specifies which mode file is to be opened in, common modes include:<br>
**`r`* = **reading (default mode)**, will **fail** if file does **not exist**<br>
**`a`* = **appending**, stream is positioned at **end of file**, **creates new file** if file does **not exist**<br>
**`w`* = **writing**, will **truncate file first** (empty contents), or **create new file** if file does **not exist**  
**`+`* = **updating**, add **`+`** after any usual mode e.g. `w+` to allow **reading and writing**, note `w+` mode will still truncate file first, `r+` will overwrite what is in streams way  

---

**file object**

**`varFile_Obj = open(file, mode)`**  
* **Information** about the file can be obtained by setting the open function to a **file object variable**  
* "mode" is again **optional**  
* Once a file is opened and data saved as a file object, then the following methods can be used on it  
* **MUST close** file object once finished using file unless using with statement (see below)

---

**name** method

**`varFile_Obj.name`**
* Returns **name** of the file 

---

**mode** method  

**`varFile_Obj.mode`**  
* Returns **mode** of file object  

---

**close** method  

**`varFile_Obj.close()`**  
* **Closes** a file  
* **ALWAYS** close a file after opening with the above function 
* Note it is the **file object variable** that is closed  
* Must include **parenthesis**  

---

**closed** method  

**`varFile_Obj.closed`**  
* Checks if a file is **closed** and returns **True** if is

---

**with** statment  

**`with open(file, mode) as varFile_Obj:`**  
    **`    var = varFile_Obj.read()`**  
* **Better practice** to use **"with" statment** to open files as it **automatically closes** them 
* Code will **run everything indented, then close file**  
* Can check file is closed as well as print file content, but **cannot read from file** outside of code block  
* Must include **colon**

---

**read** method  

**`.read()`**  
* File read as a **whole** and stores values in the variable "var" as a **string**  
* Stream positioned at the end of the file after running   
* **Optional argument** determines **number of characters read** each time method is run moving stream position accordingly, note new line characters "\n" count as a single character  
* Stream position reset if the file is reopened 

---

**readline** method  

**`.readline()`**  
* Reads **each line** of file each time code is run and stream is updated accordingly  
* Stores values as a **string**  
* **Optional argument** determines **number of characters read** each time method is run up to **max end of line**  
* If line has **NOT** been completely read, stream will **stay in position** and continue from there next time code is run  
* Stream position reset if the file is reopened  
* Must include **colon**

---

**readlines** method  

**`.readlines()`**  
* Outputs **each line** as an **element** in a **list**  
* **Optional argument** will read **complete lines up to the end of the line** which equals the number of Characters entered, note new line characters **"\n" count as the beginning of a line**  
* Must include **colon**


```python
help(print)
```

---

using a **loop** with open  

**`with open(file, mode) as varFile_Obj:`**  
    **`    for var as varFile_Obj:`**  
    **`        var = var.strip()  # Optional to remove newline characters from file lines if not using keyword end in print function`**  
    **`        print(var, end='')`**  
* Will print out **each line** in the file as an **individual string**  
* Note function **`print()`** contains a **\n by default**, but **so will each line in the file**, can change the **keyword argument in print to `end= ''`**....**Alternatively, use** the string method **`.strip()`** to remove from each line before print function  
* **Better** method to use **`strip`** **than** **`end`** as it will remove white spaces as well which can prevent errors in reading files  

using a **loop** to print **each line** individually  

**`with open(file_name, "r") as file_obj5:`**  
$\;\;\;\;$**`i = 1      # Used as an iterator`**  
$\;\;\;\;$**`for line in file_obj5:`**  
$\;\;\;\;\;\;\;\;$**`print("Line ", i, ": ", line)`**  
$\;\;\;\;\;\;\;\;$**`i+=1`**  
* Two methods to read file line by line:  
    * Either read the file as before and break the rows manually, this can be troublesome as different systems use differnt **end-of-line** characters 
    * Or read them line by line as shown here delegating this task to the underlying library allowing code to be **cross-platform**  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <Center>Working with Files</center>

### <center>Writing to Files:</center>

**write** method  

**`file_obj.write("text_to_be_written_to_file")`**  
* Open file as detailed in section above in a writable mode  
* This will write string in argument as text in file  
* If wanting to start a new line, **add "\n"** escape character to **end of string**  
* Unless using **"with statement"**, remember to **close** file  
* No need to assign to variable as with read() method  

---

**with** statment  

**`with open(file, mode) as varFile_Obj:`**  
    **`    varFile_Obj.write("text_to_be_written_to_file")`**  
* **Better practice** to use "with" statment to open files as it **automatically closes** them 
* Code will **run everything indented, then close file**  
* Can check file is closed as well as print file content, but **cannot read from file** outside of code block  
* Must include **colon**

---

**seek** method  

**`file_obj.seek(offset, whence=0)`**  
* Used to **set** the **streams position** within a file 
* **"offset"** is **required**, determines number of characters to skip over  
* **"whence"** is **optional** and **defaults to 0**  
* whence can be set to 0 = absolute file positioning (from beginning), 1 = seek relative to current position, 2 = set stream at end of file...in Python 3 CANNOT seek backwards  
* Theres **no return value**  

---

**tell** method  

**`file_obj.tell()`**  
* Will return **current stream position**, when file is opened stream will be at 0 (beginning of file) unless opened in append mode  

---

**writing from a list**  

**`list_var = ["line1", "line2",....]`**

**`with open("file", "mode") as file_obj:`**  
    **`    for each_line in list_var:`**    
    **`        file_obj.write(each_line)`**  
* **Must** use **loop** to iterate over each element to write, **cannot write list direct** to file (writing to file needs to be a string)  
* Ensure mode opened in is a writable mode  

---

**copying files**  
  
**`with open("file", "readable_mode") as readfile_obj:`**  
    **`    with open("file2", "writable_mode") as writefile_obj:`**  
    **`        for each_line in readfile_obj:`**  
    **`            writefile_obj.write(each_line)`**  
* **Must** open file to be copied in a **readable mode** e.g. "r" or "r+"  
* **Must** open file to be written to in a **writable / appendable mode** e.g. "w" or "a"  
* Use **loop** to iterate over each line from file to be copied  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>CSV Library:<center>

**CSV files**  

* csv files are "comma-separated values" and is a structured text file  
* Each line contains an entry in the dataset  
* Each attribute is separated by a **delimiter** (typically a comma or semi-colon)  
* **Usually** the first line is the **column headers**  
* CSV files are normally created by programs that handle large amounts of data. They are a convenient way to export data from spreadsheets and databases as well as import or use it in other programs  
* Can **read** and **write** to **csv files** with **pandas**, see pandas section for more info  

---

**Reading csv files**  

csv files can be opened in the normal way (though better to use **csv** or **pandas** libraries:  
**`with open(filePath,mode) as file_objVar:`**  
$\;\;\;\;$**`text = file_objVar.read()`**  
$\;\;\;\;$**`print(text)`**  
* Note **end of line characters** are still **present**  

---

**Reading csv to a dataset list**  

csv files can also be read in splitting each line element by its delimiter and adding each line as an entry to a list  
This is **easier** to do **using the csv library** (see below)  
**`datasetVar = [ ]`**  
**`with open(filePath) as file_objVar:`**  
$\;\;\;\;$**`headerVar = file_objVar.readline()`**  
$\;\;\;\;$**`for line in file_objVar:`**  
$\;\;\;\;\;\;\;\;$**`datasetVar.append( line.split(delimeter))`**  
* **Header** can be read off as the first line outside of the for loop to its own variable  
* Each line is read one at a time before spliting each element by the given delimeter and appending the entry as an element in the dataset  
* Note **end of line characters** are still **present**  

---

**Using csv library**:  

**`import csv`**  

**`datasetVar = [ ]`**  
**`with open(filePath) as file_objVar:`**  
$\;\;\;\;$**`csvReaderObj = csv.reader(file_objVar, delimiter= delimeter)`**  
$\;\;\;\;$**`for listEntryRead/rowVar in csvReaderObj:`**  
$\;\;\;\;\;\;\;\;$**`datasetVar.append(listEntryRead/rowVar)`**  
* **`delimiter`** defaults to **`","`**  
* This method will read in the **header row** as the first element in the dataset (**index [0]**)  
* Library will **remove end of line characters**  
* **Faster than Pandas** for **small datasets (<1k rows)**  
* Though **Pandas** is **faster** for **large datasets**  

---

**Using pandas to read csv to dataframe**  

**`import pandas as pd`**  

**`df = pd.read_csv('filePath',header=None)`**  
* Reads csv file to dataframe  
* **`header`** is optional, defaults to using column names, set to none (as above) if none present in file  

---

**Writing to csv file**:  

**Better to use csv library** (see below)  
**`populatedDataset = [[entry1_ele1, entry1_ele2],[entry2_ele1, entry2_ele2]...]`**  
**`with open(filePath, 'w') as file_objVar:`**  
$\;\;\;\;$**`for line in populatedDataset:`**  
$\;\;\;\;\;\;\;\;$**`file_objVar.write(delimeterToUse.join(line)+"\n")`**  
* Writes to a csv file from a dataset (list of lists)  
* **join** method used to set delimeter between each element of an entry  
* **`\n`** used to start a new line after each entry added to file  

---

**Using csv library**:  

**`populatedDataset = [[entry1_ele1, entry1_ele2],[entry2_ele1, entry2_ele2]...]`**  
**`with open(filePath, 'w') as file_objVar:`**  
$\;\;\;\;$**`csv_writerObj = csv.writer(file_objVar, delimiter= delimiter)`**  
$\;\;\;\;$**`for line in populatedDataset:`**  
$\;\;\;\;\;\;\;\;$**`csv_writerObj.writerow(line)`**  
* Writes to a csv file from a dataset (list of lists)  
* **`delimeter`** is defaulted to **`","`**   

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Excel Files:<center>

[How to Work with Excel files in Pandas (see if getting errors)](https://towardsdatascience.com/how-to-work-with-excel-files-in-pandas-c584abb67bfb)

**Read Excel files**  

**`import pandas as pd`**  
* Must first **import pandas**  

---

**`dataframe_varObj = pd.read_excel(path_var_and_extension, sheet_name=’…’, header=0, skipfooter=0)`**  
* Function will read excel file to a **dataframe**  
* **Not the best way** to read excel files as excel files can be messy containing comments/explanations in the first and/or last couple of rows, better to use **ExcelFile** (see below)    
* For **`sheet_name`**:  
    * **not** provided, then the **first sheet** will be read in **as pandas dataframe** 
    * If **Sheet name** is provided, that **specific sheet** will be read in **as pandas dataframe**  
    * **None** specified, then **all sheets** will be read in **as dictionary of dataframes** where the **keys** will be **sheet names**  
    * Read in **Multiple specific sheets** by providing names of sheets wanted as a **list**  
* **`header`** defaults to 0, and is the index of the row to start reading, the **first row** is used for the **names** of the **dataframe columns**  
* **`skipfooter`** defaults to 0 and specifies the **number of rows** at the **bottom of** the **file** to **NOT read**  

---

**ExcelFile**  

**`pdExcelFileObj = pd.ExcelFile(filePathAndExtension)`**  
* Reads an excel file into a **pandas ExcelFile object**  
* Has **built-in methods** to make it easy to retrieve and manipulate data  

---

**sheets** method  

**`xlsxFIleObj.sheet_names`**  
* Returns a list of all the **sheet names** in the file  

---

**parse** method  

**`xlsxFileObj.parse(self, sheet_name=0, header=0, skipfooter=0)`**  
* If no arguments passed, the **first excel sheet** will be returned as a **pandas dataframe**  
* **Each sheet** can be accessed by passing the **index OR sheet name as a string**  
* The other arguments are similar to **`pd.read_excel()`** method above  

---

**Writing to excel**  

**`dataFrameObj.to_excel(filePathWithExtension, sheet_name='Sheet1', index=True)`**  
* **`sheet_name`** is **optional, defaulting to `Sheet1`** or equivalent number  
* By default **`index=` True**, this will **write** the **index column to the excel file**, set to **False** to **turn off**  
* Note if trying to write a different sheet to the same file, it will **overwrite** the previous with just 1 sheet  
* To write **multiple sheets to file** use **`ExcelWriter`** method (see below)  

---

**ExcelWriter** method  

**`with pd.ExcelWriter(filePathWithExtension, mode='w') as writerObj:`**  
$\;\;\;\;$**`dataFrameObj.to_excel(writerObj, sheet_name='Sheet1', index=True)`**  
$\;\;\;\;$**`dataFrameObj.to_excel(writerObj, sheet_name='Sheet1', index=True)`**  
* This will add multiple sheets to an excel file  
* If no **`sheet_name`** provided to **any**, **only 1 sheet** will get **written**, providing the **1st but not the 2nd**, and the **2nd sheet** will default to **`Sheet1`**  
* If wanting to **add sheets** to an **existing excel file**, set **`mode`** to **`'a'` (append)**  

---

**Writing formula to an Excel file**  

* Formula can be written directly into the dataset as a string, this will then be interpreted by Excel as formulas  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Pandas:</center>

* Pandas are a Python library for data analysis, mainly used for tabular data  
* Dataframe selections containing numerical values can be passed to statistical functions (e.g. **`dfVar['col_name_to_select].mean()`**)  

---

**import pandas**  

**`import pandas as pd`**  

* Keyword **"import"** to import library  
* **"pandas"** is the library name  
* Keyword **"as"** is **optional** to change name referred to in script...in this case "pd"  
* Once the library has been imported, we have access to pre-built functions and classes  

**import specific package**  

**`from libraryName import packageName`**  
* Will import only the package named from the library named  
* Can change name package will be referred to in script by optionally including **as newReferringName** after imported package name  

---

**print all variables and function names of a module**:  

**`print(dir(moduleName))`**  
* This will print all the variables and function names from the module given  

---

**Reading files to dataframes**  

**`path_var = "file_path.ext"`**  
**`dataframe_varObj = pd.read_fileType(path_var)`**  
* The above assigns the **file path to a variable** then applies the **read function to assign the data** to a **dataframe object**  
* This then allows various methods to be applied to be able to work with the data in the dataframe  
* **Dataframes** are comprised of **rows and colums**  
* Ensure to **include extension** in file_path  

---

**create dataframes from a dictionary**  

**`dic_var = {"key1":[listVal1, listVal2], "key2":[listVal1,listVal2]}`**  
**`dataframe_varObj = pd.DataFrame(dic_var, *index)`**  
* **Values must be in list format** to ensure order  
* Keyword **"DataFrame"** is **capitalized** as shown  
* **"index"** is **optional** and can be used to **define own indexing (row identifiers)** by assigning a list or tuple ect  

---

**new dataframe from columns**  

**`new_df_varObj = df_varObj[["col_header1", "col_header2"...]]`**  
* New Dataframes can be created from the column headers  
* **TWO Square brackets** are required to create it **as a Dataframe**  
* When **only ONE square bracket** is used, it will create a **series**....Panda series are essentially a 1D Dataframe  
* Column headers are **case sensitive**  

---

**append column**:  
    
**`df_varObj["new_col_header"] = ["row1", "row2"...]`**  
* Must contain **same number** of **elements** as current dataframe number of **rows**  
* Will append new column to last column of dataframe  

---

**series - access column as series object 1D labled array**  

**`df_varObj["col_header"]`**  
OR  
**`df_varObj.col_header`**  - Only works if column name does not have spaces  
* A series is a **one dimentional** labled array, capable of holding data of any type  
* Method shown here will return the **entire column**  

---

**return multiple columns**  

`df_var[["col_header, "col_header2", ...]]`  
* Access multiple columns as a pandas dataframe  
* Note **double brackets**  


---

**saving dataframes**:  
 
To convert a dataset (list) to a dataframe:  
**`dataframeVar = pd.DataFrame(populatedDataset[1:],columns=populatedDataset[0])`**  
* This uses the first entry of the dataset as the column headers  

**`df.to_fileType("file_name.extension", sep=",", columns=None, header=True, index=True, index_label=None)`**  
* Use this method to save a dataframe to a file  
* **`sep=`** is the desired delimiter, defaults to **`","`**   
* **`columns=`** defaults to **None**, option to pass a sequence of column headers (present in dataframe) to write to file. **Columns not passed, will not be written to file**  
* **`header=`** defaults to **True**, when true, writes column headers. If a list of strings is given it is assumed to be aliases for the column names  
* **`index=`** defaults to **True**, when true, writes row names (index), note this **adds an extra column** to the file  
* **`index_label`** defaults to **None**, option to pass a str or sequence to rename columns, though note **current column headers are still present, but moved further along**  

---

**head** method  

**`dataframe_varObj.head()`**  
* **.head( ) method** allows the **first 5 rows** to be examined 
* Can specify how many **rows to be displayed** in argument

---

**tail** method  

**`dataframe_varObj.tail()`**  
* **.tail( ) method** allows the **last 5 rows** to be examined 
* Can specify how many **rows to be displayed** in argument

---

**take** method  

**`dataframe_varObj.take([indices], axis=0, **kwargs)`**  
* Return the elements in the given positional indices along an axis  
* Can be used to return specific rows by specifying indices in order you would like displayed  
* `kwargs` is for compatibility with numpy.take(), no effect on ouput  

---

**info** method  

**`df_var.info()`**  
* Returns some basic info of the data types in the dataset  

---

**describe** method  

**`df_var.describe()`**  
* If dataset includes **numeric data**, can **get descriptive statistics** using the describe()  
* **count**: Count number of non-NA/null observations <br>
* **max**: Maximum of the values in the object.<br>*italicised text*
* **min**: Minimum of the values in the object.<br>
* **mean**: Mean of the values.<br>
* **std**: Standard deviation of the observations.<br>
* **percentiles**: The percentiles to include in the output. All should fall between 0 and 1. The default is [.25, .5, .75], which returns the 25th, 50th, and 75th percentiles

---

**return column names**  

**`df_varObj.columns`**  
* Will return all the **column headers**  

---

**return index**  

**`df_varObj.index`**  
* Will return **range for rows** or **index names** if not integers    

---

**shape** method  

**`df_varObj.shape`**  
* Will return **size of dataframe** (# rows, # columns)  
* Note **index NOT included** as a column in the dataframe  

---

**.loc[ ]** method (Label of column)  

**`df_varObj.loc[row_index_Name, "col_header"]`**  
OR **pass in conditional:**  
**`df_varObj.loc[df_varObj["col_to_search"] comparator "condition]`** - This will also work without `.loc`  
* Selection by **label**  
* If only inputting **`row_index_Name`** , this will return the entire row selected  
* Rows start at **0**  
* **NOTE** row index is the **name of the row** and not necessarily an integer...**IT IS NOT** the **"index"**  
* **Square brackets**  
* Returns **KeyError** if **column header not found**

---

**slicing using loc**  

**`df_varObj.loc[start_row_index_Name : end_row_index_Name, start_col_header : end_col_header]`**  
* This will slice a dataframe to create a new one  
* **Square** brackets  
* **NOTE** row index is the **name of the row** and not necessarily an integer...**IT IS NOT** the **"index"**  
* **Bewear** If row index names are default integers, a slice such as 1:3 will return rows 2,3 and 4 with names 1,2 and 3 accordingly   
* Can be assigned to a new variable to save  
* If **only selecting one column or row**, this will **return as Pandas Series** rather than a dataframe   

---

**.iloc[ ]** method (Index-label of column)   

**`df_varObj.iloc[row_index, col_index]`**  
* Selection by **position**  
* If only inputting **`row_index`** , this will return the entire row selected  
* Rows and Columns start at **0**  
* **Square brackets**  
* Returns **IndexError** if requested indexer is out-of-bounds  

---

**slicing using .iloc[ ]** method  

**`df_varObj.iloc[start_row_index : end_row_index, start_col_index : end_col_index]`**  
* This will slice a dataframe to create a new one  
* Can be assigned to a new variable to save  
* **Square** brackets  
* If **only selecting one column or row**, this will **return as Pandas Series** rather than a dataframe   

---

**unique** method  

**`df_varObj["col_header_toCheck"].unique()`**  
* Finds unique values in a column and returns values as an array  
* **Square** brackets  

---

**selecting data with condition**  

**`df_varObj[df_varObj.col_header condition_to_check]`**  
**Can also be written:**  
**`df_varObj[df_varObj["col_header"]condition_to_check]`**  
* Without the first df_varObj name and first set of square brackets, this will return a series with boolean values relevant to the conditon to be checked against  
* Assign to a new variable to save  

---

**rename columns with a list**:  

**`df_varObj.columns = ["col_header1", "col_header2"...]`**  
* Must contain **same number** of **elements** as current dataframe number of **columns**  
* Will replace column headers in order of list  

---

**reorder columns**:  

**`df_varObj = df_varObj[["new_1st_col_header", "new_2nd_col_header"...]]`**  
* Will reorder columns with their related data  

---

**set index**  

**`df_varObj.set_index(["col_header1","col_header2"], *drop=Bool, append=Bool, inplace=Bool)`**  
* If only using one column to set index, square brackets are not required  
* **drop** is **optional**, defaults to True, when False will keep original column as well as assign to index  
* **append** is **optional**, defaults to False, when True will add new index to existing rather than replacing  
* **inplace** is **optional**, defaults to False, when True will make changes to original dataframe rather than having to set it to a new dataframe variable object  

---

**set index with list or tuple**  

**`df_varObj.index = list or tuple`**  
* This will replace the existing index with the given list or tuple elements  
* There must be the same number of elements as current index values  
* **Overwrites** current dataframe unless assinging to a new one  
* **Will NOT** reset indexes to original columns  

---

**set index name**  

**`df_varObj.index.name = "New Name"`**  
* This will set the index columns name  
* Setting to **None** will clear the indexes name  

---

**reset to default index**  

**`df_varObj.reset_index(*drop=Bool, *inplace=Bool)`**  
* Will reset index values to default integers  
* **drop** is **optional**, defaults to False, when **True will NOT reinsert column** back into dataframe   
* **inplace** is **optional**, defaults to False, when True will make changes to original dataframe rather than having to set it to a new dataframe variable object  
* If index had no column header, new header (when column is reinserted to dataframe) will be "index"  

---

**drop** function  

**`df_varObj.drop(self, labels=None, axis=0, index=None, columns=None)`**  
* **`labels`** = Index or column labels to drop  
* **`axis`** = Whether to drop labels from the index (0 or ‘index’) or columns (1 or ‘columns’)  
* **`index`** = Alternative to specifying axis (labels, axis=0 is equivalent to index=labels)  
* **`columns`** = Alternative to specifying axis (labels, axis=1 is equivalent to columns=labels)  

---

**groupby( )** method  

**`groupedDataFrameObj = dataFrameObj.groupby(groupingCriteria)`**  
* [Further information](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html)  
* **`groupingCriteria`** is usually a column header but can be any function by which to split the data  
* if **`groupingCriteria`** is a **single** column, it can be passed as a **string**, **multiple** should be passed as a **list**  
* The dataframe can be displayed by determining how to display each group value:  

$\;\;\;\;\;\;\;\;$**`groupedDataFrameObj.first( )`**  
* **`first( )`** displays the first in the table for each group  
* **`last( )`** displays the last in the table  
* **`min( )`** displays the minimum for each group  
* **`max( )`** displays the maximum for each group  
* **`mean( )`** displays the mean for each group  


* This can be saved back to a csv or excel file as a dataframe object can be  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>NumPy:</center>

* NumPy is a Python library for data analysis, mainly used for numerical data  
* Can be computationally faster and require less memory than regular Python  

---

**import numpy**  

**`import numpy as np`**  

* Keyword **"import"** to import library  
* **"numpy"** is the library name  
* Keyword **"as"** is **optional** to change name referred to in script...in this case to the standard abbreviation "np"  
* Once the library has been imported, we have access to pre-built functions and classes  

**import specific package**  

**`from libraryName import packageName`**  
* Will import only the package named from the library named  
* Can change name package will be referred to in script by optionally including **as newReferringName** after imported package name  

---

**print all variables and function names of a module**:  

**`print(dir(moduleName))`**  
* This will print all the variables and function names from the module given  

---

**cast list to numpy n-dimensional (nd) array**  

**`np_var = np.array([ele1, ele2...])`**  
* An array is a list that is arranged in **multiple directions**, see picture below  
* When there are more dimensions there will be more nested lists, note Python will print out as a table for easier viewing  
* Assign to a variable to save  
* "np" is the library name as imported  *
* Requires **round AND square** brackets  
* NumPy **array elements** need to be the **SAME type**  
* The main **difference between np.array** and **np.asarray** is that np.array creates a copy of the object array and does not reflect changes to the original array. np.asarray reflects changes to the original array  

![](http://venus.ifca.unican.es/Rintro/_images/dataStructuresNew.png "visualization of Vectors, Matrices and Arrays")

---

**numpy matrix object**  

**`np_var = np.matrix([[ele11,ele12...],`**  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**`[ele21, ele22...]])`**  
* Returns a matrix from an array-like object, or from a string of data  
* A matrix is a specialized 2-D array that retains its 2-D nature through operations  
* It has certain special operators, such as `*` (matrix multiplication) and `**` (matrix power)  

---

**largest element in an array or matrix**  

**`np.max(np_var)`**  
* Returns the largest element in array or matrix  

---

**zeros**  

**`np.zeros(shape)`**  
* Creates an array of given shape **filled with zeros**  
* **`shape`** is the number of elements in each direction in the array, **1D arrays** need just the **number of elements**, **2D arrays** should be given as a **tuple** (10,3) would produce an array with 10 rows, each with 3 elements  
* Note the zeros will be entered as **floats**  
* **If you don't have the data**, best practice is to initialise a matrix with zeros and populate it

---

**ones**  

**`np.ones(shape)`**  
* Similar to zeros (above), but fills the array with ones  
* Note the ones are entered as **floats**  

---

**eye** function (**Identity matrix**)  

**`np.eye(N, M=None)`**  
* **`N`** is the number of **rows** in the output  
* **`M`** is the number of **columns**, defaults to **`N`** when set to **None**  
* Produces a matrix filled with **zeros**, with **ones on the diagonal**  
* If **`M`** is not specified, produces a **square matrix** (same number of rows and columns)  
* Matrices of this form (max one '1' per row and column) are called permutation matrices  

---

**empty** function  

**`np.empty(shape, dtype=float)`**  
* **`dtype`** Desired output data-type for the array, e.g, numpy.int8. Default is numpy.float64  
* Use **`dtype='U10'`** for **unicode string of max length 10**  

---

**Cast dataset (list) as ndarray**  

**`ndarrayVar = np.asarray(dataset)`**  
* Casts **`dataset`** as ndarray  
* The main **difference between np.array** and **np.asarray** is that np.array creates a copy of the object array and does not reflect changes to the original array. np.asarray reflects changes to the original array  

---

**index numpy arrays**  

**`np_var[list_index(row_in_2D)][element_index(column_in_2D]`**  
**OR**  
**`np_var[row, column]`**  
* As with indexing lists, **first element starts at "0"**  
* **Square brackets** to index  
* **Change** element with **"="**, this will make change to original array  
* When indexing multiple dimension arrays, start with highest level  
* Indexing 1D arrays will only require element index  
* Indexing a **3D** array would be **`np_var[slice, row, column]`**  

---

**slice nd array**  

**`np_var[index:index]`** 

**slice 2D array**:

**`np_var[row_indexFrom:row_indexTo,col_indexFrom:col_indexTo]`**  
* Same as slicing lists and tuples  
* **Square brackets**  
* Change selected elements with **"="**, this will make change to original array  
* When changing elements, cannot use this method to add extra elements, however can change more than one element to the same thing  
* **Note how Python prints arrays** for easier viewing of diemensions and more like tables, when slicing 2D arrays this can be helpful as first index refers to the row and second index refers to the column  

---

**obtain data type of nd array**  

**`np_var.dtype`**  
* Will return datatype of "np_var"  

---

**number of elements in nd array**  

**`np_var.size`**  
* Will return number of elements in nd array

---

**number of dimensions in nd array**  

**`np_var.ndim`**  
* Will return number of dimensions in nd array  
* Think of this as how many nested lists there are i.e. **number of levels NOT number of lists at bottom level** as this would be the arrays shape,  
e.g. **`1D = array( [...] )` `2D = array( [[...],[...],[...]] )` `3D = array( [[[...],[...]]] )`**  

---

**shape: size of nd array in each dimension**  

**`np_var.shape`**  
* Will return number of elements in each dimension (direction)  

---

**unique** function  

**`np.unique(np_var, return_index=False, return_inverse=False, return_counts=False, axis=None)`**  
* Returns the sorted unique elements of an array  
* If **`return_index=True`** also return the indices of **`np_var`** that result in the unique array  
* If **`return_inverse=True`** also return the indices of the unique array that can be used to reconstruct **`np_var`**  
* If **`return_counts=True`** also return the number of times each unique item appears in **`np_var`**  

---

**array addition / subtraction**  

**`np_var3 = np_var +/- np_var2`**  
* Arrays can be added / subtracted  
* Arrays must be **SAME SHAPE** to be added or subtracted together  
* Will add or subtract elements of the same position  
* Can **add/subtract scalers** to a **single array** in a similar way  
* Can also **add/subtract vectors** (another array containing the same number of elements as the 2D array e.g.:   
$\;\;\;\;$**`matrix = np.array([[1,2,3],[4,5,6]])`**  
$\;\;\;\;$**`vector = np.array([0.5 ,0.25,0.8 ])`**  
$\;\;\;\;$**`matrix + vector = ([1.5 ,2.25,3.8 ],[4.5 ,5.25,6.8 ])`**  
    * **Above** example would **broadcast** across the **columns** (3 elements in the vector, and 3 columns in the matrix)  
    * To **broadcast** across the **rows**, vector must be in the **same shape** as the **matrix**, for the above, the vector would be:  
$\;\;\;\;$**`np.array([[0.25], [0.5]])`**  
* Results in another array of the same size as those added or subtracted together  

![](https://mathinsight.org/media/image/image/vector_2d_add.png "Vector addition")

---

**array multiplication**  

**`np_var2 = #timesToMultiply * np_var`**  
* This will multiply the array by a scalar  
* A constant can also be added or subtracted to every element in a similar way (this is called **Broadcasting**)  

---

**add axis to array**  

**`newArrayVar = arrayVar[:,:,np.newaxis]`**  
* The number of passed dimensions ( **`:,`** ) should match the current arrays shape  

---

**hadamard product ( X ◦ Y )**  

**`np_var3 = np_var * np_var2`**  
* Each element in corresponding positions will be multiplied together producing an array of equal shape  
* **Arrays must** be of **equal size** 
* See matrix multiplication for arrays of larger dimensions  

---

**dot product / scalar product ( X · Y )**  

**`np.dot(np_var1, np_var2)`**  
OR  
**`np_var1 @ np_var2`**  
* Among other things, the dot product can be used to test if two vectors are **perpendicular**, this will be shown if the dot product is **== 0**  
* Arrays **must be compatible size** (n x m, m x p) -> (n x p)  
* np.matrix can be used instead of arrays, when multiplying with np.matrix, dot product can be obtained with **\***, however be careful, as **\*** with arrays will try to broadcast rather than calculate the dot product  

---

**matrix multiplication**  

**`np.dot(np_var1, np_var2)`**  
* **Matrix A's number of columns must be equal to Matrix B's number of rows** to be able to muliply matrices  
* **Different** process to that of 1D array dot product  
* Assisn to new array variable to save  
* NOTE - **`originalMatrix @ inverseOfMatrix = IdentityMatrix`** (Matrix multiplied by its inverse will give the matrix of 1's on the main diagonal and zeros everywhere else)  
* Creates a new array by obtaining the dot product of Matrix A's i'th row to Matrix B's j'th column:  

**1st row, 1st column:**  
1x7 + 2x9 + 3x11 = 58![](https://www.mathsisfun.com/algebra/images/matrix-multiply-a.svg "matrix mulitiplication")  

**1st row, 2nd column:**  
1x8 + 2x10 + 3x12 = 64![](https://www.mathsisfun.com/algebra/images/matrix-multiply-b.svg "matrix mulitiplication")  

**completed:**
![](https://www.mathsisfun.com/algebra/images/matrix-multiply-c.svg "matrix mulitiplication")

---

**Norm of a matrix or vector**  

**`np.linalg.norm(np_var)`**  
* Returns the Frobenius norm by default (Squareroot of the sum of all squared elements)  

---

**transpose a matrix**  

**`np_var.T`**  
* Keyword **T** will transpose an array or matrix (flips a matrix over its diagonal which switches the row and column indices to create a new matrix)  

---

**trace of a matrix**  

**`np.trace(np_array_var)`**  
* Computes sum of elements[i, i+row index]  
* The trace of a matrix is the **sum of the main diagonal elements**  
* Note a trace of a matrix **ONLY exits** for a **square matrix**, however if array/matrix is not square in numpy, it still computes because **numpy trace does NOT include a check for square matrix**  

---

**determinant of a matrix**  

**`np.linalg.det(np_array_var)`**  
* Array/matrix **MUST** be **square**  
* Calculates the determinant of a matrix (sum of products of elements of any row or column and theri corresponding cofactors)  
* Note numpy uses approximations to calculate determinants and so **may not be accurate**  

---

**inverse of a matrix**  

**`np.linalg.inv(np_array_var)`**  
OR  
**`matrixVar.I`**  
* Returns the **inverse** of an array or matrix   
* Array/matrix **MUST** be **square**  
* **`.I`** method **ONLY** works on **numpy matrix** objects  
* NOTE - **`originalMatrix @ inverseOfMatrix = IdentityMatrix`** (Matrix multiplied by its inverse will give the matrix of 1's on the main diagonal and zeros everywhere else)  

---

**Moore-Penrose pseudoinverse of a matrix**  

**`np.linalg.pinv(np_array_var)`**  
* **Non-square matrix** version of matrix **inverse**  
* **A<sup>+</sup>· A = I** &emsp; but &emsp; **A · A<sup>+</sup> ≠ I**  
* Note numpy approximates, and so sometimes this can be **inaccurate**  

---

**eig function**  

**`np.linalg.eig(np_var)`**  
* Returns the eigenvalues as an array (w) and corresponding eigenvectors as another array (v)  

---

**min** method  

**`np_var.min(axis=None)`**  
* Returns lowest value in array  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  

---

**max** method  

**`np_var.max(axis=None)`**  
* Will return higest value element  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  

---

**square root** method  

**`np.sqrt(np_var)`**  
* Calculates square root of **each element** in an array  

---

**mean of array elements**  

**`np_var.mean(axis=None)`**  
* Calculates mean (average) of all elements in an array  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  
* **Mean** is denoted by the following symbols:  
    * **μ** - (mu) population parameter, i.e. the mean of the entire population  
    * **x̅** - (x-bar) is the mean of a sample  

---

**variance of elements**:  

**`np_var.var(axis=None)`**  
**OR**  
**`((np_var.mean( ) - np_var)**2).sum( ) / np_var.size`**  
* * Returns variance of the elements in the array  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  
* **Variance measures the average degree to which each point differs from the mean**  
* **Variance is the average of all data points within a group**  
* **Variance gives an actual value to how much the numbers in a data set vary from the mean**  
* **Variance** is denoted by **σ$^2$** (sigma squared)  

**Defined:**  
$\sigma^2(x) = \frac{1}{N} \sum_{i=1}^N (x_i - \bar{x})^2$

---

**standard deviation of elements**  

**`np_var.std(axis=None)`**  
**OR**  
**`np.sqrt(((np_var.mean( ) - np_var)**2).sum( ) / np_var.size)`**  
* Returns standard deviation of the elements in the array  
* **`axis`** calculates across an axis rather than of all elements, and refers to the index of the axis. e.g. in a 2D array:  
    * **`axis=0`** would calculate across the columns  
    * **`axis=1`** would calculate across the rows  
* **Standard deviation** is the **spread of a group of numbers from the mean**  
* **Standard deviation is the square root of the variance**  
* **Standard deviation** is a statistical measure that people can use **to determine how spread out numbers are in a data set**  
* **Standard deviation** is denoted by **σ** (sigma)  

**Defined:**  
$\sigma(x) = \sqrt{\frac{1}{N} \sum_{i=1}^N (x_i - \bar{x})^2}$  

**Normal distribution:**  
![](https://i.insider.com/546e68776bb3f74f68b7d0ba?width=769&format=jpeg)

---

**access value of pi π**  

**`np.pi`**  
* Will return value of Pi

---

**Random numbers with NumPy**  

Part of NumPy library, option to import just package:  
**`from numpy import random`**  

---

**Random int**  

**`np.random.randint(low, high=None, size=None)`**  
* Returns a random int  
* **`low`** = lowest integer to be drawn from distribution  
* **`high`** = if provided, this is one above the largest initeger to be drawn  
* **`size`** = output shape  
* If **only 1 parameter** provided, this is taken as the high value and low = 0   

---

**Random float**  

**`np.random.rand(d0,d1...dn)`**  
* Returns a random float between 0 and 1
* **`d0, d1...dn`** is optional and defines the return shape  

---

**Random Seed**  

**`np.random.seed(self, seed=None)`**  
* The random number generator needs a number to start with (a seed value), to be able to generate a random number  
* By default the random number generator uses the current system time  
* Use the seed() method to customize the start number of the random number generator  
* Note: If you use the same seed value twice you will get the same random number twice  

---

**Random Binomial**  

Binomials have:  
* A fixed number of trials  
* Only have 2 possible outcomes  
* the outcomes are independent of each other  
* the probability of success remains the same for each trial  

**`np.random.binomial(n, p, size=None)`**  
* **`n`** is number or trials per experiment  
* **`p`** is probability of sucess. In the interval [0,1]  
* **`size`** Number of times to run the experiment, default None = 1
* **Returns number of successes for each experiment**  

---

**Random Uniform**  

**`np.random.uniform(low=0.0, high=1.0, size=None)`**  
* Generates random numbers between low and high (inclusive) with equal probability  
* **`size`** is samples drawn  

---

**Random Poisson**  

**`np.random.poisson(lam=1.0, size=None)`**  
* **`lam`** is expectation of interval, must be >= 0  
* **`size`** is samples drawn  

---

**Random Normal Distribution**  

**`np.random.randn(d0,d1,...dn)`**  
* **`d0,d1,...dn`** is the dimentions of the returned array, **must be non-negative**  

---

**Random Gassian distribution**  

**`Normal distribution * σ + μ`**  
* See above for normal distribution  
* **`σ`** is **standard deviation**  
* **`μ`** is **mean**  

---

**linspace**

**`np.linspace(start, stop, num= #samples_to_generate)`**  
* Returns evenly spaced numbers from **"start" to "stop"**  
* **"num="** is parameter which defines how many samples to produce, defaults to 50  
* Prounounced "line space"  

---

**matplotlib**  

[Link to info on matplotlibs colourmap](https://matplotlib.org/stable/tutorials/colors/colormaps.html)

* MatPlotLib is a library used to creat static, animated, and interactive visualizations in Python  

Import library:  
**`import matplotlib.pyplot as plt`**  
* Will import matplotlib library, optional standard abbreviation "plt"  

Display plots in Jupyter Notebook:  
**`%matplotlib inline`**  

**subplots**:  

**`plt.subplot(numberRows=1, numberCols=1, index=1)`**  
* Plots several images in the same cell  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Working with Images:<center>

Colour images are represented using the **RGB colour space**. Each colour is represented by a triplet quantifying the amount of red, green, and blue colours. Each colour is represented by an integer number in **`[0, 255]`**   
Some examples:  

* RED: **`[255,0,0]`**  
* GREEN: **`[0,255,0]`**  
* BLUE: **`[0,0,255]`**  
* YELLOW: **`[255,255,0]`**  
* GRAY: **`[100,100,100]`** (by varying the value, you'll get other shades of gray, often defined using **equal values for all three parameters**)
* BLACK: **`[0,0,0]`**   
* WHITE: **`[255,255,255]`**   

If we have an image of size 200x200, we will have a 3D dimensional array (a list containing three tables of size 200x200 &mdash; python won't use this exact representation, but this is a way to see it -- one per each colour).
![RGB Image representation](https://www.researchgate.net/profile/Jane_Courtney2/publication/267210444/figure/fig6/AS:295732335661069@1447519491773/A-three-dimensional-RGB-matrix-Each-layer-of-the-matrix-is-a-two-dimensional-matrix.png)  

**Set array for image channel**:  
**`channelArrayVar = ImageObjVar[:,:,channelIndex]`**  
* Set **`channelIndex`** to the following to set an array for the:  
    * **red channel = 0**  
    * **green channel = 1**  
    * **blue channel = 2**  

**RGBA** color values are an extension of RGB color values with an Alpha channel - which specifies the opacity for a color  
**`rgba(red, green, blue, alpha)`**  
* **`alpha`** is a number between 0.0 (fully transparent) and 1.0 (not transparent at all)  

---

**Pillow (aka PIL)** module  

**`!pip install pillow`**  
* Is not built-in, install as shown using **pip**  
* Pillow is a module for processing images in Python  
* It is built on the top of PIL (Python Image Library)  
* Pillow supports many image file formats including BMP, PNG, JPEG, and TIFF  

**Import Image module**  

**`from PIL import Image`**  
* Allows images to be opened and provides functions to load images from files, and to create new images  
* PIL is the Python Imaging Library which provides the python interpreter with image editing capabilities  

---

**open( )** function  

**`ImageFileObj = Image.open(imageFilePathAndExtension)`**  
* **pillow provides** the **`open( )`** function read the image  
* A lazy operation; function identifies the file, but the file remains open and the actual image data is not read from the file until you try to process the data (or call the load( ) method)  

---

**show( )** function  

**`ImageFileObj.show( )`**  
* **pillow module provides** **`show( )`** function  
* **`show( )`** function displays the image  
* The method is mainly intended for debugging purposes, **better to use matplotlib**    
* On Unix platforms, this method saves the image to a temporary PPM file, and calls the xv utility. On Windows, it saves the image to a temporary BMP file, and **uses** the **standard BMP display utility to show it (usually Paint)**  
* For displaying the image Pillow first converts the image to a .png format (on Windows OS) and stores it in a temporary buffer and then displays it. Therefore, due to the conversion of the image format to .png some properties of the original image file format might be lost (like animation). Therefore, it is advised to use this method only for test purposes  

---

Using **pyplot** from **matplotlib**  

**`from matplotlib import pyplot as plt`**  
**OR**  
**`import matplotlib.pyplot as plt`**  
* Imports **pyplot** sublibrary from matplotlib library  

**imshow( )** function  

**`plt.imshow(ImageFileObj, cmap=None)`**  
* **matplotlib** function  
* Used to display data as an image  
* **`ImageFileObj`** is the **data of the image**  
* **`cmap`** is **used** when the **shape** of the array is **2D** (grayscale), but **ignored** when **shape** of the array is **3D**  
[Info on **`imshow`**](https://matplotlib.org/3.5.0/api/_as_gen/matplotlib.pyplot.imshow.html)  
[See for using **`cmap`** parameter - info on matplotlibs colourmap](https://matplotlib.org/stable/tutorials/colors/colormaps.html)  
[More info on cmap](https://stackoverflow.com/questions/25625952/matplotlib-what-is-the-function-of-cmap-in-imshow)

---

**size** attribute  

**`ImageFileObj.size`**  
* Provides the size of the image returned as a **tuple** that contains **width** and **height**  
* Part of **Image class**  

---

**format** attribute  

**`ImageFileObj.format`**  
* Returns the **format** of the image file  
* Part of **Image class**  

---

**mode** attribute  

**`ImageFileObj.mode`**  
* Part of **Image class**  
* Tells the type and depth of the pixel in the image  
* A 1-bit pixel has a range of 0-1, and an 8-bit pixel has a range of 0-255  
* There are different modes provided by this module. A few of them are:

|**Mode**|**Description**|
|:---|:---|
|1|1-bit pixels, black and white|
|L|8-bit pixels, Greyscale|
|P|8-bit pixels, mapped to any other mode using a color palette|
|RGB|3×8-bit pixels, true color|
|RGBA|4×8-bit pixels, true color with transparency mask|

---

**Resize an image**  

**`rescaledVar = ImageFileObj.resize(newSize)`**  
* **`newSize`** should be passed as a **tuple**  
* Part of **Image class**  

---

**Save image**  

**`PIL_imageObj.save(filePathWithExtension, imageType)`**  
* Part of **Image class**  
* Saves an image that has been previously loaded - easier as **PIL image object** than image file object  
* Note you can save an image as a different **`imageType`** than the original was opened as  

---

**Create ndarray from an image**  

**`imgArrayVar = np.asarray(ImageFileObj)`**  
* Creates a numpy array from an Image file object  
* Images will be a 3D array  

---

**Clipping images**  

**`newArrayVar = ndarrayVar/255`**$\;\;\;\;$**(or other mathematical operation)**  
* By using **mathematical operators**, we can adjust the values in an **array for an image**  
* **matplotlib (plt)** is able to show images represented as **floats** in the range **[0..1]** and **integers** in the range **[0..255]**  
* Values **below 0 are considered as 0**, values **above 1 are considered as 1**  for **floats**, **same applies** when outside **integer range**  

---

**Broadcasting to an image**  

**`newImgVar = clippedImageVar*broadcastArray`**  
* **`clippedImageVar`** should be **clipped** to keep any **scaled values** inside the **image range** for floats (0-1)  
* **`broadcastArray`** should be **same shape** as image  
* Sometimes you may need to add an axis to an array to make it the same shape (see Numpy)  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Basic Statistics:</center>

**Statistical types of data**  

Three main types:
- $x$ is an **ordinal** variable if $x\in\mathbb{N}$ (**Natural numbers** - whole, positive, **typically does not include 0**);  
$\;\;\;\;$e.g:  
    * Our age  
    * Amazon star reviews  
    * Likert scale (strongly agree [5], agree [4], neutral [3], disgree [2], strongly disagree [1])  
- $x$ is a **numerical** variable if $x\in\mathbb{R}$ (**Real numbers** - all rational and irrational numbers;  
- $x$ is an **categorical (or nominal)** variable if $x\in C$, where $C$ is a **finite set** of element (and typically there's **no order between the elements** of $C$)  
$\;\;\;\;$e.g:  
    * Yes/No,  
    * The categories of films/books  

**Types of probability distribution**  

There are **two main types**:  
* **Discrete**; good for **categorical / ordinal** data  
* **Continuous**; good for **numerical** data  

**Discrete probability distributions** include  

* Bernoulli Distribution  
* Uniform Distribution  
* Poisson Distribution  

**Continuous probability distributions** include  

* Continuous Uniform Distribution  
* Gaussian Distribution  

**Bernoulli Distribution**  

See NumPy section for creating random distributions in Python  

Any kind of events with **two possible outcomes (binary events**), e.g. flipping a fair coin  
The **probability mass function (PMF) `f`** over possible outcomes **k** is:  
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/614e0c64d59f0ff2e926deafcb2de6e502394fac)  
**k** = success - outcome you want to keep track of (1 = success)  
**p** = probability of success (probability of failiure is 1-p)  
Every Bernoulli trial must be an **independant event**  

![](https://valelab4.ucsf.edu/svn/3rdpartypublic/boost/libs/math/doc/sf_and_dist/graphs/bernoulli_pdf.png)

**Uniform Distribution**  

See NumPy section for creating random distributions in Python  

Good to formalise **events with equal probability**  
e.g. drawing a heart, diamond, club, or spade from a deck of cards,  
$\;\;\;\;$ or rolling a number on a dice  
Has **one parameter n (the number of events)** where each event has the **same probability**  
from the set of realisation {a-b}, (otherwise probability is zero)  
**probability mass function (PMF) `f`**:  
![](https://www.math.net/mj/Zih4KSA9IFxmcmFjMW4gXCAsIFwgXHRleHR7eCA9IDEsIDIsIDMsIC4uLiwgbn0=_100.svg)  
**n** = number of events  

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1f/Uniform_discrete_pmf_svg.svg/488px-Uniform_discrete_pmf_svg.svg.png)

**Poisson Distribution**  

See NumPy section for creating random distributions in Python  

Good to formalise **events occurring in a fixed interval of time (or space), or other specified interval types such as distance, area or volume**  
e.g. Number of patients visiting the GP between 10-11am  
$\;\;\;\;$or Number of rainy days in Edinburgh in a year  
**probability mass function (PMF) `f`**:  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/6c429d187b5d4ef8ddea32a2d224f423cf9fe5b0)  
Valid **only for values on the x-axis** 

e is Euler's number (e = 2.71828...)  
k is the number of occurrences  
k! is the factorial of x  
λ (sometimes written μ) is a potitive number equal to the expected value (EV) of X when that is also equal to its variance   
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/2debd3f9adf97c8af4919aa69ed4a7121b47a737)

![](https://wsproject.org/images/poisson3.gif)

**Continuous probability distributions** include  

* Continuous Uniform Distribution  
* Gaussian Distribution  

**Continuous Uniform Distribution**  

The distribution describes an experiment where there is an **arbitrary outcome that lies between certain bounds**  
The **bounds are** defined by the parameters, **a and b**, which are the **minimum and maximum values**  
**probability density function (PDF) `f`**:  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/b701524dbfea89ed90316dbc48c5b62954d7411c)  

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Uniform_Distribution_PDF_SVG.svg/375px-Uniform_Distribution_PDF_SVG.svg.png)  

**Gaussian Distribution**  

See NumPy section for creating random distributions in Python  

For a **real-valued** (Rational and irrational numbers) random variable 
Informally called a bell curve, but there are other types of bell shaped distributions  
**probability density function (PDF) `f`**:  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/00cb9b2c9b866378626bcfa45c86a6de2f2b2e40)  

**μ** (Mu) is the **mean** or expectation of the distribution (and also its median and mode)  
**σ** (Sigma) is the **standard deviation**  

When **μ=0 and σ=1**, this is called **Normal Distribution (Z)**  

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Normal_Distribution_PDF.svg/330px-Normal_Distribution_PDF.svg.png)  
Red curve is the **Standard normal distribution**  

**Normal distribution:**  
![](https://i.insider.com/546e68776bb3f74f68b7d0ba?width=769&format=jpeg)  

**Expected value**  

The return you can expect for some kind of action  
Generalised as the weighted average  
For **discrete binomial events** (2 outcomes):  
![](https://www.superprof.co.uk/resources/wp-content/ql-cache/quicklatex.com-7ab0e984c43345bb465953f789344174_l3.png)  

For **discrete multiple events** (multiple probabilities):  
![](https://www.superprof.co.uk/resources/wp-content/ql-cache/quicklatex.com-4e0f834dd559812ee38b8c28b3c2b91b_l3.png)  

**P(x)** = probability of success  
**X** = number of trials  

For a **continuous random variable**:  
![](https://study.com/cimages/multimages/16/visual4-1.png)  

The curve is esscentially broken up into smaller and smaller intervals and the weighted average is calculated similar to discrete distribution  4

**Mode**  

Mode is the value with the highest probability (this will be in the center of a symetric distribution)  

Single mode = **Unimodel**  
Two or more modes = **Multimodel**  

**Variance**  

Quantifies the spread around the mean  
Defined as the mean of the squared difference between the mean and the data  
For **Discrete** random variable:  
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/2577f2b00102ca127d8867a756b85e17d97eab5f)  
**μ** = expected value  

For **Continuous** random variable:  
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/15af4223be86b41d179dfd36b2ecbc27fd2d467a)  
**f(x)** = PDF  

**Medium**  

The **middle value** in a sorted, ascending or descending, list of values  
![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Finding_the_median.png/330px-Finding_the_median.png)  

![](https://ubalt.pressbooks.pub/app/uploads/sites/11/2020/12/ch29a-redone.png)  

**Pearson correlation coefficient (PCC)**  

A measure of **linear correlation** between two sets of data  
It is the ratio between the covariance of two variables and the product of their standard deviations; thus it is essentially a normalized measurement of the covariance, such that the result always has a value between −1 and 1  

![](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b9c2079a3ffc1aacd36201ea0a3fb2460dc226f)  
Where:
**n** = sample size  
**x<sub>i</sub>, y<sub>i</sub>** = individual sample points indexed with *i*  
![](https://wikimedia.org/api/rest_v1/media/math/render/svg/5792e9289b8786ab64a5ef4e0cd083f9c151062e) = (the sample mean); and analogously for ȳ  

Does not exactly mean that one event causes the other (but we can have an idea)  
Values closer to $\pm$1 = high correlation  
Values closer to 0 = low correlation  

![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Correlation_coefficient.png/600px-Correlation_coefficient.png)

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Data Preprocessing:</center>

---

**Data Scaling**  

**`min = npArrayVar.min(axis=0)`**  
**`max = npArrayVar.max(axis=0)`**  

**`scaledArrayVar = (npArrayVar - min)/ (max-min)`**  
* **Scaleing** the range of the **data [min,max] to [0,1]**  
* **`axis=0`** restricts calculations to columns of data to **treat each feature separately**  

---

**Data Normalisation**  

**`normalisedVar = (npArrayVar-npArrayVar.mean(axis=0))/npArrayVar.std(axis=0)`**  
* Another way to **scale dataset**, purpose is to make the **mean of your data equal (or very close to) 0**, while the **standard deviation becomes 1**  
* Calculated by **subtracting** the **mean from** your **data and** by **dividing** the **result by** the **standard deviation**  
* **`axis=0`** restricts calculations to columns of data to **treat each feature separately**  

---

**Ordinal Encoding**  

Most categorical data cannot be handled in machine learning and cannot be processed as above  
Can assign numbers to each and create an array as follows:  

**`categoriesArray = np.unique(npArrayCategoricalVar)`**$\;\;\;\;$**Can be done from dataset or array**  
**`dictCat = {}`**  

**`for i,cat in enumerate (categoriesArray):`**  
$\;\;\;\;$**`dictCat[cat] = i`**  

**`ordinalArray = np.zeros((npArrayCategoricalVar.size,),dtype=np.int32)`**  

**`for i in range(ordinalArray.size):`**  
$\;\;\;\;$**`ordinalArray[i] = dictCat[npArrayCategoricalVar[i]]`**  
* Returns an array where each category has been replaced with a unique number  

---

**One-hot encoding**  

**`oneHotArrayVar = np.eye(categoriesArrayVar.size)[ordinalArrayVar]`**  
* Converts ordinal encoding to a **group of 'bits'** where each bit relates to a category  
* Makes it **easier to concatinate array with original array** (See below)  
* Each column represents a category, each row will have 1 in one category and 0 in the rest, the resulting row is a binary variable encoding for each category  

---

**Concatenate arrays**  

**`concatenatedArray = np.concatenate(firstArray, secondArray, axis=0)`**  
* **`axis`** **defaults to 0 (columns)**, set to **1** to concatenate **rows**, set to **None** to **flattern arrays before use**  
* The arrays must have the same shape, except in the dimension corresponding to **`axis`** (the first, by default)  

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Simple APIs:</center>


```python

```


```python

```


```python

```


```python

```

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)

---

## <center>Notes:</center>


```python

```


```python

```


```python

```

[<p style="text-align: right;">**⬆ Table of Contents ⬆**</p>](#Python-Quick-Reference)


```python

```


```python

```
