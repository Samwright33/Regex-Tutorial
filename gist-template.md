# Tutorial on Regex

Hello and welcome! In this tutorial, we will be reviewing Regex, also known as regular expression. This tutorial is designed to help users gain a better understanding of what regular expression is and how they work. We will be disecting the parts that make up a regualr expression and how they work together. 

## Summary

Regular expression is a chain of specific characters that makes up a search pattern. These search patterns can be used to locate and validate strings or patterns within text, files, and other forms of character input. Regular expression utilizes traditional and special characters to describe a each individual search pattern. 

Here is an example of what a regualr expression may look like:

/^#?([a-z0-9]{14}|[a-z0-9]{7})$/

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

### Anchors

Anchors are characters that are used at the beginning and  end of a regular expression. Their purpose is to indicate the beginning and the end of a string.

Anchor Characters and Uses:

* ^ - Matches a string that begins with the word following the character.

* $ - Matches a string that ends with the word directly in front of the character.

Example: /^#?([a-z0-9]{14}|[a-z0-9]{7})$/

* The characters (/^) and ($/) are acting as the anchors in this code snippet

### Quantifiers

Quanitifers are used in a regular expression to describe how many occurances of a character, group, or character class are required for a pattern to be a match. Their purpose is to ensure the match is to be accurate. 

Quantifier Characters and Uses:

* (*) - Matches a string to the preceding character zero or more times

* (+) - Matches a string to the preceding character one or more times

* (?) - Matches a string to the preceding character zero or one time

* ({5}) - This means the length of the character preceding the quantifier should be 5

Examples: 

* STW* - Matches a string with ST having zero or more W's following it

* STW+ - Matches a string with ST having one or more W's following it

* STW? - Matches a string with ST having zero or one W's following it

* STW{5} - Matches a string with ST having 5 W's following it

* STW{5,10} - Matches a string with ST having 5-10 W's following it

* STW{10, } - Matches a string with ST having ten or more W's following it

### OR Operator

The OR Operator is a compenant defined by the element (|) and is used to match the expression before or after the element is stated in the expression. The pattern will match either the compenant before the element or after, it should not match both. The element ([]) serves the same purpose except it will exclude the contents that are contained within the brackets when matching. 

Examples: 

* S(T|W) - Matches a string with S followed by either T or W

* S[TW] - Matches a string with S and excludes both T and W from the match 

### Character Classes

Character classes are used to describe what type of characters we can expect in the pattern. 

* /d - Matches a character that is a digit value 

* /w - Matches a word character value

* /s - Matches a whitespace character such as a line break

* [a-z] - Matches the characters inside the brackets, in this case all 26 alphabletical letters

* [0-5] - Matches the characters inside the brackets, in this case numerical values 0-5

Example:

* An example of a character class is [a-z0-9]. This example is searching for characters using all 26 alphabetical letters and 0-9 in numerical values

### Flags

Flags are essentially parameters inplemented to alter the way the expression is interpreted. They are implemented using two dashes such as (/STW/)

* g - This stands for global. It will not return after the first pattern match and instead it will restart the subsequent searches from the end of the match directly before it

* m - This stands for multi-line. When the multi-line flag is enabled, it will match the start and end of a line rather than the entire string

* i - This stands for insensitive. This flag will make the entire expression case-insensitive.

Examples: 

* /STW/g - Matches STW in the search 

* /STW/m - Matches the beginning and the end of STW instead of the enitre string 

* /STW/i - Case insensative, therefore will match with all instances of STW such as sTw and sTW

### Grouping and Capturing

Grouping and capturing allows for a string or pattern to be unified as one entity in the search. 

* () - Parentheses allow us to create a capturing group containing the value

* ?: - Allows us to disable the capturing group that is stated

* ?<foo> - Essentially giving a name to a group we create 

Examples: 

* S(TW) - The parentheses allow for us to create a capture group containing TW

* S(?:TW) - This allows for (TW) to be disabled in the capturing group

* S(?<foo>TW) - This provides the capture group with a name foo

### Bracket Expressions

A bracket expression is a regualr expression containted inside brackets. They are used to match a single character within the brackets with a string. 

* [] - Matches a character that is in the brackets 

* []% - Matches a character before the % symbol 

* [^] - Matches a string that does not have the bracket value and is complemented

Examples: 

* [STW] - Matches a string that S or T or W

* [0-5] - Matches a string that has a character 0-5 before the decimal 

* [^a-z] - Matches a string that does not have a letter from a-z

### Greedy and Lazy Match

A greedy match represents the longest possible string. Essentially this quantifier tells the engine to match as many instances of the quantified value as it can.

A lazy match represents the shortest possible string.
Essentially this quantifier tells the engine to match as few of instances of the quantified value as it can.

Example: 

* (* + {}) - Example of a greedy operator

* <.+?> - Matches a character one or more times included in the <>

* <[^<>]+> - Matches a character except for <> one or more times included in the <>

### Boundaries

Boundaries represent the area between character values. Essentially they serve as a barrier between adjacent character values. The two types of boundaries are word and non word. 

* /b - This is used for word boundaries. This is the area between a word and a nonword at the beginning and end of a string

* /B - This is used for nonword boundaries. This is the area where word boundaries are not present. 

Examples:

* \bSTW\b - Will match a string for STW using a "whole search only" search

* \BSTW\B - Matches STW only if the pattern is surrounded by word characters 

### Back-references

Back-references are used to match the text matched in a capturing group. They are used to refer to a captured match. 

Examples: 

* ([abc])\1 -  \1 allows the to matche the same text that was matched by the first capturing group

* ([abc])([de])\2\1 - \2 can be used to identify the same text that was matched by the second capturing group

* (?<foo>[abc])\f<foo> - References the name foo to the group and it is used as a reference 
 
### Look-ahead and Look-behind

Look-ahead and Look-behind are zero-length assertions like the beginning and end of line, and beginning and end of word anchors. They are used to match character values and determine if the result has a match or not. This is done using positive and negative look-aheads and look-behinds.

* (?=STW) - Positive lookahead - Matches a group after the main expression but does not include for the result

* (?=!STW) - Negative lookahead - Matches a group that does not match after the main expression

* (?=<STW>) - Positive lookbehind - Matches a group before the main expression but does not include for the result

* (?<!STW>) - Negative lookbehind - Matches a group that does not match before the main expression

## Author

This tutorial was created by Sam Wright. He works in Governemnt Sales and is currently a student completing The University of Wisconsin Full Stack Development Coding Bootcamp. He will be graduating in May with his certificate and will pursue freelance web development while conitnuing his career in sales. 

[View my Github Profile Here](https://github.com/Samwright33)
