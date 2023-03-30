# Regex-tutorial - matching a hex value

This file focuses on creating a Regular expression tutorial which focuses on matching a hex value.
The descriptions below explain how a specific regular expression, or regex, functions by breaking down components of the expression and describing what it does. 



## Summary

A **regex**, which is short for **regular expression**, can be described as a sequence of characters that defines a specific search pattern. Regex is case sensitive. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input. Regex are also frequently used to validate input. 

We will be evaluating the following regular expressions used to match HEX values:

/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

Descriptions below will provide details of the anchors, quantifiers, OR Operator, grouping and capturing and bracket expressions used in this regular expression (focusing on matching HEX values).



## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping and Capturing](#grouping-and-capturring)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Author](#author)

## Regex Components

A regex is considered a literal, so the pattern must be wrapped in slash characters (/). If we examine the “Matching a Username” regex, you'll see that this is true:

Now let's take a look at the components of a regex in relation to matching a hex value:

### Anchors

Anchor: ^ Code Snipet: /^#

Description:
 Anchors match regular expressions by asserting something about the string (e.g. beginning, end) based on expressions/matching pattern next to the anchor.Anchors  do not match regular expressions by themselves.

For example: ^This indicates that the string must begin with This.

The ^ is an anchor which indicates that the beginning of the string must match the character #. # is what is used to distinguish a hexadecimal number from a decimal number. However, as we will see in the next anchor, # is optional.

Anchor: $

Code Snipet: $/

Description:

The $ anchor signifies a string that ends with the characters that precede it. The The $ anchor is used to check if a string matches properly with a pattern. It is used to assert a pattern to the end of the string. The $ anchor does not assert at the beginning of a string.

For Example: end$ indicates that the string must end with end.

So, in our “Matching a hex value” regex, the string must match with the 3 or 6 character pattern identified before the $ anchor. The 3 or 6 character pattern is described in more detail under Quantifiers below.


### Quantifiers

Quantifiers set the limits of the string that your regex matches (or an individual section of the string). They frequently include the minimum and maximum number of characters that your regex is looking for.

Quantifier: ?

Code Snipet: /^#?

Description:

In our matching a hex value regex, the quantifier ? indicates that the character # preceding the quantifier ? is optional. It's optional for # to appear at the beginning of the expression.

? implies a boolean value, 0 or 1. Typically, this makes the preceding symbol/character optional.

For example: This could be useful to distinguish between British and American spelling in a string e.g. colour vs color -- the regex would colou?r

Quantifier: {}

Code Snipet: [a-f0-9]{6} Code Snipet: [a-f0-9]{3}

Description:

Quantifier indicates the number of times the preceding pattern matches. Normally, the quantifiers are greedy, causing the regex to match as many occurrences of a particular pattern as possible. However, if ? was appended, the quantifier would become lazy-- causing the regex to match as few occurrences as possible. In our case, the quantifier is greedy.

For example: 2{5} indicates that 2 must be repeated 5 times. Matching string must be 22222.

In our regex, {6} indicates that there are 6 instances of the string in the preceding bracket expression. That implies that this quantifier will allow exactly 6 characters in the string containing characters between a-f and/or integer between 0-9. {3} indicates that there are 3 instances of the string in the preceding bracket expression. That implies that this quantifier will allow exactly 3 characters in the string containing characters between a-f and/or integer between 0-9.

### Grouping and Capturing
 
 Grouping and Capturing: ()

Code Snipet: ([a-f0-9]{6}|[a-f0-9]{3})

Description: The () works by grouping the regular expression between them. The grouping treats multiple characters as a single unit. This can be useful when extracting information using any programming language. This group of data will be exposed in the form of an array. Values can be accessed using an index on the result of the match.

For example: (pet){3} matched petpetpet. The unit of characters 'pet' would need to repeat 3 times indicated in the quantifier.

In our case, the grouped expression is a bracket expression whereby details are provided in the section below. Ultimately the end string anchor $ is applied to this grouping.

### Bracket Expressions

Bracket Expression: []

Code Snipet: [a-f0-9]

Description: Bracket expression is a regex that matches a specific pattern of characters (alphabetic, numeric, special characters, symbols etc..) defined within the brackets. Typically a hyphen(-) is used to describe a set or range of characters e.g. [a-z]. It is possible to use the ^ metacharacter to negate what is in between the brackets.

For example: [a-d 1-3] indicates that the string must include atleast 1 character that is between a and d or 1-3

In our reg ex, the bracket [] expression indicates matching a string that has any lower case character between a-f or any integer between 0-9

### Character Classes

A character class in a regex defines a set of characters, any one of which can occur in an input string to fulfill a match. We've actually already discussed some character classes. The bracket expressions outlined previously, including positive and negative character groups, are considered character classes.

Code Snipet: a-f0-9 Description: Character classes only matches one out of many characters defined in the character set. A hyphen can be used inside a character class to define a range of characters More than one range can be used -- as is the case in our code snipet.

For example: [0-9] This character class matches a single digit between 0 and 9

In our case, the character class consists of lower case a-f and/or integer 0-9.




### The OR Operator

Remember that a bracket expression does not require the string to meet all of the requirements in the pattern. This means that [a-z0-9_-] searches for alphanumeric characters or the two special characters included in the pattern. Often, you'll want to add this same logic outside of a bracket expression, especially within a grouping construct or between two different grouping constructs.

OR Operator: |

Code Snipet: [a-f0-9]{6}|[a-f0-9]{3}

Description: The | indicator (i.e. OR indicator) is a boolean that matches either the expression before or after.

For example: 3|5 indicates that either 3 or 5 or both integers are allowed in the string. 353 or 333 or 555 are all acceptable matching patterns.

In our case, that means match with 3 character string containing lower case a-f and/or integer 0-9 OR a string with 6 characters containing lowercase a-f and/or integer between 0-9. A matching string has to have 3 or 6 character with the specified pattern. Anything that is not 3 or 6 characters will not match.

## Greedy and Lazy Match

Code Snipet: [a-f0-9]{6} Code Snipet: [a-f0-9]{3}

Quantifier: {}

Description: Greedy means match the longest possible string. Lazy means match the shortest possible string.

For example: w.+l matches well in well but the lazy w.+?l matches wel

As described in the quantifier section above, normal quantifiers are greedy, which causes the regex to match as many occurrences of a particular pattern as possible. However, if ? was appended, the quantifier would become lazy-- causing the regex to match as few occurrences as possible. In our case, the quantifier is greedy.





## Author

My name is Awele Anita Lan. My main goal is to explore Javascript, Node.js, Sequelize, MySQL, CSS, HTML, React and other web technologies. My GitHub page has many projects while learning and exploring web technologies. Creating this tutorial via github gist is another way to describe and explore another important technology - Regex.

You will continue to see new projects in the future.

Author - Awele Anita LAN 
## Link to github profile below:
https://github.com/Awele1111/Reggex-tutorial
https://github.com/Awele1111
