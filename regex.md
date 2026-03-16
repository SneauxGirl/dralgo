```
 ______  ______  ______  ______  ______  
| |__| || |__| || |__| || |__| || |__| |
|  ()  ||  ()  ||  ()  ||  ()  ||  ()  |
|______||______||______||______||______|
```
------------------------------------------------------

# REGEX

------------------------------------------------------

// ===== Core Regex Symbols =====
```
.    → any character
\d   → digit
\w   → word character
\s   → whitespace
+    → one or more
*    → zero or more
^    → start of string
'$'    end of string (remove '' before use)
[]   → character set
[^]  → negated character set
()   → capture group
|    → OR
?    → lazy modifier / optional
```

------------------------------------------------------
## 1. Remove Non-Alphanumeric Characters
```
str.replace(/[^\w]/g, '')
```
```
Meaning:
• [ ... ] → character set
• ^ → NOT
• \w → word characters (a-z A-Z 0-9 _)
• g → global (all matches)

Translation: Remove everything that is not a letter, number, or underscore.
```

## 2. Remove Non-Letters
```
str.replace(/[^a-z]/gi, '')
```
```
Meaning:
• ^ → NOT
• a-z → lowercase letters
• g → global (all matches)
• i → case-insensitive (so A-Z too)

Translation: Remove everything that is not a letter (preserve case).
```

## 2. Collapse Multiple Whitespaces
```
str.replace(/\s+/g, ' ')
```
```
Meaning:
• \s → whitespace (space, tab, newline)
• + → one or more

Translation: Replace any group of whitespace with one space. Ruin ASCII art in a single line of code.
```

## 4. Trim Whitespace (manual)
```
str.replace(/^\s+|\s+$/g, '')
```
```
Meaning:
^      start of string
'$'    end of string (remove '' before use)
\s+    whitespace
|      OR

Combined:
^\s+   whitespace at start
\s+$   whitespace at end

Translation: Remove whitespace from start OR end. Equivalent to .trim(), but with more nuance.
```

## 5. Extract Digits
```
str.match(/\d+/g)
```
```
Meaning:
\d  digit
+   one or more

Translation: Extract digits.

Example: "order 66 costs 300 credits" returns ["66", "300"]
```

## 6. Basic Email Validation
```
/^[^\s@]+@[^\s@]+\.[^\s@]+$/
```
```
Meaning:
^            start
[^\s@]+      text before @
@            literal @
[^\s@]+      domain name
\.           dot
[^\s@]+      extension
'$'          end of string (remove '' before use)

Translation: Something@something.something

Good enough for basic type validation use cases. Edge cases need more nuance.
```

## 7. Lazy Matching
```
.*?
```
```
Meaning:
.   any character
*   zero or more (greedy by default)
?   lazy modifier (minimal match)

Translation: Match as little as possible. Useful for tags or patterns that would otherwise be consumed greedily.

Example:
"<tag>hello</tag><tag>world</tag>".match(/<tag>.*?<\/tag>/g)
// Returns ["<tag>hello</tag>", "<tag>world</tag>"]
```

## 8. Positive Lookahead
```
foo(?=bar)
```
```
Meaning:
foo      match literal 'foo'
(?=bar)  only if followed by 'bar' (lookahead)

Translation: Match 'foo' only if it is immediately followed by 'bar' without including 'bar' in the match.

Example:
"foobar".match(/foo(?=bar)/) // Returns ["foo"]
"foobar".match(/foo(?=bar)/) // Returns null
```

## 9. Negative Lookahead
```
foo(?!bar)
```
```
Meaning:
foo      match literal 'foo'
(?!bar)  only if NOT followed by 'bar' (lookahead)

Translation: Match 'foo' only if it is NOT immediately followed by 'bar' without including 'bar' in the match.

Example:
"foobar".match(/foo(?!bar)/) // Returns null
"foobar".match(/foo(?!bar)/) // Returns ["foo"]
```

## 10. Positive/Negative Lookbehind
```
(?<=) - positive lookbehind
(?<!) - negative lookbehind

(?>) - atomic group

An atomic group exits a group and throws away alternative patterns after the first matched pattern inside the group (backtracking is disabled).

(?>foo|foot)s applied to foots will match its 1st alternative foo, then fail as s does not immediately follow, and stop as backtracking is disabled
```

## 11. Word Boundaries
```
\bword\b
```
```
Meaning:
\b   boundary between word and non-word character

Translation: Match 'word' only as a whole word, not as part of another word.

Example:
"sword".match(/\bword\b/) // null
"word".match(/\bword\b/)  // ["word"]
"wording".match(/\bword\b/)// null
```

## 12. Capture Groups
```
(\d{4})-(\d{2})-(\d{2})
```
```
Meaning:
()      capture group
\d{4}   exactly 4 digits
\d{2}   exactly 2 digits
-       literal hyphen

Translation: Capture year, month, day separately in groups.

Example:
"2026-03-10".match(/(\d{4})-(\d{2})-(\d{2})/)
// $1 = "2026", $2 = "03", $3 = "10"

Reformat:
"2026-03-10".replace(/(\d{4})-(\d{2})-(\d{2})/, '$2/$3/$1')
// Returns "03/10/2026"
```
```
 ______  ______  ______  ______  ______ 
| |__| || |__| || |__| || |__| || |__| |
|  ()  ||  ()  ||  ()  ||  ()  ||  ()  |
|______||______||______||______||______|
```