# Regex
# Regular Expressions

## Test Method

Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching.

The `.test()` method takes the regex, applies it to a string (which is placed inside the parentheses), and returns `true` or `false` if your pattern finds something or not.

```js
let testStr = "freeCodeCamp";
let testRegex = /Code/;
testRegex.test(testStr);
```

The `test` method here returns `true`.

### Extract Matches

So far, you have only been checking if a pattern exists or not within a string. You can also extract the actual matches you found with the `.match()` method.

To use the `.match()` method, apply the method on a string and pass in the regex inside the parentheses.

Here's an example:

```js
"Hello, World!".match(/Hello/);
let ourStr = "Regular expressions";
let ourRegex = /expressions/;
ourStr.match(ourRegex);
```

Here the first `match` would return `["Hello"]` and the second would return `["expressions"]`.

Note that the `.match` syntax is the "opposite" of the `.test` method you have been using thus far:

```js
'string'.match(/regex/);
/regex/.test('string');
```

---

Apply the `.match()` method to extract the string `coding`.

```js
let extractStr = "Extract the word 'coding' from this string.";
let codingRegex = /coding/;
let result = extractStr.match(codingRegex);
```

---

## Test and Matches

### Test

- *regexObject*.test( *String* )
  
- returns true or false
  
- Executes the search for a match between a regular expression and a specified string.
  

### Match

- *string*.match(RegExp )
  
- returns an array if it matches. if there are no matches it returns null
  
- Used to retrieve the matches when matching a string against a regular expression.
  

Use `.test` if you want a faster boolean check. Use `.match` to retrieve all matches when using the `g` global flag.

---

## Flags

i - ignores case

An example of using this flag is `/Ignorecase/i`. This regex can match the strings `ignorecase`, `igNoreCase`, and `IgnoreCase`.

g - global flag - With this flag the search looks for all matches, without it – only the first match is returned.

```js
let testStr = "Repeat, Repeat, Repeat";
let repeatRegex = /Repeat/g;
testStr.match(repeatRegex);
```

And here `match` returns the value `["Repeat", "Repeat", "Repeat"]`

we can have multiple flags in regex as well. for example:

```js
let twinkleStar = "Twinkle, twinkle, little star";
let starRegex = /Twinkle/ig; 
let result = twinkleStar.match(starRegex); 
//result = [ 'Twinkle', 'twinkle' ]
```

---

