---
layout: post
title: EntityFramework - deploy custom stored procedures to Azure
---

Continuing on my [previous post regarding EF-Azure][1] for project [IOnline][2], I need to adapt
this requirement to: (1) Not using EF to count number of messages (total messages in the system and by categories)
and (2) Use [Dapper][3] for the data access layer. So I will have to create some stored procedures
to make this works.

1. ## Create stored procedures and references to Dapper

2. ## Enable migration


## References

[1]: ![_config.yml]({{ site.baseurl }}/2015-8-30-EntityFramework-code-first-automatic-migration-azure.md)
[2]: https://github.com/juanonsoftware/ionline
[3]: https://github.com/StackExchange/dapper-dot-net