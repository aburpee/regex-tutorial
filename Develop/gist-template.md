# Regex Tutorial: Email Strings

## Summary

In this tutorial, I will be outlining the different components of Regular Expressions, or Regex for short. Regex is used for string matching, meaning finding certain combinations of letters, numbers, or other characters within a string. 

I will be guiding through how to parse a regex that specifically looks for a string in an email format. See below.

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

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
The two anchors we'll look at are "^" (caret) and "$" (dollar). 

Anchors do not match characters. Rather, they match positions. The caret matches the beginning of the text and the dollar matches the end of the text.

In our email regex following the caret, /^([a-z0-9_\.-]+), we are looking for a string that matches the interior expression. Similarly, preceding the dollar, ([a-z\.]{2,6})$/, we are looking for a string that matches the interior expression. We'll dive into the interior expressions later on, so don't worry if it isn't quite clicking yet.

### Quantifiers
Quantifiers indicate numbers of characters or expressions to match. In our email regex, we have three examples:
* /^([a-z0-9_\.-]+)
* ([\da-z\.-]+)
* ([a-z\.]{2,6})

The plus sign tells regex to look for that pattern 1 or more times. As an example think of: 
regex.regex.regex@regex.regex.com. The plus sign is saying that the first part of the email address needs to match this pattern at least once. The domain needs to match the regex at least once as well.

{2,6} is another quantifier that is looking for at least 2, and at most 6 occurances of the preceding expression. In our email example, it's looking for a string of 2 to 6 characters that match the expression.

### OR Operator
Our email example doesn't include the | (or) operator. 

That being said consider the statement ^I like (turtles|penguins)$

In this case, the regex will look for the statement I like turtles OR I like penguins.

### Character Classes
Our email example includes one character class \d in the domain part of our email:
([\da-z\.-]+)

\d will match any digit in the expression and is equivalent to [0-9].

### Flags
Flags aren't present in our email regex. Here are a few examples of things to look out for:
* i flag makes the search case-insensitive, meaning A and a are the same.
* g flag searches for all matches, not just the first occurance.
* y flag is "sticky", meaning it searches at the exact position in the string.

### Grouping and Capturing
In our email example, we have several groups: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

* ([a-z0-9_\.-]+)
* ([\da-z\.-]+)
* ([a-z\.]{2,6})

What this means is that each group needs to be satisfied before the expression moves to the next group.

### Bracket Expressions
Looking at our groups above, we can examine the bracket expressions in each.
* [a-z0-9_\.-]: The address can contain a-z, 0-9, _, -, or a .
* [\da-z\.-]: The domain can contain any digits, any letters a-z, ., or -. 
* [a-z\.]: The end of the email can contain letters a-z or .

### Greedy and Lazy Match
Our email example doesn't contain greedy or lazy matches, but here is a brief explanation.

Like the names suggest, greedy matching looks for as many matches as possible, whereas lazy matching looks for as few matches as possible.

### Boundaries
Similar to above, word boundaries don't exist in our email regex. 

Word boundaries are used to match the entire word. So \hello\b will look for the individual word hello. In the string 'hello, world', it would match with hello. In the string 'helloworld' it would not match hello, because hello and world are not broken into separate words. 

### Back-references
Back references are not included in our email regex. 

Simply put, back references match the same text as previously matched by a capturing group. Supposing we wanted the address and the domain part of our email to have the same regex. We would use 
* ^([a-z0-9_\.-]+)@\1

The \1 says 'use the first capturing group in this position also. 

### Look-ahead and Look-behind
Look ahead and look behind are not included in our email regex.

Look ahead (?=) looks for a string immediately following the preceding group.

Look behind (?<=) looks for a string immediately preceding the following group.

## Author
* Adam Burpee

I am a student of web development and data science and I am practicing contributing back to the community. 

Here is my [github](https://github.com/aburpee)
