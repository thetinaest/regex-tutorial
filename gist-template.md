# Regex Tutorial

Regex (short for Regular Expression) is something that can be used in many different programming languages to extract information from text by using specific patterns. Regex can be used to do many thing like validating emails, formatting phone numbers, or parsing/replacting pieces of stings for example. The applications are numerous. 

## Summary

<!-- Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary. -->

I'll be describing some regex basics below. 

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
* `$` will match a string that ends with the specified chatacters. For example: ` $world!` would match the same string, `Hello world!`

### Quantifiers
Quantifiers can be used to match strings with a certain amount of specified characters. The amount of characters can be specified as well. These characters are as follows: `*`, `+`, `?`, and `{}`. Each of have their own unique uses.
* `*` can be used to find a string that excludes or includes your specified character. Even if it includes multiple instances of that same character. For example: `Good evening*` would match the following strings: `Good evenin`, `Good evening`, `Good eveninggggg`, and so on. Any string that starts with `Good evenin` and has one or more `g` at the end will match.

* `+` can be used to find a string that includes your specified character, even if that character is repeating. If the string does not include at least 1 instance of this character, it will not match. For example: `Good morning+` would match the following strings: `Good morning`, `Good morninggggg`, `Good morninggggg`, etc. 

* `?` can be used to find a string that has only one or zero of the specified character. For example: `Good night?` would match the following strings: `Good night`, `Good nigh`. If the string ends with more than 1 (or 0) `t` will not match.

* `{}` can be used to set the number of characters we are looking for at the end of a string. You can include two numbers within the `{}`, separated by a comma. The first number is required and will be the minimum number of characters we are looking to match. The second number is not required, and it can be used to set the mamimum number of characters to match. See the following examples:
    * `Code{2}` would match any string that has `Cod` followed by at least 2 `e`. If the string ends with more than 2 `e`, this will match as well. For example, `Code{2}` will match: `Codee`, `Codeee`, etc.
    
    * `Code{1,3}` would match any string that has `Cod` followed by at least 1 `e`, and up to 3 `e`. If the string ends with more than 3 `e`, it will not match. For example, `Code{1,3}` will match: `Code`, `Codee`, and `Codeee`.

### OR Operator
The characters `|` and `[]` can be used to specify more than 1 character to search for. 

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

<!-- A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile) -->
