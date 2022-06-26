# Regex Tutorial

Regex (short for Regular Expression) is something that can be used in many different programming languages to extract information from text by using specific patterns. Regex can be used to do many thing like validating emails, formatting phone numbers, or parsing/replacting pieces of stings for example. The applications are numerous. 

## Summary
I'll be describing some regex basics below. With each explanation, I will reference the following line of regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` and describing what each component does, if applicable. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors:
Anchors are used to match a position in a line of text. These characters are `^` and `$`.
* `^` will match a string that starts with the specified characters. For example:` ^Hello ` would match the following string: `Hello world!`
    * The regex I specified above uses this character. This means that `^([a-z0-9_\.-]+)` is looking for a string that begins with a-z, or 0-9. If the string does not begin with these characters, it will not match. For exmaple, this section of regex would match `thetinaest`, `123thetinaest`, `g6f2l` and so on.
* `$` will match a string that ends with the specified chatacters. For example: ` $world!` would match the same string, `Hello world!`

### Quantifiers
Quantifiers can be used to match strings with a certain amount of specified characters. The amount of characters can be specified as well. These characters are as follows: `*`, `+`, `?`, and `{}`. Each of have their own unique uses.
* `*` can be used to find a string that excludes or includes your specified character. Even if it includes multiple instances of that same character. For example: `Good evening*` would match the following strings: `Good evenin`, `Good evening`, `Good eveninggggg`, and so on. Any string that starts with `Good evenin` and has one or more `g` at the end will match.

* `+` can be used to find a string that includes your specified character, even if that character is repeating. If the string does not include at least 1 instance of this character, it will not match. For example: `Good morning+` would match the following strings: `Good morning`, `Good morninggggg`, `Good morninggggg`, etc. 
    *  The regex I specified above uses this character. This means that `^([a-z0-9_\.-]+)` is looking for a string that begins with a-z, or 0-9. If the string has any of these characters more than once, it will still match. For example: `aaaa`, `a55a5`, `abcabc777`, etc. would all match.

* `?` can be used to find a string that has only one or zero of the specified character. For example: `Good night?` would match the following strings: `Good night`, `Good nigh`. If the string ends with more than 1 (or 0) `t` will not match.

* `{}` can be used to set the number of characters we are looking for at the end of a string. You can include two numbers within the `{}`, separated by a comma. The first number is required and will be the minimum number of characters we are looking to match. The second number is not required, and it can be used to set the mamimum number of characters to match. See the following examples:
    * `Code{2}` would match any string that has `Cod` followed by at least 2 `e`. If the string ends with more than 2 `e`, this will match as well. For example, `Code{2}` will match: `Codee`, `Codeee`, etc.
    
    * `Code{1,3}` would match any string that has `Cod` followed by at least 1 `e`, and up to 3 `e`. If the string ends with more than 3 `e`, it will not match. For example, `Code{1,3}` will match: `Code`, `Codee`, and `Codeee`.
        * The regex I specified above uses this operator. This means that `([a-z\.]{2,6})` is looking for a string that ends with at least 2 lowercase letters, and at most 6. For example: `com`, `net`, `org`, etc. would all match in this case.

### OR Operator
The characters `|` and `[]` can be used to specify more than 1 character to search for. 

* `|` will match a string that is followed by one OR the other character. For example: `ca(t|p)` will match a string that has `ca` followed by either a `t` or a `p`. So, it will match both `cat` and `cap`. It will also [capture](#grouping-and-capturing) the `t` or `p`.
* `[]` works the same as the `|` but without capturing anything. `ca[tp]` will match both `cat` and `cap`. Click [this link](#bracket-expressions) to read more about bracket expressions.
    * The regex I specified above uses this operator. This means that `^([a-z0-9_\.-]+)` is looking for a string that begins with a-z, OR 0-9. It could be any lowercase letter OR any number and still match. For example: `aaaa`, `a55a5`, `8abcabc777`, etc. would all match.

### Character Classes
Character classes can be searched by using `\d`, `\w`, and `\s`. 
* `\d` will match any *digit*. 
    * The regex I specified above uses this character. This means that `([\da-z\.-]+)` will match any string with a digit in this position. Because it is followed by `a-z`, it will also match any lowercase letter that might be in this same position. Because it is following an `@`, this section of regex would match the following examples: `hello@56site`, `6ty@hello`, `b5d@blue4`, etc. 
* `\w` will match any *alphanumeric* character including underscores.
* `\s` will match any *whitespace* character (this includes tabs and line breaks).


### Flags
The characters `g`, `m`, and `i` allow us to get even more specific with our searches. 
* `g` is a global search. This means it will match ALL occurences of our search. 
* `m` is a multi-line search. When used with `^` or `$` for a multi-line string, it will match the atart or end of *any line* in the string rather than just the beginning or end of the string in general. 
* `i` is an insensitive search. This will make the entire expression case-insensitive. serching for `/hElLo` would still match `Hello` or `HELLO` for example.


### Grouping and Capturing
The `()` operator can be used for grouping or capturing. This can be useful if we need to extract information from text/strings. If there are multiple occurences, these will be exposed as an array. We will have the ability to access the data by using an index of the match.
* `?:` can be used to disable the capturing group. Whatever was enclosed in the `()` will not appear in the list of captures matches. This can be written out as `a(?:bc)` for example.
* `?<name>` can be added to add a name to the captured group. This can be written out as `a(?<captures>)` for example.

### Bracket Expressions
Brackets will indicate a set of characters to match. Any character that we put inside the brackets can return a match. For example, `/[abcd]` would match `anvil`, `cat`, `does`, etc. As long as the string has one of the specified characters, it will match. 

### Greedy and Lazy Match
* A *greedy* match will consume the entirety of a string based on our specified characters. It will not only return specifically what you have searched for but everything else within it as well. For example, `<.+>` would match the entire string `<div>Hello, world</div>`. 
* A *lazy* match will return only what your specified search asked for. If we wanted ONLY the div tag, we could add a `?` to the same serach. For example: `<.+?>` would return just `<div>` and `</div>`.

### Boundaries
The `\b` and `\B` operators are what we use to set bondaries. 
* `\b` would perform a "whole word only" search. `\babc\b` would match `abc`, but it would NOT match `qabcq`. It will only match the string at the beginning of the word (as in, the beginning of word characters). `\babc\b` would also match `!abc!`.
* `\B` would match everything that `\b` doesn't. This could be used if we were looking to find a pattern that is surrounded by other word characters. For exmaple: `\Babc\B` would match `qabcq` but it would NOT match `abc` or `!abc!`.

### Back-references
Back-references matches the same text that was matched by a capturing group previously. This is helpful for reusing previous parts of the pattern and checking if two pieces of a string also match. A back reference is specified by using a backslash `\` and a single digit, such as `1`. The digit will specify which capturing group we want to match. For example: `([abc])([def])\2\1`. By using the `\2` we can identify the same string that was matched by the second capturing group (in this case, `de`).

### Look-ahead and Look-behind
the look ahead and look behind operators are `(?=)` and `(?<=)`.
* `a(?=b)` would match an `a` only if it's followed by a `b`. The `b` will not be included in the match. 
* `(?<=a)b` will match a `b` that is preceeded by an `a`. The `a` will not be included in the match.

## Author

This document was created by Kristina Brennan. Please use [this link](https://github.com/thetinaest) to visit my github. 

The following sites were used as a reference in creation of this document. 
- [https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285)
- [https://sodocumentation.net/regex](https://sodocumentation.net/regex)
- [https://www.regular-expressions.info/tutorial.html](https://www.regular-expressions.info/tutorial.html)

