---
layout: post
title: Xóa files / folders trên windows một cách nhanh nhất
modified: 20150803
---

Trong trường hợp cần xóa nhiều folder theo một pattern nào đó, với cấu trúc folder phức tạp,
có thể dùng cách sau để xóa nhanh.

```
D:\Build>for /d /r . %d in (bin\release) do @if exist "%d" rd /s/q "%d"
```

- Tham số `bin\release` : pattern của thư mục cần xóa.

- Dấu `.` sau `/d /r` : thư mục hiện tại.

## *References*

1. [A question on SO](http://stackoverflow.com/questions/521382/command-line-tool-to-delete-folder-with-a-specified-name-recursively-in-windows)
