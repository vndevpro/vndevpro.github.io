---
layout: post
title: Processing Markdown on the server side with .NET
---



## 1. CommonMark.NET

[This is the repository][1]. It implements [CommonMark specification][2] and having some performance comparison.
After doing some tests, there is one case not working: it doesn't understand header markup if it is not having a space
before any viewable character.

```
"##This is a header" will not be understanding

but "## This is a header" is.
```

## 2. MarkdownDeep
[This is the repository][4]. It has both JavaScript and .NET versions so we can use on both Browser ([editor demo here][5]) and the server side.

The above failing case is not happen in MarkdownDeep.

## 3. ServiceStack

In `ServiceStack.Text.dll, v4.0.40.0` there is an extension method of `string` to strip all Markdown markup
and return plain text.

```
var plainText = body.StripMarkdownMarkup();
```

When you want to get a substring of the text from markdown source, this is very useful because formatting characters
should not be included in the result.


[1]: https://github.com/Knagis/CommonMark.NET/
[2]: http://spec.commonmark.org/
[3]: http://www.toptensoftware.com/markdowndeep/
[4]: https://github.com/toptensoftware/MarkdownDeep
[5]: http://www.toptensoftware.com/markdowndeep/dingus