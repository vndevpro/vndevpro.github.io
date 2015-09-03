---
layout: post
title: Creating cache services instead of providers
---

The *Provider Model* is common in .NET Framework as we might know some like RoleProvider, ProfileProvider,
MembershipProvider and so on. I want have something similar for *cache*, my application can switch
to a different cache system just by changing some configuration element. So Provider Model seems a good approach to follow.

Reading more on some articles from active guys [Provider is not a pattern][1], [PROVIDER MODEL IS A SOLID PATTERN][2],
[The Provider Model Pattern, Really][3]... I have my own choosen

## 1. A simple Cache Service interface

        T Get<T>(string key) where T : class;
        
        bool Set<T>(string key, T value) where T : class;
        bool Set<T>(string key, T value, TimeSpan expiry) where T : class;

        bool Remove(string key);

## 2. An InMemoryCache implementation

This implementor uses the system MemoryCache, it is an Adapter to MemoryCache

## 3. A RedisCache implementation

This service uses [Redis Client][5] to perform connection to Redis server and the serialization methods
from [SerializationMaster][4] to serialize/deserialize string to object of any type.

![_config.yml]({{ site.baseurl }}/images/redis/redis-cache.jpg)

[1]: http://blog.ploeh.dk/2011/04/27/Providerisnotapattern/
[2]: http://candordeveloper.com/2012/06/26/provider-model-is-a-solid-pattern/
[3]: http://www.codethinked.com/the-provider-model-pattern-really
[4]: https://www.nuget.org/packages/Rabbit.SerializationMaster
[5]: https://www.nuget.org/packages/StackExchange.Redis