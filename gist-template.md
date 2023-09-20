# Regular Expression - Matching an Email

Regular expressions, often referred to as regex, refers to a distinct string usually made up of various sets of characters that can be used as both a query tool and a validator in code bases, as well as traditional documents. They were dervied in the early 1950s out of the concept of regular language coined by the mathemitician `Stephen Cole Kleene`. They became widely used in 1968 within the theoretical computer science field as a way to match patterns within text files and support lexical analysis. Although regular expressions are known for being extremely cryptic looking, when broken down piece by piece, one can see they are not quite as complex as they look to the untrained eye, and one could start writing their own regex expressions fairly easily.

## Summary

This tutorial will be covering the regex expression used for both matching and validating an email:

`^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`

"Consider you're a software developer tasked with identifying insecurely used email addresses within a codebase. Employing the regular expression provided below will expedite the process of identifying these email addresses. You can also utilize this regular expression as a string in your codebase to validate email addresses. By doing so, you ensure that when users submit forms requiring valid email addresses, they must adhere to a specific format: a minimum number of characters, followed by the '@' symbol, followed by a domain name with a variable length, and ending with a domain extension (e.g., .com, .net, .dev) of between 2 and 6 characters."

## Regex Components

Here's a breakdown of the components of the regular expression for email validation:

```regex
^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$
```

1. `^`: Asserts the start of the line, ensuring that the email address starts from the beginning.

2. `([a-z0-9_\.-]+)`: This is the local part of the email address, before the "@" symbol.
   - `([a-z0-9_\.-]+)`: It's enclosed in parentheses to create a capture group.
   - `[a-z0-9_\.-]`: Character class that allows lowercase letters, digits, underscores (_), dots (.), and hyphens (-).
   - `+`: Allows one or more occurrences of the characters in the character class.

3. `@`: Matches the "@" symbol, which separates the local part from the domain part.

4. `([\da-z\.-]+)`: This is the domain part of the email address.
   - `([\da-z\.-]+)`: Enclosed in parentheses to create a capture group.
   - `[\da-z\.-]`: Character class that allows lowercase letters, digits, dots (.), and hyphens (-).
   - `+`: Allows one or more occurrences of the characters in the character class.

5. `\.`: Matches the dot (.) character, which separates the domain from the domain extension.

6. `([a-z\.]{2,6})`: This part matches the domain extension (e.g., .com, .net).
   - `([a-z\.]{2,6})`: Enclosed in parentheses to create a capture group.
   - `[a-z\.]`: Character class that allows lowercase letters and dots (.) in the domain extension.
   - `{2,6}`: Specifies that the domain extension should have a length between 2 and 6 characters.

7. `$`: Asserts the end of the line, ensuring that the email address ends at this point.

In summary, this regular expression validates an email address by ensuring that it starts with a valid local part, followed by "@" symbol, a valid domain part, and ends with a valid domain extension. It's a comprehensive pattern for secure email validation.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)


### Anchors

Anchors within a regular expression serve as indicators for the beginning and end points of the expression. In this particular expression, the `^` signifies the start of the expression, while the `$` signifies the end of the expression.

### Quantifiers

Quantifiers are special characters that alter the behavior of the preceding character or character class in a regular expression, determining how many of them should be matched consecutively.

Quantifiers enable the definition of the desired number of characters or character classes to be matched:

- The `+` symbol matches one or more of the preceding character.
- `{min, max}` specifies a precise numeric range for quantification (notice that this is employed at the end of the regex expression above to specify a range for the domain name system).

### Grouping Constructs
In the regular expression `^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`, the grouping constructs are created using parentheses `(` and `)` to define capturing groups. These capturing groups are used to capture specific parts of the email address. Here's how each capturing group is constructed:

1. Capturing Group 1: `([a-z0-9_\.-]+)`
   - It starts with an opening parenthesis `(` to begin the capturing group.
   - Inside the group, it specifies the character class `[a-z0-9_\.-]+`, which matches one or more lowercase letters, digits, underscores, dots, or hyphens.
   - It ends with a closing parenthesis `)` to close the capturing group.
   - This capturing group captures the local part (username) of the email address.

2. Capturing Group 2: `([\da-z\.-]+)`
   - Similar to the first group, it starts with an opening parenthesis `(`.
   - Inside the group, it specifies the character class `[\da-z\.-]+`, which matches one or more lowercase letters, digits, dots, or hyphens.
   - It ends with a closing parenthesis `)`.
   - This capturing group captures the domain name part of the email address (excluding the TLD).

3. Capturing Group 3: `([a-z\.]{2,6})`
   - Again, it starts with an opening parenthesis `(`.
   - Inside the group, it specifies the character class `[a-z\.]{2,6}`, which matches between 2 and 6 lowercase letters or dots.
   - It ends with a closing parenthesis `)`.
   - This capturing group captures the top-level domain (TLD) part of the email address.

These capturing groups allow you to extract and work with specific segments of the matched email address when using this regular expression for tasks like validation or data extraction.

### Bracket Expressions
`[]` define a character or group range and stand for a single character. In the context of the regular expression covered in this tutorial, these brackets serve to delineate each character class. Any character specified within the brackets can be a valid match.

