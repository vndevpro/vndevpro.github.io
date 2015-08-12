---
layout: post
title: Tại sao nên sử dụng CDN?
modified: 20150806
---

Tăng tốc độ load của page, giảm tải & băng thông cho server, giảm số concurrent reuqests đến server
là một số benifits của việc dùng CDN cho script, css, image...

##Lợi ích khi sử dụng CDN

- Tăng tốc độ load của page, vì CDN được sử dụng bởi nhiều website nên có thể browser đã cache file
và không phải tải lại.
- Giảm tải & băng thông cho server của ứng dụng.
- Giảm số concurrent reuqests đến server, trình duyệt giới hạn số kết nối đồng thời đến một hostname
là 6 hoặc 7, request khác được xử lý nhanh hơn.

##Coding với ASP.NET MVC

Khi add thêm một bundle, thêm url của CDN và ASP.NET Bundle sẽ sử dụng url này để reference khi
website được config sang chế độ production (

![_config.yml]({{ site.baseurl }}/images/posts/cdn-code-01.png)

![_config.yml]({{ site.baseurl }}/images/posts/cdn-code-02.png)

## References
1. http://www.asp.net/ajax/cdn
2. http://www.dotnetjalps.com/2014/07/cdn-in-aspnet-mvc-bundling.html
3. http://www.hanselman.com/blog/CDNsFailButYourScriptsDontHaveToFallbackFromCDNToLocalJQuery.aspx