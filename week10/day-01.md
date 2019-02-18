---
description: '/ bb | [^b] {2} /, that is the question...'
---

# Day 01

What we covered today:

* Regular expressions

### Warmup <a id="warmup"></a>

* Prime Factors

## Regular Expressions I <a id="regular-expressions-i"></a>

Regular Expressions are pattern matchers for text. Sounds relatively dry \(or very, very dry\) but they are incredibly powerful. They are often considered a write-only language. You can write it, but it is virtually impossible to read. They occur in lots and lots of programming languages \(they are even in javascript\), and if you are interested in the history of them - see [here](https://en.wikipedia.org/?title=Regular_expression#History) - but the way that Ruby works with them stems from the Perl programming language.

### So, how do we work with them in Ruby? <a id="so-how-do-we-work-with-them-in-ruby"></a>

#### _Literal Characters_ <a id="literal-characters"></a>

We can match literal characters in virtually the same way as we would with two equals signs. Instead of using the two equals signs though, we use `=~` , think of this as a fuzzy or dynamic search. To specify a regular expression in Ruby \(and most other languages\), we use `//` \(these are considered Regexp delimiters\). Let's have a muck around with them.

```ruby
"bob" == "bob" # This obviously returns true.
​
"bob" =~ /bob/
# This is true, they do match. But instead of returning true, it returns the index of where the pattern started to match. In this case, it returns 0.  It returns nil if it doesn't match anything.
​
"Hello, my name is bob" =~ /bob/
# Again, this is true, but returns 18
```

Obviously this isn't the powerful part though, considering this does virtually the same thing as the multiple equals signs. So let's get into some of the cooler stuff.

#### _Metacharacters_ <a id="metacharacters"></a>

In regular expressions, there are characters that mean far more than literal characters. This can prove problematic \(but there are ways to escape metacharacters\), but also the source of some of the most powerful parts.

```ruby
"o!o" =~ /o.o/ # Returns 0
```

#### _Character Classes_ <a id="character-classes"></a>

These are often used to check for capitalized and uncapitalized versions, but can also be used to check for multiple letters. The metacharacters for these are `[]`.

```javascript
"bob" =~ /[Bb]ob/  # Returns 0
"Bob" =~ /[Bb]ob/  # Returns 0
"cob" =~ /[Bbc]ob/ # Returns 0
"dog" =~ /[Bb]ob/  # Returns nil
"any vowels" =~ /[aeiou]/ # Returns 0
```

For this sort of stuff, we can also use ranges. These are quite useful.

```javascript
"A" =~ /[A-Z]/      # Returns 0
"a" =~ /[A-Z]/      # Returns nil
"a" =~ /[A-z]/      # Returns 0
```

There are lots of inbuilt ranges, and these are really useful to know. Some of them are...

* `\s` - Will match any space characters \(spaces, new lines etc.\)
* `\S` - Anything other than space characters
* `\w` - Will match any word character \(i.e. actual letters or numbers\)
* `\W` - Will match any non-word character

```ruby
"Wolf" =~ /[\w]/    # Returns 0
"Wolf" =~ /[\W]/    # Returns nil
"Wolf " =~ /[\W]/   # Returns 4
​
"Wolf " =~ /[\s]/   # Returns 4
"Wolf " =~ /[\S]/   # Returns 0
```

We can obviously add lots and lots of things between those square brackets. But there are other ways we can do this as well. We can use `()` and `|` to check for multiple things.

```ruby
"Jane" =~ /(Jane|Serge)/    # Returns 0
"Serge" =~ /(Jane|Serge)/   # Returns 0
```

The round brackets are metacharacters in Regexp as well! They are a way to say this or this \(or this or this or this\). The pipe is the delimiter for saying "or".

There are a lot more metacharacters. The `.`, for example, is a wildcard, it will match anything.

```ruby
"jane" =~ /.ane/            # Returns 0
"zane" =~ /.ane/            # Returns 0
"Serge and Jane" =~ /.ane/  # Returns 10
```

This is still relatively hardcoded though, we need to specify where the characters are and what they are. To help solve this problem, there are quantifiers.

#### _Quantifiers_ <a id="quantifiers"></a>

Quantifiers are a way to check in Regexp whether things exist, or exist more than once etc.

The ones that you will actually use:

* `+` means one or more
* `?` means one or zero
* `*` means zero or more

It can look like the following:

```ruby
"Hi there" =~ /i+/      # Returns 1
"Hi there" =~ /the?/    # Returns 3
"Hi theeere" =~ /the*/  # Returns 3
```

These are regularly used for existence checks.

#### _Capturers_ <a id="capturers"></a>

These are difficult to understand. Basically, you match something in parentheses and can refer back to them. You capture something by using round brackets, and refer back to them using a `\` and an integer \(that mimics the order of capture\).

```ruby
"WolfWolf" =~ /(....)\1/
# Matches any four characters, but then needs to have the same four characters straight after.  This returns zero.
​
"ArcticWolf ArcticWolf" =~ /(......)(....) \1\2/
# Matches "Arctic" in the first brackets, then "Wolf" in the second brackets.  "Arctic" is saved as \1 and "Wolf" is saved as \2
```

#### _Regex Cheatsheet_ <a id="regex-cheatsheet"></a>

* ​[Cheatsheet](https://www.ralfebert.de/snippets/ruby-rails/regex_cheat_sheet/)​