For instance: `[a-z0-9_\.-]` can match any of the following:
- Any lowercase letter from `a` to `z`
- Any digit from `0` to `9`
- An underscore `_`
- A period `.`
- A dash `-`

These brackets, when used in a regular expression, offer flexibility in specifying acceptable characters or character ranges for matching purposes.

### Character Classes
Character classes are the attribute in a regex expression that allow us to define specific sets of characters that can be used in a search pattern.

The character classes utilized in this regex expression are `[a-z0-9_\.-]`, `[\da-z\.-]`, and `[a-z\.]`.

`[a-z0-9_\.-]`: `a-z` matches a single character in the range between a (index 97) and z (index 122) (case sensitive), `0-9` matches a single character in the range between 0 (index 48) and 9 (index 57) (case sensitive), `_` matches the character _ with index 9510 (5F16 or 1378) literally (case sensitive), `\.` matches the character . with index 4610 (2E16 or 568) literally (case sensitive), and `-` matches the character - with index 4510 (2D16 or 558) literally (case sensitive).

`[\da-z\.-]`: `\d` can be used to match any digit (0-9), `a-z` matches a single character in the range between a (index 97) and z (index 122) (case sensitive), `\.` matches the character . with index 4610 (2E16 or 568) literally (case sensitive), and `-` matches the character - with index 4510 (2D16 or 558) literally (case sensitive).

`[a-z\.]`: `a-z` matches a single character in the range between a (index 97) and z (index 122) (case sensitive), and `\.` matches the character . with index 4610 (2E16 or 568) literally (case sensitive)

Other examples of single characters:

`\d` can be used to match any digit (0-9), `\w` to match any alphanumeric character (a-zA-Z0-9), and `\s` any white space such as a space or a tab

### The OR Operator
There are no OR operators within this particular regex expression but in general OR operators are represented with the pipe `|` and specified under the regex type of alternation.

### Flags
Regex flags are employed to alter the behavior of an expression, affecting aspects such as case sensitivity. In JavaScript, there are only six available flags:

-  `i`: Enables case-insensitive matching.
-  `g`: Searches for all occurrences, not just the first match.
-  `m`: Activates multiline mode, allowing `^` and `$` to match the start and end of each line.
-  `s`: Enables "dotall" mode, permitting a dot `.` to match newline characters (`\n`).
-  `u`: Provides comprehensive Unicode support for matching Unicode characters.
-  `y`: Activates "sticky" mode, ensuring that the search starts at the current position in the target string.

It's worth noting that the regex expression explained in this tutorial does not make use of any flags.

### Character Escapes
Character escapes in regular expressions are used to match specific characters or character classes. Here are the character escapes for the flags mentioned in the previous response:

 `\i`: Case-insensitive matching.
 `\g`: Searches for all occurrences.
 `\m`: Multiline mode.
 `\s`: Dotall mode (matches newline characters with `.`).
 `\u`: Unicode support.
 `\y`: Sticky mode.

These escapes are used to enable or disable the corresponding flag's behavior within a regular expression.

### Greedy and Lazy Match

In regular expressions, both greedy and lazy quantifiers are used to control how much text a quantifier should match. Here's the difference between the two:

1. Greedy Quantifier: Greedy quantifiers match as much text as possible while still allowing the overall regex to match. They are represented by appending a quantifier with a `?`. For example, `*`, `+`, `?`, and `{}` can be made greedy by adding a `?` after them.

   Greedy quantifiers try to match the maximum number of characters while still allowing the overall regex to succeed. For instance, in the regex `.*`, the `*` is greedy and will try to match as many characters as possible.

2. Lazy (Non-Greedy) Quantifier: Lazy quantifiers match as little text as possible while still allowing the overall regex to match. They are represented by appending a quantifier with a `??`. For example, `*?`, `+?`, `??`, and `{}` can be made lazy by adding a `??` after them.

   Lazy quantifiers try to match the minimum number of characters necessary for the overall regex to succeed. For example, in the regex `.*?`, the `*?` is lazy and will try to match as few characters as possible.

Here's a brief summary of the two:

- Greedy quantifiers (`*`, `+`, `?`, `{}` without `?`) match as much as possible.
- Lazy quantifiers (`*?`, `+?`, `??`, `{}` with `??`) match as little as possible.


### Boundaries

`\b` is an example of a word boundary. It usually represents matching positions on either side; where once side is a word character and the other is something other than a word character.

Word boundaries are particularlly useful when you want to match a sequence of letters or digits on their own, to ensure they occur at the beginnning or end of a specific sequence of characters.

### Back-references

Back-references are commands which refer to a previous part of the matched regualr expression. They are generally specified with a backslash and a single digit `\2`

### Look-ahead and Look-behind

Usually represented with `?=foo`, look-ahead represents what immediately follows the string "foo", while look-behind, the inverse, is notated as `?<=foo` and represents what immediately precedes the string "foo".

## Author

I am a passionate and aspiring developer with in depth knowledege of full stack applications and know languages like Java, Javascript, Express, Node JS, Python, SQL and many more. 
If you have any questions about this projects, please contact me directly at <a href="mailto:alekhyavinni12@gmail.com">alekhyavinni12@gmail.com</a>
You can view more of my projects at [Link to Github](https://github.com/alekhyavinni)