- [[abc]](#Match-Single-Character-with-Multiple-Possibilities) Find any character between the brackets
  
- [[^abc]](#Match-Single-Characters-Not-Specified) Find any character NOT between the brackets
  
- [^0-9] Find any character NOT between the brackets (any non-digit)
  
- (x|y) Find any of the alternatives specified
  

#### Metacharacters - characters with a special meaning

- [.](#Match-Anything-with-Wildcard-Period) Find a single character, except newline or line terminator
  
- [?](#Find-Characters-with-Lazy-Matching) to make a part of a pattern optional, meaning it may occur zero times or one time.
  
- [\w](#Match-All-Letters-and-Numbers) Match All Letters and Numbers
  
- [\W](#Match-Everything-But-Letters-and-Numbers) Find a non-word character
  
- [\d](#Match-All-Numbers) Find a digit
  
- \D Find a non-digit character
  
- [\s](#Match-Whitespace) Find a whitespace character
  
- \S Find a non-whitespace character
  
- [?=n](#Positive-and-Negative-Lookahead) Matches any string that is followed by a specific string n
  
- [?!n](#Positive-and-Negative-Lookahead) Matches any string that is not followed by a specific string n
  

#### quantifiers

- [n+](#Match-Characters-that-Occur-One-or-More-Times) Matches any string that contains at least one n
  
- [n*](#Match-Characters-that-Occur-Zero-or-More-Times) Matches any string that contains zero or more occurrences of n
  

---

---

### Match Anything with Wildcard Period

```js
let humStr = "I'll hum a song";
let hugStr = "Bear hug";
let huRegex = /hu./;
huRegex.test(humStr);
huRegex.test(hugStr);
```

if you wanted to match `hug`, `huh`, `hut`, and `hum`, you can use the regex `/hu.`

### Match Single Character with Multiple Possibilities

```js
let bogStr = "bog";
let bgRegex = /b[aiu]g/;
bigStr.match(bgRegex);
```

---

Use a character class with vowels (`a`, `e`, `i`, `o`, `u`) in your regex `vowelRegex` to find all the vowels in the string `quoteSample`.

**Note:** Be sure to match both upper- and lowercase vowels.

```js
let quoteSample = "Beware of bugs in the above code; I have only proved it correct, not tried it.";
let vowelRegex = /[aeiou]/ig;
let result = quoteSample.match(vowelRegex); 
//result = [
//  'e', 'a', 'e', 'o', 'u', 'i',
//  'e', 'a', 'o', 'e', 'o', 'e',
//  'I', 'a', 'e', 'o', 'o', 'e',
//  'i', 'o', 'e', 'o', 'i', 'e',
//  'i'
//]
```

---

### Match Single Characters Not Specified

 `/[^aeiou]/gi` matches all characters that are not a vowel. Note that characters like `.`, `!`, `[`, `@`, `/` and white space are matched - the negated vowel character set only excludes the vowel characters.

---

Create a single regex that matches all characters that are not a number or a vowel. Remember to include the appropriate flags in the regex.

---

```js
let quoteSample = "3 blind mice.";
let myRegex = /[^aeiou0-9]/ig;  
let result = quoteSample.match(myRegex);  
console.log(result)
// result = [
//  ' ', 'b', 'l',
//  'n', 'd', ' ',
//  'm', 'c', '.'
//]
```

# Match Characters that Occur One or More Times

`/a+/g` would find one match in `abc` and return `["a"]`. Because of the `+`, it would also find a single match in `aabc` and return `["aa"]`.

# Match Characters that Occur Zero or More Times

The character to do this is the asterisk or star: `*`.

```js
let soccerWord = "gooooooooal!";
let gPhrase = "gut feeling";
let oPhrase = "over the moon";
let goRegex = /go*/;
soccerWord.match(goRegex);
gPhrase.match(goRegex);
oPhrase.match(goRegex);
```

In order, the three `match` calls would return the values `["goooooooo"]`, `["g"]`, and `null`.

# Find Characters with Lazy Matching

In regular expressions, a greedy match finds the longest possible part of a string that fits the regex pattern and returns it as a match. The alternative is called a lazy match, which finds the smallest possible part of the string that satisfies the regex pattern.

You can apply the regex `/t[a-z]*i/` to the string `"titanic"`. This regex is basically a pattern that starts with `t`, ends with `i`, and has some letters in between.

Regular expressions are by default greedy, so the match would return `["titani"]`. It finds the largest sub-string possible to fit the pattern.

However, you can use the `?` character to change it to lazy matching. `"titanic"` matched against the adjusted regex of `/t[a-z]*?i/` returns `["ti"]`.

**Note:** Parsing HTML with regular expressions should be avoided, but pattern matching an HTML string with regular expressions is completely fine.

---

Fix the regex `/<.*>/` to return the HTML tag `<h1>` and not the text `"<h1>Winter is coming</h1>"`. Remember the wildcard `.` in a regular expression matches any character.

---

# Match Beginning String Patterns

```js
let firstString = "Ricky is first and can be found.";
let firstRegex = /^Ricky/;
firstRegex.test(firstString);
let notFirst = "You can't find Ricky now.";
firstRegex.test(notFirst);
```

The first `test` call would return `true`, while the second would return `false`.

# Match Ending String Patterns

```js
let theEnding = "This is a never ending story";
let storyRegex = /story$/;
storyRegex.test(theEnding);
let noEnding = "Sometimes a story will have to end";
storyRegex.test(noEnding);
```

The first `test` call would return `true`, while the second would return `false`.

# Match All Letters and Numbers

```js
let longHand = /[A-Za-z0-9_]+/;
let shortHand = /\w+/;
let numbers = "42";
let varNames = "important_var";
longHand.test(numbers);
shortHand.test(numbers);
longHand.test(varNames);
shortHand.test(varNames);
```

All four of these `test` calls would return `true`.

# Match Everything But Letters and Numbers

You can search for the opposite of the `\w` with `\W`. Note, the opposite pattern uses a capital letter. This shortcut is the same as `[^A-Za-z0-9_]`.

```js
let shortHand = /\W/;
let numbers = "42%";
let sentence = "Coding!";
numbers.match(shortHand);
sentence.match(shortHand);
```

The first `match` call would return the value `["%"]` and the second would return `["!"]`.

# Match All Numbers

The shortcut to look for digit characters is `\d`, with a lowercase `d`. This is equal to the character class `[0-9]`, which looks for a single character of any number between zero and nine.

# Restrict Possible Usernames

1. Usernames can only use alpha-numeric characters.
  
2. The only numbers in the username have to be at the end. There can be zero or more of them at the end. Username cannot start with the number.
  
3. Username letters can be lowercase and uppercase.
  
4. Usernames have to be at least two characters long. A two-character username can only use alphabet letters as characters.
  

---

Change the regex `userCheck` to fit the constraints listed above.

```js
let username = "JackOfAllTrades";
let userCheck = /^[A-z]+[A-z]+\d*$|^[A-z]+\d+\d$/;  
let result = userCheck.test(username);
```

# Match Whitespace

You can search for whitespace using `\s`, which is a lowercase `s`. This pattern not only matches whitespace, but also carriage return, tab, form feed, and new line characters. You can think of it as similar to the character class `[ \r\t\f\n\v]`.

```js
let whiteSpace = "Whitespace. Whitespace everywhere!"
let spaceRegex = /\s/g;
whiteSpace.match(spaceRegex);
```

This `match` call would return `[" ", " "]`.

non-Whitespace /\S/g

# Specify Upper and Lower Number of Matches

Recall that you use the plus sign `+` to look for one or more characters and the asterisk `*` to look for zero or more characters. These are convenient but sometimes you want to match a certain range of patterns.

You can specify the lower and upper number of patterns with quantity specifiers. Quantity specifiers are used with curly brackets (`{` and `}`). You put two numbers between the curly brackets - for the lower and upper number of patterns.

For example, to match only the letter `a` appearing between `3` and `5` times in the string `ah`, your regex would be `/a{3,5}h/`.

```js
let A4 = "aaaah";
let A2 = "aah";
let multipleA = /a{3,5}h/;
multipleA.test(A4);
multipleA.test(A2);
```

The first `test` call would return `true`, while the second would return `false`.

---

Change the regex `ohRegex` to match the entire phrase `Oh no` only when it has `3` to `6` letter `h`'s.

---

```js
let ohStr = "Ohhh no";
let ohRegex = /Oh{3,6}\sno/gi;  
let result = ohRegex.test(ohStr);
console.log(result)
```

# Specify Only the Lower Number of Matches

Change the regex `haRegex` to match the word `Hazzah` only when it has four or more letter `z`'s.

```js
let haStr = "Hazzzzah";
let haRegex = /Haz{4,}ah/;  
let result = haRegex.test(haStr);
```

# Specify Exact Number of Matches

```js
let A4 = "haaaah";
let A3 = "haaah";
let A100 = "h" + "a".repeat(100) + "h";
let multipleHA = /ha{3}h/;
multipleHA.test(A4);
multipleHA.test(A3);
multipleHA.test(A100);
```

In order, the three `test` calls would return `false`, `true`, and `false`.

# Check for All or None

```js
let american = "color";
let british = "colour";
let rainbowRegex= /colou?r/;
rainbowRegex.test(american);
rainbowRegex.test(british);
```

Both uses of the `test` method would return `true`.

# Positive and Negative Lookahead

Lookaheads are patterns that tell JavaScript to look-ahead in your string to check for patterns further along. This can be useful when you want to search for multiple patterns over the same string.

There are two kinds of lookaheads: positive lookahead and negative lookahead.

A positive lookahead will look to make sure the element in the search pattern is there, but won't actually match it. A positive lookahead is used as `(?=...)` where the `...` is the required part that is not matched.

On the other hand, a negative lookahead will look to make sure the element in the search pattern is not there. A negative lookahead is used as `(?!...)` where the `...` is the pattern that you do not want to be there. The rest of the pattern is returned if the negative lookahead part is not present.

```js
let quit = "qu";
let noquit = "qt";
let quRegex= /q(?=u)/;
let qRegex = /q(?!u)/;
quit.match(quRegex);
noquit.match(qRegex);
```

Both of these `match` calls would return `["q"]`.

A more practical use of lookaheads is to check two or more patterns in one string. Here is a (naively) simple password checker that looks for between 3 and 6 characters and at least one number:

```js
let password = "abc123";
let checkPass = /(?=\w{3,6})(?=\D*\d)/;
checkPass.test(password);
```

Use lookaheads in the `pwRegex` to match passwords that are greater than 5 characters long, and have two consecutive digits.

```js
let sampleWord = "astronaut";
let pwRegex = /(?=\w{5,})(?=\D*[A-z]\d\d)/;  
let result = pwRegex.test(sampleWord);
```

# Check For Mixed Grouping of Characters

If you want to find either `Penguin` or `Pumpkin` in a string, you can use the following Regular Expression: `/P(engu|umpk)in/g`

```js
let testStr = "Pumpkin";
let testRegex = /P(engu|umpk)in/;
testRegex.test(testStr);
```

The `test` method here would return `true`.

Fix the regex so that it checks for the names of `Franklin Roosevelt` or `Eleanor Roosevelt` in a case sensitive manner and it should make concessions for middle names.

Then fix the code so that the regex that you have created is checked against `myString` and either `true` or `false` is returned depending on whether the regex matches.

```js
let myString = "Franklin D. Roosevelt";
let myRegex = /(Franklin|Franklin D.|Eleanor)Roosevelt/;
let result = myRegex.test(myString); 
// After passing the challenge experiment with myString and see how the grouping works
console.log(result)Reuse Patterns Using Capture Groups
```

# Reuse Patterns Using Capture Groups

You could use `/row row row/`, but what if you don't know the specific word repeated? Capture groups can be used to find repeated substrings.

Capture groups are constructed by enclosing the regex pattern to be captured in parentheses. In this case, the goal is to capture a word consisting of alphanumeric characters so the capture group will be `\w+` enclosed by parentheses: `/(\w+)/`.

```js
let repeatNum = "42 42 42";
let reRegex = /^(\d+)\s\1 \1$/;
let result = reRegex.test(repeatNum);
console.log(result)
```

# Remove Whitespace from Start and End

Write a regex and use the appropriate string methods to remove whitespace at the beginning and end of strings.

**Note:** The `String.prototype.trim()` method would work here, but you'll need to complete this challenge using regular expressions.

let hello = "   Hello, World!  ";

let wsRegex = /^\s+|\s+$/g; // Change this line

let result = hello.replace(wsRegex, '') // Change this line

console.log(result)

# Use Capture Groups to Search and Replace

Searching is useful. However, you can make searching even more powerful when it also changes (or replaces) the text you match.

You can search and replace text in a string using `.replace()` on a string. The inputs for `.replace()` is first the regex pattern you want to search for. The second parameter is the string to replace the match or a function to do something.

```js
let wrongText = "The sky is silver.";
let silverRegex = /silver/;
wrongText.replace(silverRegex, "blue");
```

The `replace` call would return the string `The sky is blue.`.

You can also access capture groups in the replacement string with dollar signs (`$`).

```js
"Code Camp".replace(/(\w+)\s(\w+)/, '$2 $1');
```

The `replace` call would return the string `Camp Code`.

---

Write a regex `fixRegex` using three capture groups that will search for each word in the string `one two three`. Then update the `replaceText` variable to replace `one two three` with the string `three two one` and assign the result to the `result` variable. Make sure you are utilizing capture groups in the replacement string using the dollar sign (`$`) syntax.

```js
let str = "one two three";
let fixRegex = /(\w+)\s(\w+)\s(\w+)/;  
let replaceText = '$3 $2 $1'; // Change this lin replace(fixRegex, replaceText);
```

# Find Characters with Lazy Matc

In regular expressions, a greedy match finds the longest possible part of a string that fits the regex pattern and returns it as a match. The alternative is called a lazy match, which finds the smallest possible part of the string that satisfies the regex pattern.

You can apply the regex `/t[a-z]*i/` to the string `"titanic"`. This regex is basically a pattern that starts with `t`, ends with `i`, and has some letters in between.

Regular expressions are by default greedy, so the match would return `["titani"]`. It finds the largest sub-string possible to fit the pattern.

However, you can use the `?` character to change it to lazy matching. `"titanic"` matched against the adjusted regex of `/t[a-z]*?i/` returns `["ti"]`.

**Note:** Parsing HTML with regular expressions should be avoided, but pattern matching an HTML string with regular expressions is completely fine.

---

Fix the regex `/<.*>/` to return the HTML tag `<h1>` and not the text `"<h1>Winter is coming</h1>"`. Remember the wildcard `.` in a regular expression matches any character.

```js
let text = "<h1>Winter is coming</h1>";
let myRegex = /<.*?>/;  
let result = text.match(myRegex);
```

#
