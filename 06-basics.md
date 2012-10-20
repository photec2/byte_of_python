# Basics

Just printing 'Hello World' is not enough, is it? You want to do more than that - you want to take some input, manipulate it and get something out of it. We can achieve this in Python using constants and variables.

## Literal Constants

An example of a literal constant is a number like `5`, `1.23`, `9.25e-3` or a string like `'This is a string'`or `"It's a string!"`. It is called a literal because it is *literal* - you use its value literally. The number `2`always represents itself and nothing else - it is a *constant* because its value cannot be changed. Hence, all these are referred to as literal constants.

## Numbers

Numbers are mainly of two types - integers and floats.

An examples of an integer is `2` which is just a whole number.

Examples of floating point numbers (or *floats* for short) are `3.23` and `52.3E-4`. The `E` notation indicates powers of 10. In this case, `52.3E-4` means `52.3 * 10^-4^`.

*Note for Experienced Programmers:* There is no separate 'long int' type. The default integer type can be a value of any length.

## Strings

A string is a *sequence* of *characters*. Strings are basically just a bunch of words.

You will be using strings in almost every Python program that you write, so pay attention to the following part.

### Single Quote

You can specify strings using single quotes such as `'Quote me on this'`. All white space i.e. spaces and tabs are preserved as-is.

### Double Quotes

Strings in double quotes work exactly the same way as strings in single quotes. An example is `"What's your name?"`

### Triple Quote

You can specify multi-line strings using triple quotes - (`"""` or `'''`). You can use single quotes and double quotes freely within the triple quotes. An example is:

~~~python
'''This is a multi-line string. This is the first line.
This is the second line.
"What's your name?," I asked.
He said "Bond, James Bond."
'''
~~~

### Escape Sequences

Suppose, you want to have a string which contains a single quote (`'`), how will you specify this string? For example, the string is `What's your name?`. You cannot specify `'What's your name?'` because Python will be confused as to where the string starts and ends. So, you will have to specify that this single quote does not indicate the end of the string. This can be done with the help of what is called an *escape sequence*. You specify the single quote as `\'` - notice the backslash. Now, you can specify the string as `'What\'s your name?'`.

Another way of specifying this specific string would be `"What's your name?"` i.e. using double quotes. Similarly, you have to use an escape sequence for using a double quote itself in a double quoted string. Also, you have to indicate the backslash itself using the escape sequence `\\`.

