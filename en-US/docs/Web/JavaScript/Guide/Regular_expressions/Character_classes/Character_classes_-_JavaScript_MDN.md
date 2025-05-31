# Character classes - JavaScript | MDN

**Source URL:** [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Character_classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Character_classes)  
**Last Updated:** 2025-05-24T14:00:31.805Z  
**Extracted:** 2025-05-31 16:59:30

---

# Character classes - JavaScript | MDN

Character classes distinguish kinds of characters such as, for example, distinguishing between letters and digits.

## [Try it](#try_it)

#### JavaScript Demo: RegExp Character classes

#### JavaScript Demo: RegExp Character classes

```
const chessStory = "He played the King in a8 and she moved her Queen in c2.";
const regexpCoordinates = /\w\d/g;
console.log(chessStory.match(regexpCoordinates));
// Expected output: Array [ 'a8', 'c2']

const moods = "happy 🙂, confused 😕, sad 😢";
const regexpEmoticons = /[\u{1F600}-\u{1F64F}]/gu;
console.log(moods.match(regexpEmoticons));
// Expected output: Array ['🙂', '😕', '😢']
```

## [Types](#types)

| Characters | Meaning |
| --- | --- |
| `[xyz]   [a-c]` | [**Character class:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class) Matches any one of the enclosed characters. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character enclosed in the square brackets, it is taken as a literal hyphen to be included in the character class as a normal character.<br><br>For example, `[abcd]` is the same as `[a-d]`. They match the "b" in "brisket", and the "c" in "chop".<br><br>For example, `[abcd-]` and `[-abcd]` match the "b" in "brisket", the "c" in "chop", and the "-" (hyphen) in "non-profit".<br><br>For example, `[\w-]` is the same as `[A-Za-z0-9_-]`. They both match the "b" in "brisket", the "c" in "chop", and the "n" in "non-profit".<br><br>When the [`unicodeSets`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/unicodeSets) (`v`) flag is enabled, the character class has some additional features. See the [character class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class) reference for more information. |
| `[^xyz]   [^a-c]` | [**Negated character class:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class) Matches anything that is not enclosed in the square brackets. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first character after the `^` or the last character enclosed in the square brackets, it is taken as a literal hyphen to be included in the character class as a normal character. For example, `[^abc]` is the same as `[^a-c]`. They initially match "o" in "bacon" and "h" in "chop".<br><br>**Note:** The ^ character may also indicate the [beginning of input](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Assertions). |
| `.` | [**Wildcard:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Wildcard) Matches any single character _except_ line terminators: `\n`, `\r`, `\u2028` or `\u2029`. For example, `/.y/` matches "my" and "ay", but not "yes", in "yes make my day", as there is no character before "y" in "yes". If the [`dotAll`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/dotAll) (s) flag is enabled, also matches line terminators. Inside a character class, the dot loses its special meaning and matches a literal dot. |
| `\d` | [**Digit character class escape:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class_escape) Matches any digit (Arabic numeral). Equivalent to `[0-9]`. For example, `/\d/` or `/[0-9]/` matches "2" in "B2 is the suite number". |
| `\D` | [**Non-digit character class escape:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class_escape) Matches any character that is not a digit (Arabic numeral). Equivalent to `[^0-9]`. For example, `/\D/` or `/[^0-9]/` matches "B" in "B2 is the suite number". |
| `\w` | [**Word character class escape:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class_escape) Matches any alphanumeric character from the basic Latin alphabet, including the underscore. Equivalent to `[A-Za-z0-9_]`. For example, `/\w/` matches "a" in "apple", "5" in "$5.28", "3" in "3D" and "m" in "Émanuel". |
| `\W` | [**Non-word character class escape:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class_escape) Matches any character that is not a word character from the basic Latin alphabet. Equivalent to `[^A-Za-z0-9_]`. For example, `/\W/` or `/[^A-Za-z0-9_]/` matches "%" in "50%" and "É" in "Émanuel". |
| `\s` | [**White space character class escape:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class_escape) Matches a single white space character, including space, tab, form feed, line feed, and other Unicode spaces. Equivalent to `[\f\n\r\t\v\u0020\u00a0\u1680\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff]`. For example, `/\s\w*/` matches " bar" in "foo bar". |
| `\S` | [**Non-white space character class escape:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class_escape) Matches a single character other than white space. Equivalent to `[^\f\n\r\t\v\u0020\u00a0\u1680\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff]`. For example, `/\S\w*/` matches "foo" in "foo bar". |
| `\t` | Matches a horizontal tab. |
| `\r` | Matches a carriage return. |
| `\n` | Matches a linefeed. |
| `\v` | Matches a vertical tab. |
| `\f` | Matches a form-feed. |
| `[\b]` | Matches a backspace. If you're looking for the word-boundary assertion (`\b`), see [Assertions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Assertions). |
| `\0` | Matches a NUL character. Do not follow this with another digit. |
| `\c_X_` | Matches a control character using [caret notation](https://en.wikipedia.org/wiki/Caret_notation), where "X" is a letter from A–Z (corresponding to code points `U+0001`_–_`U+001A`). For example, `/\cM\cJ/` matches "\\r\\n". |
| `\x_hh_` | Matches the character with the code `_hh_` (two hexadecimal digits). |
| `\u_hhhh_` | Matches a UTF-16 code-unit with the value `_hhhh_` (four hexadecimal digits). |
| `\u_{hhhh}_ or _\u{hhhhh}_` | (Only when the `u` flag is set.) Matches the character with the Unicode value `U+_hhhh_` or `U+_hhhhh_` (hexadecimal digits). |
| `\p{_UnicodeProperty_}`, `\P{_UnicodeProperty_}` | [**Unicode character class escape:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Unicode_character_class_escape) Matches a character based on its Unicode character properties: for example, emoji characters, or Japanese _katakana_ characters, or Chinese/Japanese Han/Kanji characters, etc.). |
| `\` | Indicates that the following character should be treated specially, or "escaped". It behaves one of two ways.<br><br>*   For characters that are usually treated literally, indicates that the next character is special and not to be interpreted literally. For example, `/b/` matches the character "b". By placing a backslash in front of "b", that is by using `/\b/`, the character becomes special to mean match a word boundary.<br>*   For characters that are usually treated specially, indicates that the next character is not special and should be interpreted literally. For example, "\*" is a special character that means 0 or more occurrences of the preceding character should be matched; for example, `/a*/` means match 0 or more "a"s. To match `*` literally, precede it with a backslash; for example, `/a\*/` matches "a\*".<br><br>**Note:** To match this character literally, escape it with itself. In other words to search for `\` use `/\\/`. |
| `_x_\|_y_` | [**Disjunction:**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Disjunction) Matches either "x" or "y". Each component, separated by a pipe (`\|`), is called an _alternative_. For example, `/green\|red/` matches "green" in "green apple" and "red" in "red apple".<br><br>**Note:** A disjunction is another way to specify "a set of choices", but it's not a character class. Disjunctions are not atoms — you need to use a [group](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Groups_and_backreferences) to make it part of a bigger pattern. `[abc]` is functionally equivalent to `(?:a\|b\|c)`. |

## [Examples](#examples)

### [Looking for a series of digits](#looking_for_a_series_of_digits)

In this example, we match a sequence of 4 digits with `\d{4}`. `\b` indicates a [word boundary](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Assertions) (i.e., do not start or end matching in the middle of a number sequence).

```
const randomData = "015 354 8787 687351 3512 8735";
const regexpFourDigits = /\b\d{4}\b/g;

