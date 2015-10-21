---
layout: post
title: Ngăn chặn XSS trong ASP.NET
modified: 20150806
---

Làm thế nào để ngăn chặn XSS attack trong ứng dụng trên nền tảng ASP.NET ?
ASP.NET cung cấp sẵn những khả năng này và chúng ta có thể tùy biến nó theo yêu cầu của ứng dụng.
Bài viết này giới thiệu các steps đảm bảo input từ người dùng là an toàn cho ứng dụng.

## Giao diện nhập cơ bản

Trong form này có 2 trường cơ bản, một trường `Message` cho phép nhập freetext, và một trường số.
Khi `Message` không chứa mã HTML, form như sau:

![_config.yml]({{ site.baseurl }}/images/posts/xss/normal-input.png)

## Nhập Message có mã HTML

Giả sử yêu cầu của ứng dụng là cho phép user nhập "rich text", ví dụ:

![_config.yml]({{ site.baseurl }}/images/posts/xss/html-input-allowhtml.png)

ASP.NET kiểm tra dữ nhiệu submit lên server và blocks request

![_config.yml]({{ site.baseurl }}/images/posts/xss/html-submit-exception.png)

## Tùy biến để cho phép server chấp nhận rich text HTML

Có 2 lựa chọn cho phép làm việc này: sử dụng attribute `AllowHtml` hoặc `ValidationInput`,
nhưng lựa chọn #2 sẽ turn-off validation trên server. Vì vậy nên lựa chọn `AllowHtml` trong nhiều trường hợp có hiệu quả hơn.
[(xem thay đổi)][7]

```
[AllowHtml]
public string Message { get; set; }
```

Kết quả sẽ là

![_config.yml]({{ site.baseurl }}/images/posts/xss/html-input-allowhtml.png)

## Khả năng bị tấn công XSS

Việc cho phép mã JavaScript được nhập vào ứng dụng có nguy cơ bị tấn công XSS.

Trên Chrome V45, trình duyệt hiểu và ngăn chặn được nguy cơ này.

![_config.yml]({{ site.baseurl }}/images/posts/xss/chrome(version45)-protect-us.png)

Nhưng trên các trình duyệt khác thì không. Hơn nữa ứng dụng phía server cần xử lý được rủi ro này

![_config.yml]({{ site.baseurl }}/images/posts/xss/firefox-doesnt-protect-us.png)

## Xử lý trên server

### Solution 1

Việc xử lý thực hiện trên từng trường dữ liệu có nguy cơ bị XSS

1. Cài Package [AntiXSS][5] vào ứng dụng

2. Gọi function xử lý trường nhập dữ liệu chứa mã HTML, các thẻ HTML không an toàn sẽ bị loại bỏ. [(xem thay đổi)][6]

```
var safeHtml = Sanitizer.GetSafeHtmlFragment(item.Message);
```

![_config.yml]({{ site.baseurl }}/images/posts/xss/safe-html.png)

### Solution 2

Xử lý một cách tự động thông qua một ModelBinder

1. Cài package [RabbitWebMvc][8] vào ứng dụng

2. Sử dụng `DefaultBinder` là `SafeHtmlModelBinder`

```
ModelBinders.Binders.DefaultBinder = new SafeHtmlModelBinder();
```

## References

- [Preventing XSS in ASP.NET Made Easy][1]
- [OWASP AntiSamy Project .NET][4]


[1]: http://lockmedown.com/preventing-xss-in-asp-net-made-easy/
[2]: https://msdn.microsoft.com/en-us/library/system.web.util.httpencoder(v=vs.110).aspx
[3]: https://msdn.microsoft.com/en-us/library/system.web.security.antixss.antixssencoder.htmlattributeencode(v=vs.110).aspx
[4]: https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project_.NET
[5]: https://www.nuget.org/packages/AntiXss/
[6]: https://github.com/vndevpro/mvc-xss/commit/170d81324b46e47ca3d67852060d40396716ebf0?diff=unified
[7]: https://github.com/vndevpro/mvc-xss/commit/fa82bf31ddcc8c9fd4d12d7d026177f6a1fe759e
[8]: https://www.nuget.org/packages/RabbitWebMvc/