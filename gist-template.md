# Regular Expression - Matching an Email

Regular expressions, often referred to as regex, refers to a distinct string usually made up of various sets of characters that can be used as both a query tool and a validator in code bases, as well as traditional documents. They were dervied in the early 1950s out of the concept of regular language coined by the mathemitician Stephen Cole Kleene. They became widely used in 1968 within the theoretical computer science field as a way to match patterns within text files and support lexical analysis. Although regular expressions are known for being extremely cryptic looking, when broken down piece by piece, one can see they are not quite as complex as they look to the untrained eye, and one could start writing their own regex expressions fairly easily.

## Summary

This tutorial will be covering the regex expression used for both matching and validating an email:

As a software developer you are tasked with finding and securing non-secure email usages within a codebase, you can use the following regular expression for email validation and detection:

```javascript
const emailRegex = /^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}$/;
```

Here's an explanation of the regular expression:

- `^[A-Za-z0-9._%+-]+`: This part matches the email's local part, which can contain letters (both uppercase and lowercase), digits, dots, underscores, percent signs, and plus or minus signs. It ensures that the local part starts at the beginning of the string.

- `@`: This part matches the "@" symbol in the email.

- `[A-Za-z0-9.-]+`: This part matches the domain name, which can contain letters (both uppercase and lowercase), digits, dots, and hyphens.

- `\.`: This matches the dot (.) that separates the domain name from the domain extension.

- `[A-Za-z]{2,6}`: This part matches the domain extension (e.g., .com, .net, .dev) and ensures it consists of 2 to 6 letters.

By using this regular expression, you can quickly search through the codebase to identify and validate email addresses. You can also use it to enforce email validation in forms, ensuring that users enter valid email addresses before proceeding.

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

### Anchors

### Quantifiers

### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
