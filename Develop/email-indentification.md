# How to understand a RegEx for an Email

RegEx, short for Regular Expression, is a way to validate whether a piece of code, text, passage or any amount of characters. It helps developers confirm the data they want to pass into their code accurately.

## Introduction

The RegEx I've chosen to explain validates an email, shown below:

```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```

## Table of Contents

- [Anchors](#anchors)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Quantifiers](#quantifiers)
- [Literals](#literals)
- [Miscellaneous Last Bits](#miscellaneous-last-bits)
- [Summary](#summary)

## Regex Components

### Anchors
#### ```/```
The easiest way to start and understand this RegEx is from the beginning. The whole code snippet is book-ended by two forward slashes (```/```). This can easily be copy-pasted directly into code allowing for the program to stop reading in the specified code and into RegEx understanding.
#### ```^```  ```$```
The next character, (```^```), indicates the start of the actual Regular Expression, and the second-to-last character (```$```) indicates the end of the RegEx and where the code should stop interpreting within RegEx.

### Grouping and Capturing
#### ```(``` ```)```
Parentheses group the specified characters together and create a group for capturing a string or substring. For example, a social media site might ask for your email when creating an account. Let's take a simple email: ```test123@email.com```. The parentheses in the RegEx group together 
1. all the letters and numbers before the ```@``` sign,  ```test123``` 
2. the characters between the ```@``` sign and period (```.```), ```email```
3. and the characters after the period (```.```), ```com```

```([a-z0-9_\.-]+)``` , ```([\da-z\.-]+)``` , ```([a-z\.]{2,6})``` respectively

### Bracket Expressions
#### ```[``` ```]```
Brackets designate things similar to parentheses, but are more restrictive. They simply define which specific value only 1 character has. In this case, the first character class expression we see is ```[a-z0-9_\.-]```. 

### Character Classes
Within this, one value can be any lowercase letter in the English alphabet (```a-z```), any single digit number (```0-9```), an underscore ( ```_``` ), and then something a bit more complicated: The ```\``` designation indicates that the next character will not follow RegEx documentation, but instead be interpreted literally. In this case, a period ( ```.``` ) has a meaning within RegEx so it cannot be used to simply stand for a period within the function. ```\.``` is used to indicate that the expression will allow a period to be taken in. The last character in the brackets, ( ```-``` ), simply indicates that the expression will allow a dash.

### Quantifiers
#### ```+```  , ```*``` , ```?```
Quantifiers placed after a bracketed character set do indicated how many (if any) characters the expression can allow. The plus sign allows for at least 1 of the preceding character set to be required. The asterisk allows for at least none of the preceding set. And the question mark allows either none of the preceding set or just one.

### Literals

The next value is ```@``` in this chosen expression. This does not have any RegEx meaning and simply requires the expression to follow the previous bracketed character set with an ```@``` sign.

### Miscellaneous Last Bits
#### ```\d```
In the second bracketed character set, the values ```\d``` indicate any digit, very similar to ```0-9```.
#### ```{``` ```}```
The last unique tokens in this expression are the curly braces. They are [quantifiers](#quantifiers) similar to ```+```  , ```*``` , and ```?``` but more precise. The first number (in this case ```2```) indicates the minimum amount of the preceding bracketed character set required. If only one number is present (ex. ```{2}```), then the expression requires exactly that amount. If there are 2 numbers seperated with a comma, it indicates the allowed range of the previous character set. If there is a comma and a number present, it designates either at least that amount or at most that amount (ex. ```{3,}``` at least 3 characters required and ```{,6}``` at most 6 characters required).

### Summary
The whole expression:

```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```

#### Breaking it up
#### ```([a-z0-9_\.-]+)```
This takes in a substring before an ```@``` sign containing at least one of any letter, number, underscore, period or dash.
#### ```@```
The expression must then be followed by an ```@``` sign.
#### ```([\da-z\.-]+)```
This takes in a substring between an ```@``` sign and period containing at least one of any letter, digit, underscore, period or dash.
#### ```\.```
The expression must then be followed by a period ( ```.``` ).
#### ```([a-z\.]{2,6})```
This takes in a substring after a period containing at least 2 but no more than 6 of any letter or period.

## Author
[Jeffry Langford](github.com/JeffryLangford)
