---
layout: post
title: Aliyun MNS dotnet core SDK
---

It is known that Aliyun has a really bad support for .Net world. Every one of its products and services has a well built Java SDK, but not everyone has a .Net one. Even if some of them do provide .Net SDK, some do not provide full functionality, some do not work in a .Net way and some are buggy and lack of maintenance. Even today, after .Net core has been released for over two years, there is not one product or service officially provides .Net core SDK. This is really bad, especially for .Net prospectors like me.

So, I decided to invent the wheel for those who share the same pain. [mns-netcore](https://github.com/aries-zhang/mns-netcore) is then created and open sourced. It now fully supports all [Aliyun MNS](https://www.aliyun.com/product/mns)' queue operations and still in optimization. This lib is a .Net standard library, which means it works both in .Net Framework and .Net core. To use it, you can reference from [Nuget](https://www.nuget.org/packages/mns-netcore/), and meanwhile, you are welcome to raise an issue or contribute by sending pull requests.

In its README, there is detailed specification about how to send and subscribe messages. Finally, please feel free to ask any questions about it on GitHub issues.