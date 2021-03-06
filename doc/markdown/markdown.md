# Markdown

## Table of Contents

**[GitLab Flavored Markdown](#gitlab-flavored-markdown-gfm)**

* [Newlines](#newlines)
* [Multiple underscores in words](#multiple-underscores-in-words)
* [URL auto-linking](#url-auto-linking)
* [Code and Syntax Highlighting](#code-and-syntax-highlighting)
* [Emoji](#emoji)
* [Special GitLab references](#special-gitlab-references)
* [Task lists](#task-lists)

**[Standard Markdown](#standard-markdown)**

* [Headers](#headers)
* [Emphasis](#emphasis)
* [Lists](#lists)
* [Links](#links)
* [Images](#images)
* [Blockquotes](#blockquotes)
* [Inline HTML](#inline-html)
* [Horizontal Rule](#horizontal-rule)
* [Line Breaks](#line-breaks)
* [Tables](#tables)

**[References](#references)**

## GitLab Flavored Markdown (GFM)

For GitLab we developed something we call "GitLab Flavored Markdown" (GFM). It extends the standard Markdown in a few significant ways to add some useful functionality.

You can use GFM in

- commit messages
- comments
- issues
- merge requests
- milestones
- wiki pages

You can also use other rich text files in GitLab. You might have to install a dependency to do so. Please see the [github-markup gem readme](https://github.com/gitlabhq/markup#markups) for more information.

## Newlines

GFM honors the markdown specification in how [paragraphs and line breaks are handled](http://daringfireball.net/projects/markdown/syntax#p).

A paragraph is simply one or more consecutive lines of text, separated by one or more blank lines.  
Line-breaks, or softreturns, are rendered if you end a line with two or more spaces

    Roses are red [followed by two or more spaces]  
    Violets are blue

    Sugar is sweet

Roses are red  
Violets are blue

Sugar is sweet

## Multiple underscores in words

It is not reasonable to italicize just _part_ of a word, especially when you're dealing with code and names that often appear with multiple underscores. Therefore, GFM ignores multiple underscores in words.

    perform_complicated_task
    do_this_and_do_that_and_another_thing

perform_complicated_task
do_this_and_do_that_and_another_thing

## URL auto-linking

GFM will autolink standard URLs you copy and paste into your text. So if you want to link to a URL (instead of a textural link), you can simply put the URL in verbatim and it will be turned into a link to that URL.

    http://www.google.com

http://www.google.com

## Code and Syntax Highlighting

Blocks of code are either fenced by lines with three back-ticks <code>```</code>, or are indented with four spaces. Only the fenced code blocks support syntax highlighting.

```no-highlight
Inline `code` has `back-ticks around` it.
```

Inline `code` has `back-ticks around` it.

Example:

    ```javascript
    var s = "JavaScript syntax highlighting";
    alert(s);
    ```

    ```python
    def function():
        #indenting works just fine in the fenced code block
        s = "Python syntax highlighting"
        print s
    ```

    ```ruby
    require 'redcarpet'
    markdown = Redcarpet.new("Hello World!")
    puts markdown.to_html
    ```

    ```
    No language indicated, so no syntax highlighting.
    s = "There is no highlighting for this."
    But let's throw in a <b>tag</b>.
    ```

becomes:

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

```python
def function():
    #indenting works just fine in the fenced code block
    s = "Python syntax highlighting"
    print s
```

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

```
No language indicated, so no syntax highlighting.
s = "There is no highlighting for this."
But let's throw in a <b>tag</b>.
```

## Emoji

	Sometimes you want to :monkey: around a bit and add some :star2: to your :speech_balloon:. Well we have a gift for you:

	:zap: You can use emoji anywhere GFM is supported. :v:

	You can use it to point out a :bug: or warn about :speak_no_evil: patches. And if someone improves your really :snail: code, send them some :birthday:. People will :heart: you for that.

	If you are new to this, don't be :fearful:. You can easily join the emoji :family:. All you need to do is to look up on the supported codes.

	Consult the [Emoji Cheat Sheet](http://emoji.codes) for a list of all supported emoji codes. :thumbsup:

Sometimes you want to :monkey: around a bit and add some :star2: to your :speech_balloon:. Well we have a gift for you:

:zap: You can use emoji anywhere GFM is supported. :v:

You can use it to point out a :bug: or warn about :speak_no_evil: patches. And if someone improves your really :snail: code, send them some :birthday:. People will :heart: you for that.

If you are new to this, don't be :fearful:. You can easily join the emoji :family:. All you need to do is to look up on the supported codes.

Consult the [Emoji Cheat Sheet](http://emoji.codes) for a list of all supported emoji codes. :thumbsup:

## Special GitLab References

GFM recognizes special references.

You can easily reference e.g. an issue, a commit, a team member or even the whole team within a project.

GFM will turn that reference into a link so you can navigate between them easily.

GFM will recognize the following:

| input                  | references                 |
|-----------------------:|:---------------------------|
| `@user_name`           | specific user              |
| `@group_name`          | specific group             |
| `@all`                 | entire team                |
| `#123`                 | issue                      |
| `!123`                 | merge request              |
| `$123`                 | snippet                    |
| `~123`                 | label by ID                |
| `~bug`                 | one-word label by name     |
| `~"feature request"`   | multi-word label by name   |
| `9ba12248`             | specific commit            |
| `9ba12248...b19a04f5`  | commit range comparison    |
| `[README](doc/README)` | repository file references |

GFM also recognizes certain cross-project references:

| input                                   | references              |
|----------------------------------------:|:------------------------|
| `namespace/project#123`                 | issue                   |
| `namespace/project!123`                 | merge request           |
| `namespace/project$123`                 | snippet                 |
| `namespace/project@9ba12248`            | specific commit         |
| `namespace/project@9ba12248...b19a04f5` | commit range comparison |

## Task Lists

You can add task lists to merge request and issue descriptions to keep track of to-do items.  To create a task, add an unordered list to the description in an issue or merge request, formatted like so:

```no-highlight
* [x] Completed task
* [ ] Unfinished task
    * [x] Nested task
```

Task lists can only be created in descriptions, not in titles or comments.  Task item state can be managed by editing the description's Markdown or by clicking the rendered checkboxes.

# Standard Markdown

## Headers

```no-highlight
# H1
## H2
### H3
#### H4
##### H5
###### H6

Alternatively, for H1 and H2, an underline-ish style:

Alt-H1
======

Alt-H2
------
```

# H1
## H2
### H3
#### H4
##### H5
###### H6

Alternatively, for H1 and H2, an underline-ish style:

Alt-H1
======

Alt-H2
------

### Header IDs and links

All markdown rendered headers automatically get IDs, except for comments.

On hover a link to those IDs becomes visible to make it easier to copy the link to the header to give it to someone else.

The IDs are generated from the content of the header according to the following rules:

1. remove the heading hashes `#` and process the rest of the line as it would be processed if it were not a header
2. from the result, remove all HTML tags, but keep their inner content
3. convert all characters to lowercase
4. convert all characters except `[a-z0-9_-]` into hyphens `-`
5. transform multiple adjacent hyphens into a single hyphen
6. remove trailing and heading hyphens

For example:

```
###### ..Ab_c-d. e [anchor](URL) ![alt text](URL)..
```

which renders as:

###### ..Ab_c-d. e [anchor](URL) ![alt text](URL)..

will first be converted by step 1) into a string like:

```
..Ab_c-d. e &lt;a href="URL">anchor&lt;/a> &lt;img src="URL" alt="alt text"/>..
```

After removing the tags in step 2) we get:

```
..Ab_c-d. e anchor ..
```

And applying all the other steps gives the id:

```
ab_c-d-e-anchor
```

Note in particular how:

- for markdown anchors `[text](URL)`, only the `text` is used
- markdown images `![alt](URL)` are completely ignored

## Emphasis

```no-highlight
Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~
```

Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~

## Lists

```no-highlight
1. First ordered list item
2. Another item
  * Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
  1. Ordered sub-list
4. And another item.

   Some text that should be aligned with the above item.

* Unordered list can use asterisks
- Or minuses
+ Or pluses
```

1. First ordered list item
2. Another item
  * Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
  1. Ordered sub-list
4. And another item.

   Some text that should be aligned with the above item.

* Unordered list can use asterisks
- Or minuses
+ Or pluses

## Links

There are two ways to create links, inline-style and reference-style.

    [I'm an inline-style link](https://www.google.com)

    [I'm a reference-style link][Arbitrary case-insensitive reference text]

    [I'm a relative reference to a repository file](LICENSE)

    [You can use numbers for reference-style link definitions][1]

    Or leave it empty and use the [link text itself][]

    Some text to show that the reference links can follow later.

    [arbitrary case-insensitive reference text]: https://www.mozilla.org
    [1]: http://slashdot.org
    [link text itself]: http://www.reddit.com

[I'm an inline-style link](https://www.google.com)

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself][]

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com

**Note**

Relative links do not allow referencing project files in a wiki page or wiki page in a project file. The reason for this is that, in GitLab, wiki is always a separate git repository. For example:

`[I'm a reference-style link][style]`

will point the link to `wikis/style` when the link is inside of a wiki markdown file.

## Images

    Here's our logo (hover to see the title text):

    Inline-style:
    ![alt text](assets/logo-white.png)

    Reference-style:
    ![alt text1][logo]

    [logo]: assets/logo-white.png

Here's our logo:

Inline-style:

![alt text](/assets/logo-white.png)

Reference-style:

![alt text][logo]

[logo]: /assets/logo-white.png

## Blockquotes

```no-highlight
> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.
```

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.

## Inline HTML

You can also use raw HTML in your Markdown, and it'll mostly work pretty well.

See the documentation for HTML::Pipeline's [SanitizationFilter](http://www.rubydoc.info/gems/html-pipeline/HTML/Pipeline/SanitizationFilter#WHITELIST-constant) class for the list of allowed HTML tags and attributes.  In addition to the default `SanitizationFilter` whitelist, GitLab allows the `class`, `id`, and `style` attributes.

```no-highlight
<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>
```

<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>

## Horizontal Rule

```
Three or more...

---

Hyphens

***

Asterisks

___

Underscores
```

Three or more...

---

Hyphens

***

Asterisks

___

Underscores

## Line Breaks

My basic recommendation for learning how line breaks work is to experiment and discover -- hit &lt;Enter&gt; once (i.e., insert one newline), then hit it twice (i.e., insert two newlines), see what happens. You'll soon learn to get what you want. "Markdown Toggle" is your friend.

Here are some things to try out:

```
Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a *separate paragraph*.

This line is also a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the *same paragraph*.

This line is also a separate paragraph, and...  
This line is on its own line, because the previous line ends with two
spaces.
```

Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a *separate paragraph*.

This line is also begins a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the *same paragraph*.

This line is also a separate paragraph, and...  
This line is on its own line, because the previous line ends with two
spaces.

## Tables

Tables aren't part of the core Markdown spec, but they are part of GFM and Markdown Here supports them.

```
| header 1 | header 2 |
| -------- | -------- |
| cell 1   | cell 2   |
| cell 3   | cell 4   |
```

Code above produces next output:

| header 1 | header 2 |
| -------- | -------- |
| cell 1   | cell 2   |
| cell 3   | cell 4   |

**Note**

The row of dashes between the table header and body must have at least three dashes in each column.

## References

- This document leveraged heavily from the [Markdown-Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).
- The [Markdown Syntax Guide](http://daringfireball.net/projects/markdown/syntax) at Daring Fireball is an excellent resource for a detailed explanation of standard markdown.
- [Dillinger.io](http://dillinger.io) is a handy tool for testing standard markdown.
