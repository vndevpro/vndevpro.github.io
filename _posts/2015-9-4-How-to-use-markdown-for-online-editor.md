---
layout: post
title: How to use Markdown on browser
---

The WYSIWYG is very common and many websites support this feature. It often encodes user input into HTML format.
There is another option using [Markdown][1] markup language. This post will explain in detail how to make it work
and a custom JQuery plugin wrapps [showdownjs][2].

## 1. Add showdown to your side

On development machine, you can go to [showndown repository][3] and take the release, or [this cdn][4] for production.

This is an ASP.NET bundle

![_config.yml]({{ site.baseurl }}/images/posts/markdown/showdown-bundle.jpg)

## 2. Using the plugin

If your side use JQuery, this plugin [JQuery Showdown Preview][5] is a good option to start with.

![_config.yml]({{ site.baseurl }}/images/posts/markdown/showdown-preview.png)

The plugin accepts an option with parameters at version 1.0

- source: the source element selector, any element containing markdown text
- defaultMessage: when the source element is nothing, this text will be shown. It accepts markdown syntax

## 3. And a result
![_config.yml]({{ site.baseurl }}/images/posts/markdown/markdown-preview.png)

[1]: https://en.wikipedia.org/wiki/Markdown
[2]: http://showdownjs.github.io/demo/
[3]: https://github.com/showdownjs/showdown/tree/master/dist
[4]: https://cdnjs.com/libraries/showdown
[5]: https://github.com/netvietdev/showdown-preview