---
layout: post
title: Using rawgit cdn on github repository
---

When our public repository is not popular enough to be hosted on any CDN service,
we can still reference to github url not needed to host it privately on the server get it locally
on the server and having CDN benifit as usual (performance, bandwidth...)

## Why not using directly the Raw GitHub url?

Use web browser we can view raw content of a css/js file on github directly, such as [this][1] but
content type of the response stream is always `text/plan`, not `text/css`, then this file is not understandable
as our expected.

![_config.yml]({{ site.baseurl }}/images/posts/rawgit/github-view-css-content-type.png)

## Use rawgit

Simply take a github url and go to [rawgit.com][3] and paste to its input. You get it then.

![_config.yml]({{ site.baseurl }}/images/posts/rawgit/cssbox.png)

Rawgit uses MaxCDN behind but it [does not guarantee][4] to be 100% up ;)

## References
1. [rawgit faq] (https://rawgit.com/faq)

[1]: https://raw.githubusercontent.com/netvietdev/cssbox/dict/v1.0/cssbox.min.css
[2]: https://rawgit.com/faq
[3]: http://rawgit.com
[4]: https://rawgit.com/faq#no-uptime-guarantee