---
layout: post
title: Processing Markdown markup language on the server side with .NET
---



The WYSIWYG is very common and many websites support this feature. It often encodes user input into HTML format.
There is another option using [Markdown][1] markup language. This post will explain in detail how to make it work
and a custom JQuery plugin wrapps [showdownjs][2].

## 1. CommonMark.NET

[This is the repository][1]. It implements [CommonMark specification][2] and having some performance comparison.
After doing some tests, there is one case not working: it doesn't understand header markup if it is not having a space
before any viewable character.

```
"##This is a header" will not be understanding, but "## This is a header" is.
```


[1]: https://github.com/Knagis/CommonMark.NET/
[2]: http://spec.commonmark.org/
