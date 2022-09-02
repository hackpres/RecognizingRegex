# RecognizingRegex

RecognizingRegex aims to remove the frustration of regular expressions. The first time a person sees a regex(regular expression) it's usually quite intimidating. However, what may initially seem like a series of unrelated alphanumeric characters, in a nonsensical format, is actually quite useful for developers. Here in this tutorial I will walk you through a single expression, but I aim to leave you with the tools necessary to tackle whatever regex you may encounter. Without further ado, Lets dive in!

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Assertions](#assertions)

## Regex Components

### Anchors

-Anchors, or Boundary-type assertions, are typically found at the beginning or end of the expression.
    `^` Matches the beginning of the string or line.
    `$` Matches the end of the string or line.
    `\b` Finds a match at the beginning or end of a word. Beginning like this; \bHI, end like this: HI\b
    `\B` Finds a match that is not at the beginning or end of a word.

### Quantifiers

-Quantifiers indicate numbers of characters or expressions to match.
    `x*` Matches the preceding item "x" 0 or more times.
    `x+` Matches the preceding item "x" 1 or more times.
    `x?` Matches the preceding item "x? 0 or 1 times.
    `x{n}` Where "n" is a positive integer, matches exactly "n" occurrences of the preceeding item "x".
    `x{n,}` Where "n" is a positive integer, matches at least "n" occurrences of the preceding item "x".
    `x{n,m}` Where "n" is 0 or a positive integer, "m" is a positive integer, and m > n, matches at least "n" and at most "m" occurrences of the preceding item "x".
    -By default quantifiers are "greedy", meaning they try to match as much of the string as possible. The ? character after the quantifier makes it "non-greedy", meaning it will stop as soon as it finds a match. For example: `x*?``x+?``x??``x{n}?``x{n,}?``x{n,m}?`

### Grouping Constructs

-Groups and back references indicate groups of expression characters.
    `(x)` Capturing group: Matches "x" and remembers the match.
    `(?<Name>x)` Named capturning group: Matches "x" and stores it on the groups property of the returned matches under the name specified by <Name>. Angle brackets are required for group name.
    `(?:x)` Non-capturing group: Matches "x" but does not remember the match.
    `\n` Where "n" is a positive integer. A back reference to the last substring matching the n parenthetical in the regex.
    `\k<Name>` A back reference to the last substring matching the Named capture group specified by <Name>.

### Bracket Expressions

-Brackets are used to find a range of characters.
    `[abc]` Matches any character within the brackets.
    `[^abc]` Matches any character not found within the brackets.
    `[9]` Matches any character within the bracket range.
    `[^0]` Matches any character NOT found within the brackets.

### Character Classes

-Character classes distinguish kinds of characters such as, distinguishing between letters and digits.
    `.` Matches any single character except line terminators. However, inside a bracket expression, the dot loses its special meaning and matches a literal dot.
    `\d` Matches any digit. Equivalent to [0-9].
    `\D` Matches any character that is not a digit. Equivalent to [^0-9].
    `\w` Matches any alphanumeric character from the basic Latin alphabet.
    `\W` Matches any character that is not a word character from the basic Latin alphabet.
    `\s` Matches a single white space character, including space, tab, form feed, line feed, and other Unicode spaces.
    `\S` Matches a single character other than white space.
    `\t` Matches a horizontal tab.
    `\r` Matches a carriage return.
    `\n` Matches a line feed.
    `\v` Matches a vertical tab.
    `\f` Matches a form-feed.
    `[\b]` Matches a backspace.
    `\0` Matches a NUL character. Do not follow this with another digit.
    `\cX` Matches a control character using caret notation where "X" is a letter from A-Z.
    `\xhh` Matches the character with the code hh (two hexadecimal digits).
    `\xhhhh` Matches the UTF-16 code-unit with the value hhhh (four hexadecimal digits).
    `\u{hhhh}` or `\u{hhhhh}` (Only when the u flag is set) Matches the character with the Unicode value U+hhhh or U+hhhhh (hexadecimal digits).

### The OR Operator

    `|` The OR Operator matches the expression before or after itself

### Flags

-Flags or Modifiers are used to perform case-insensitive and global searches.
    `g` Finds all matches rather than stopping after the first match.
    `i` Performs case-insensitive matching.
    `m` Performs multiline matching.

### Character Escapes

-`\` Indicates that the following character should be treated specially, or "escaped". It behaves one of two ways.
    Example: `/\b/` For characters that are usually treated literally, indicates that the next character is special and not to be interpreted literally.
    Example: `/a\*/` For characters that are usually treated specially, indicates that the next character is not special and should be interpreted literally.

### Assertions

    `x(?=y)` Lookahead assertion: Matches "x" only if "x" is followed by "y".
    `x(?!y)` Negative lookahead assertion: Matches "x" only if "x" is not followed by "y".
    `(?<=y)x` Lookbehind assertion: Matches "x" only if "x" is preceded by "y".
    `(?<!y)x` Negative lookbehind assertion: Matches "x" only if "x" is not preceded by "y".

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