console.table(randomData.match(regexpFourDigits));
// ['8787', '3512', '8735']
```

See more examples in the [character class escape](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class_escape) reference.

### [Looking for a word (from the latin alphabet) starting with A](#looking_for_a_word_from_the_latin_alphabet_starting_with_a)

In this example, we match a word starting with the letter A. `\b` indicates a [word boundary](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Assertions) (i.e., do not start matching in the middle of a word). `[aA]` indicates the letter "a" or "A". `\w+` indicates any character _from the Latin alphabet_, multiple times (`+` is a [quantifier](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Quantifiers)). Note that because we already match until there are no more word characters, an end `\b` boundary is not necessary.

```
const aliceExcerpt =
  "I'm sure I'm not Ada,' she said, 'for her hair goes in such long ringlets, and mine doesn't go in ringlets at all.";
const regexpWordStartingWithA = /\b[aA]\w+/g;

console.table(aliceExcerpt.match(regexpWordStartingWithA));
// ['Ada', 'and', 'at', 'all']
```

See more examples in the [character class escape](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class_escape) reference.

### [Looking for a word (from Unicode characters)](#looking_for_a_word_from_unicode_characters)

Instead of the Latin alphabet, we can use a range of Unicode characters to identify a word (thus being able to deal with text in other languages like Russian or Arabic). The "Basic Multilingual Plane" of Unicode contains most of the characters used around the world and we can use character classes and ranges to match words written with those characters.

```
const nonEnglishText = "Приключения Алисы в Стране чудес";
const regexpBMPWord = /([\u0000-\u0019\u0021-\uFFFF])+/gu;
// BMP goes through U+0000 to U+FFFF but space is U+0020

console.table(nonEnglishText.match(regexpBMPWord));
["Приключения", "Алисы", "в", "Стране", "чудес"];
```

See more examples in the [Unicode character class escape](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Unicode_character_class_escape) reference.

### [Counting vowels](#counting_vowels)

In this example, we count the number of vowels (A, E, I, O, U, Y) in a text. The `g` flag is used to match all occurrences of the pattern in the text. The `i` flag is used to make the pattern case-insensitive, so it matches both uppercase and lowercase vowels.

```
const aliceExcerpt =
  "There was a long silence after this, and Alice could only hear whispers now and then.";
const regexpVowels = /[aeiouy]/gi;

console.log("Number of vowels:", aliceExcerpt.match(regexpVowels).length);
// Number of vowels: 26
```

## [See also](#see_also)

---

*This documentation was extracted from the database for URLs containing 'developer.mozilla'*
