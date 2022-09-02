# RecognizingRegex

RecognizingRegex aims to remove the frustration of regular expressions. The first time a person sees a regex(regular expression) it's usually quite intimidating. However, what may initially seem like a series of unrelated alphanumeric characters, in a nonsensical format, is actually quite useful for developers. Here in this tutorial I will walk you through a single expression, but I aim to leave you with the tools necessary to tackle whatever regex you may encounter. Without further ado, Lets dive in!

## Summary

In this tutorial we will be looking at a regex that allows us to match an Email format. This would typically be used in confirming that a user input a valid email when creating an account with your site or application.

    `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Now lets make sense of this!

    `^` is the first character we come across. This just signifies that our next expression is checking the beginning of our string.</br>
    `(` next we are going to open a capturing group.</br>
    `[a-z0-9_\.-]` then we have a bracket expression. This one aims to confirm that:</br>

        `a-z` we have any character between a-z.</br>
        `0-9` we have any number between 0-9.</br>
        `_` will allow a match with underscores.</br>
        `\.` using the escape character with the . will allow a match with a dot.</br>
        `-` will allow a match a hyphen.</br>

    `+` then we add a plus sign to tell the regex to match from 1 to unlimited characters.</br>
    `)` then we will close our first capturing group.</br>
    `@` will match the At Sign only once.</br>
    `(` then we need to open another capturing group.</br>
    `[\da-z\.-]` this bracket expression will confirm that:</br>

        `\d` we have any digit (this is equivalent to putting [0-9]).</br>
        `a-z` we have any character between a-z.</br>
        `\.` using the escape character with the . will allow a match with a dot.</br>
        `-` will allow a match a hyphen.</br>

    `+` then we add a plus sign to tell the regex to match from 1 to unlimited characters.</br>
    `)` then we will close our second capturing group.</br>
    `\.` next we need to check for a single "." using the escape character with the "." will allow a match with a dot.</br>
    `(` then we need to open another capturing group.</br>
    `[a-z\.]` this bracket expression will confirm that:</br>

        `a-z` we have any character between a-z.</br>
        `\.` using the escape character with the . will allow a match with a dot.</br>
        
    `{2,6}` will confirm that the total characters matched with our bracket expression are at least 2 and no more than 6.</br>
    `)` then we will close our third capturing group.</br>
    `$` tells our third capturing group to be checking the end of the string.</br>

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
    `x?` Matches the preceding item "x" 0 or 1 times.
    `x{n}` Where "n" is a positive integer, matches exactly "n" occurrences of the preceeding item "x".
    `x{n,}` Where "n" is a positive integer, matches at least "n" occurrences of the preceding item "x".
    `x{n,m}` Where "n" is 0 or a positive integer, "m" is a positive integer, and m > n, matches at least "n" and at most "m" occurrences of the preceding item "x".

    -By default quantifiers are "greedy", meaning they try to match as much of the string as possible. The ? character after the quantifier makes it "non-greedy", meaning it will stop as soon as it finds a match. For example: `x*?``x+?``x??``x{n}?``x{n,}?``x{n,m}?`

* Examples include:

    `s*` will match every character in "javascript".
    `s+` will match only the "s" in "javascript".
    `s?` will match every character in "javascript".
    `s{2}` will not match "javascript" but will match twice in "mississippi".
    `s{1,3}`will match the "s" in "javascript" and the 3 "s" in "misss".

### Grouping Constructs

-Groups and back references indicate groups of expression characters.

    `(x)` Capturing group: Matches "x" and remembers the match.
    `(?<Name>x)` Named capturning group: Matches "x" and stores it on the groups property of the returned matches under the name specified by <Name>. Angle brackets are required for group name.
    `(?:x)` Non-capturing group: Matches "x" but does not remember the match.
    `\n` Where "n" is a positive integer. A back reference to the last substring matching the n parenthetical in the regex.
    `\k<Name>` A back reference to the last substring matching the Named capture group specified by <Name>.

* Examples include:

    `(s)` will match and group every "s" in "javascript miss".
    `(?<testGroup>s)` will match and group every "s" in "javascript miss" with the group name "testGroup".
    `s?` will match every "s" in "javascript miss" without grouping them.

### Bracket Expressions

-Brackets are used to find a range of characters.

    `[abc]` Matches any character within the brackets.
    `[^abc]` Matches any character not found within the brackets.
    `[0-9]` Matches any character within the bracket range.
    `[^0-9]` Matches any character NOT found within the brackets.

* Examples include:

    `[ajr]` will match every "a", "j", and "r" in "javascript".
    `[^ajr]` will match the "v", "s", "c", "i", "p", and "t" in "javascript".
    `[9]` will match the "9" in "19".
    `[^9]` will match the "1" in "19".

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

* Examples include:

    `.` will match every character in "javascript".
    `\w` will match every character except the "/" in "javascript/19".
    `\W` will match only the "/" in "javascript/19".
    `\s` will match only the " " in "javascript 19".
    `\S` will match every character except the " " in "javascript 19".

### The OR Operator

    `|` The OR Operator matches the expression before or after itself

* Examples include:

    `z|r` will match the "r" in "javascript 19".
    `9|r` will match both the "r" and the "9" in "javascript 19".

### Flags

-Flags or Modifiers are used to perform case-insensitive and global searches.

    `g` Finds all matches rather than stopping after the first match.
    `i` Performs case-insensitive matching.
    `m` Performs multiline matching.

### Character Escapes

-`\` Indicates that the following character should be treated specially, or "escaped". It behaves one of two ways.

* Examples include: 

    `/\b/` For characters that are usually treated literally, indicates that the next character is special and not to be interpreted literally.
    `/a\*/` For characters that are usually treated specially, indicates that the next character is not special and should be interpreted literally.

### Assertions

    `x(?=y)` Lookahead assertion: Matches "x" only if "x" is followed by "y".
    `x(?!y)` Negative lookahead assertion: Matches "x" only if "x" is not followed by "y".
    `(?<=y)x` Lookbehind assertion: Matches "x" only if "x" is preceded by "y".
    `(?<!y)x` Negative lookbehind assertion: Matches "x" only if "x" is not preceded by "y".

* Examples include:

    `s(?=r)` will not match any character in "javascript 19".
    `s(?!y)` will match the "s" in "javascript 19".
    `(?<=a)s` will match the "s" in "javascript 19".
    `(?<!a)s` will not match any character in "javascript 19".

## Author

I'm Hacker, don't worry tho, thats just my surname! I grew up in Charleston, SC and am currently residing in Atlanta, GA. I've always been a creative with a bit of a logical "bend". Web development allows me to combine those two parts of myself to help build a more beautiful, and efficient Web for everyone!

Fell free to follow my development projects on GitHub @ <a href="https://github.com/hackpres">hackpres</a>!<br/>
<img src="./img/hackpres.png" width="300"/>