What if you wanted to specify a two-line string? One way is to use a triple-quoted string as shown [previously](#triple-quotes) or you can use an escape sequence for the newline character - `\n` to indicate the start of a new line. An example is `This is the first line\nThis is the second line`. Another useful escape sequence to know is the tab - `\t`. There are many more escape sequences but I have mentioned only the most useful ones here.

One thing to note is that in a string, a single backslash at the end of the line indicates that the string is continued in the next line, but no newline is added. For example:

~~~python
"This is the first sentence. \
This is the second sentence."
~~~

is equivalent to `"This is the first sentence. This is the second sentence."`.

### Raw String

If you need to specify some strings where no special processing such as escape sequences are handled, then what you need is to specify a *raw* string by prefixing `r` or `R` to the string. An example is `r"Newlines are indicated by \n"`.

### Strings Are Immutable

This means that once you have created a string, you cannot change it. Although this might seem like a bad thing, it really isn't. We will see why this is not a limitation in the various programs that we see later on.

*Note for C/C++ Programmers:* There is no separate `char` data type in Python. There is no real need for it and I am sure you won't miss it.

*Note for Perl/PHP Programmers:* Remember that single-quoted strings and double-quoted strings are the same - they do not differ in any way.

*Note for Regular Expression Users:* Always use raw strings when dealing with regular expressions. Otherwise, a lot of backwhacking may be required. For example, backreferences can be referred to as `'\\1'` or `r'\1'`.

### The format method

Sometimes we may want to construct strings from other information. This is where the `format()` method is useful.

~~~python
#!/usr/bin/python
 Filename: str_format.py

age = 20
name = 'Swaroop'

print('{0} was {1} years old when he wrote this book'.format(name, age))
print('Why is {0} playing with that python?'.format(name))
~~~

Output:

~~~
$ python str_format.py
Swaroop was 20 years old when he wrote this book
Why is Swaroop playing with that python?
~~~

How It Works:

A string can use certain specifications and subsequently, the *format* method can be called to substitute those specifications with corresponding arguments to the `format` method.

Observe the first usage where we use `{0}` and this corresponds to the variable `name` which is the first argument to the format method. Similarly, the second specification is `{1}` corresponding to `age` which is the second argument to the format method.

Notice that we could have achieved the same using string concatenation: `name + ' is ' + str(age) + ' years old'` but notice how much uglier and error-prone this is. Second, the conversion to string would be done automatically by the `format` method instead of the explicit conversion here. Third, when using the `format` method, we can change the message without having to deal with the variables used and vice-versa.

What Python does in the `format` method is that it substitutes each argument value into the place of the specification. There can be more detailed specifications such as:

~~~python
 decimal (.) precision of 3 for float '0.333'
>>> '{0:.3}'.format(1/3)
 fill with underscores (_) with the text centered
 (^) to 11 width '___hello___'
>>> '{0:_^11}'.format('hello')
 keyword-based 'Swaroop wrote A Byte of Python'
>>> '{name} wrote {book}'.format(name='Swaroop', book='A Byte of Python')
~~~

## Variable

Using just literal constants can soon become boring - we need some way of storing any information and manipulate them as well. This is where *variables* come into the picture. Variables are exactly what the name implies - their value can vary, i.e.,  you can store anything using a variable. Variables are just parts of your computer's memory where you store some information. Unlike literal constants, you need some method of accessing these variables and hence you give them names.

## Identifier Naming

Variables are examples of identifiers. *Identifiers* are names given to identify *something*. There are some rules you have to follow for naming identifiers:

- The first character of the identifier must be a letter of the alphabet (uppercase ASCII or lowercase ASCII or Unicode character) or an underscore ('_').
- The rest of the identifier name can consist of letters (uppercase ASCII or lowercase ASCII or Unicode character), underscores ('_') or digits (0-9).
- Identifier names are case-sensitive. For example, `myname` and `myName` are **not** the same. Note the lowercase `n` in the former and the uppercase `N` in the latter.
- Examples of *valid* identifier names are `i`, `__my_name`, `name_23`, `>a1b2_c3`. Examples of ''invalid'' identifier names are `2things`, `this is spaced out`, `my-name`, and `"this_is_in_quotes"`.

## Data Types

Variables can hold values of different types called **data types**. The basic types are numbers and strings, which we have already discussed. In later chapters, we will see how to create our own types using [classes](#object-oriented-programming).

## Object

Remember, Python refers to anything used in a program as an *object*.  This is meant in the generic sense. Instead of saying 'the *something*', we say 'the *object*'.

 Note for Object Oriented Programming users:* Python is strongly object-oriented in the sense that everything is an object including numbers, strings and functions.

We will now see how to use variables along with literal constants. Save the following example and run the program.

## How to write Python programs

Henceforth, the standard procedure to save and run a Python program is as follows:

- Open your favorite editor.
- Enter the program code given in the example.
- Save it as a file with the filename mentioned in the comment. I follow the convention of having all Python programs saved with the extension `.py`.
- Run the interpreter with the command `python program.py` or use IDLE to run the programs. You can also use the [executable method](#executable-python-programs) as explained earlier.

## Example: Using Variables And Literal Constants

~~~python
 Filename : var.py
i = 5
print(i)
i = i + 1
print(i)

s = '''This is a multi-line string.
This is the second line.'''
print(s)
~~~

Output:

~~~
$ python var.py
5
6
This is a multi-line string.
This is the second line.
~~~

How It Works:

Here's how this program works. First, we assign the literal constant value `5` to the variable `i` using the assignment operator (`=`). This line is called a statement because it states that something should be done and in this case, we connect the variable name `i` to the value `5`.  Next, we print the value of `i` using the `print` function which, unsurprisingly, just prints the value of the variable to the screen.

Then we add `1` to the value stored in `i` and store it back. We then print it and expectedly, we get the value `6`.

Similarly, we assign the literal string to the variable `s` and then print it.

*Note for static language programmers:* Variables are used by just assigning them a value. No declaration or data type definition is needed/used.

### Logical And Physical Line

A physical line is what you *see* when you write the program. A logical line is what *Python sees* as a single statement. Python implicitly assumes that each *physical line* corresponds to a *logical line*.

An example of a logical line is a statement like `print('Hello World')` - if this was on a line by itself (as you see it in an editor), then this also corresponds to a physical line.

Implicitly, Python encourages the use of a single statement per line which makes code more readable.

If you want to specify more than one logical line on a single physical line, then you have to explicitly specify this using a semicolon (`;`) which indicates the end of a logical line/statement. For example,

~~~python
i = 5
print(i)
~~~

is effectively same as

~~~python
i = 5;
print(i);
~~~

and the same can be written as

~~~python
i = 5; print(i);
~~~

or even

~~~python
i = 5; print(i)
~~~

However, I **strongly recommend** that you stick to **writing a maximum of a single logical line on each single physical line**. The idea is to avoid the semicolon as much as possible so that the code will be more readable. In fact, I have *never* used or even seen a semicolon in a Python program.

It is possible to use more than one physical line for a single logical line, but this should only be used if the logical line is really long. An example of writing a logical line spanning many physical lines follows. This is referred to as **explicit line joining**.

~~~python
s = 'This is a string. \
This continues the string.'
print(s)
~~~

This gives the output:

    This is a string. This continues the string.

Similarly,

~~~python
print\
(i)
~~~

is the same as

~~~python
print(i)
~~~

Sometimes, there is an implicit assumption where you don't need to use a backslash. This is the case where the logical line uses parentheses, square brackets or curly braces. This is called **implicit line joining**.  You can see this in action when we write programs using [lists](#lists) in later chapters.

### Indentation

Whitespace is important in Python. Actually, **whitespace at the beginning of the line is important**. This is called **indentation**. Leading whitespace (spaces and tabs) at the beginning of the logical line is used to determine the indentation level of the logical line, which in turn is used to determine the grouping of statements.

This means that statements which go together **must** have the same indentation. Each such set of statements is called a **block**. We will see examples of how blocks are important in later chapters.

One thing you should remember is that wrong indentation can give rise to errors. For example:

~~~python
i = 5
 print('Value is ', i) # Error! Notice a single space at the start of the line
print('I repeat, the value is ', i)
~~~

When you run this, you get the following error:

~~~
  File "whitespace.py", line 4
    print('Value is ', i) # Error! Notice a single space at the start of the line
    ^
IndentationError: unexpected indent
~~~

Notice that there is a single space at the beginning of the second line. The error indicated by Python tells us that the syntax of the program is invalid i.e. the program was not properly written. What this means to you is that *you cannot arbitrarily start new blocks of statements* (except for the default main block which you have been using all along, of course). Cases where you can use new blocks will be detailed in later chapters such as the [Control Flow](#control-flow).

*How to indent:* Do **not** use a mixture of tabs and spaces for the indentation as it does not work across different platforms properly. I *strongly recommend* that you use a *single tab* or *four spaces* for each indentation level.
Choose either of these two indentation styles. More importantly, choose one and use it **consistently**; and be consistent with the style used in existing files you are editing. i.e. When writing new files use that indentation style *only* and if a file you need to edit is using tabs, while editing that file use tabs for indentation.

*Note to static language programmers:* Python will always use indentation for blocks and will never use braces. Run `from __future__ import braces` to learn more.

## Summary

Now that we have gone through many nitty-gritty details, we can move on to more interesting stuff such as control flow statements. Be sure to become comfortable with what you have read in this chapter.