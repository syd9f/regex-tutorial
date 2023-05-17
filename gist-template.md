# Regex Tutorial - Matching an Email

The dictionary definition of a Regex, or regular expression, is "a sequence of symbols and characters expressing a string or pattern to be searched for within a longer piece of text." In other words, a regex defines a <em>search pattern</em>.

This tutorial will break down the components of specific regex, in order to understand what role each component plays in the search pattern. 

## Summary

The following code snippet is commonly used for matching, or validating, a user's email address:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

There are several pieces to this code that ultimately work together to create a search pattern for finding results that match the specified criteria, in this case an email address. 

Each section of this tutorial will cover an individual aspect of this regex, and break down the roles each part is playing.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

<b>`/`</b>`^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`<b>`/`</b>

At the beginning and end of the expression in our code snippet, you will notice a `/`. These slashes are there because this regex is using <em>literal</em> notation, which requires the use of slashes. 

A regular expression is generally considered a literal, however in JavaScript there is also the option to use a RegExp constructor function, which uses quotation marks rather than slashes.

### Anchors

Anchors are required in a regex to signify where a string starts and ends. 

`/`<b>`^`</b>`([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})`<b>`$`</b>`/`

At the beginning of the code snippet, following the first slash that marks the beginning of the regex, the `^` indicates the beginning of a string of characters. 

Preceding the closing slash, at the end of the regex, is a `$` anchor, which is indicating the <em>end</em> of the string.

### Quantifiers

Frequently, there is a need to specify a limit to the amount of characters used. Quantifiers are used in a regex to set those limits, as seen in our code:

`/^([a-z0-9_\.-]`<b>`+`</b>`)@([\da-z\.-]`<b>`+`</b>`)\.([a-z\.]`<b>`{2,6}`</b>`)$/`

Each of the three <em>[bracket expression's](#bracket-expressions)</em> in our example are accompanied by a quantifier, in two different ways.

The first and second quantifiers,  are found immediately following the <em>[bracket expression's](#bracket-expressions)</em> before and after the @ symbol in the email address, and use the `+` quantifier. 

The `+` quantifier is used here to specify that the emails username and domain name must match the pattern specified in the expressions 1 or more times, meaning that the results must contain and match at least 1 of the specified characters.

Following the final <em>[bracket expression](#bracket-expressions)</em> in our code, is a different type of quantifier. `{2,6}` is a quantifier that uses curly braces `{}` to set the minimum (`2`), and maximum (`6`) amount of characters that the pattern must match.

### Grouping Constructs

`/^`<b>`([a-z0-9_\.-]+)`</b>`@`<b>`([\da-z\.-]+)`</b>`\.`<b>`([a-z\.]{2,6})`</b>`$/`

In our code, there are 3 <em>subexpressions</em>, representing the 3 parts of an email address: the username - `([a-z0-9_\.-]+)`, domain name - `([\da-z\.-]+)`, and extension - `([a-z\.]{2,6})`(username@domain-name.extension). In order to check each section individually for their respective requirements, grouping constructs are required.

Grouping constructs use parentheses `()` to separate the regex into groups, dividing the three sections of our code. Within the parentheses of each group contains a <em>[bracket expression](#bracket-expressions)</em> and a <em>[quantifier](#quantifiers)</em> for that section. 


### Bracket Expressions

A bracket expression, also known as a <em>positive character group</em>, represents the characters that we want to include in our search pattern.

`/^(`<b>`[a-z0-9_\.-]`</b>`+)@(`<b>`[\da-z\.-]`</b>`+)\.(`<b>`[a-z\.]`</b>`{2,6})$/`

The code that we are analyzing above includes 3 bracket expressions:

 The first, `[a-z0-9_\.-]`, is specifying that the <em>unspecified</em> amount of characters at the beginning of the email, before the `@` symbol, can include:

 * lowercase alphanumeric characters a-z
 * numbers 0-9
 * an underscore `_`
 * a period `.` (the `\` before the `.` in the code is a [character escape](#character-escapes), and does not include the `\` as a part of the search criteria)
 * a hyphen `-`

 The second bracket expression found in our code, `[\da-z\.-]`, found immediately following the `@` symbol in the email address, tells us that the email's domain can include:

 * numbers 0-9 <em>(`\d` is a [character class](#character-classes)</em>)
 * lowercase alphanumeric characters a-z
 * a period `.` (again, here the `\` before the `.` in the code is, a <em>[character escape](#character-escapes)</em>, and does not include the `\` as a part of the search criteria)

 The third and final bracket expression, `[a-z\.]`, is located at the end of the email's domain following the period (the com side of .com). This bracket expression is followed by a <em>[quantifier](#quantifiers)</em> that specifies this part must be between 2 and 6 characters. Those characters can include:

 * lowercase alphanumeric characters a-z
 * a period `.` (once again, using the [character escape](#character-escapes) used in the previous expressions)

### Character Classes

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

A character class is used in a regex to define a set of characters. 

### The OR Operator

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`


### Character Escapes

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Author

Sydnie Farrell is a student at Columbia Engineering Coding Bootcamp, studying Full Stack Web Development.

- [Github](https://github.com/syd9f) 
