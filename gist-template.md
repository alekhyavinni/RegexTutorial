# Regular Expression - Matching an Email

Regular expressions, often referred to as regex, refers to a distinct string usually made up of various sets of characters that can be used as both a query tool and a validator in code bases, as well as traditional documents. They were dervied in the early 1950s out of the concept of regular language coined by the mathemitician Stephen Cole Kleene. They became widely used in 1968 within the theoretical computer science field as a way to match patterns within text files and support lexical analysis. Although regular expressions are known for being extremely cryptic looking, when broken down piece by piece, one can see they are not quite as complex as they look to the untrained eye, and one could start writing their own regex expressions fairly easily.

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

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
