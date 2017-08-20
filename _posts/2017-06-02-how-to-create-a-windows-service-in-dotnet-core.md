---
layout: post
title: How to create a windows service in dotnet core
---

A couple of weeks ago, we started a new project which is to consume messages from EventHub in Microsoft Azure, process these messages, and store extracted data into our database in Aliyun. Since our team was considering the possibility of using dotnet core to make our apps capable of running on multiple platforms at the time, we decided to take a dive. However, while everything seemed ready, we still had a few troubles to overcome, which include this one: how to run a dotnet core console app as a windows service?

OK, here comes the answer: bridging and wrapping.

Bridging seems more popular. The representatives are these two libraries: [DotNetCore.WindowsService](https://github.com/PeterKottas/DotNetCore.WindowsService) and 
[DasMulli.Win32.ServiceUtils](https://github.com/dasMulli/dotnet-win32-service). They basically adapt windows service facilities for dotnet core, and everything works just like what you do in .Net framework.

Wrapping is less common but more delicate. In this way, you can wrap a dotnet standard library in a windows service that runs on .Net Framework. [This article](https://stackify.com/creating-net-core-windows-services/) introduces details about this method. What you need to pay attention to is the compatibility of dotnet standard versions (see the compatibility table [here](https://github.com/dotnet/standard/blob/master/docs/versions.md)). I have also written a simple app to exemplify this method, you can see it [here]().

Is that done? Definitely not. The question is actually invalid after scrutiny: as long as you can run an app in the background and somebody can manage its life cycle, why do you need a windows service? The reason why this question came up is that we are still deep in the sea of Windows.

So, although the previous two methods are awesome, my preferred answer is docker. You can put your long-run dotnet core app into a docker image and let the docker engine manage everything. Now, welcome to the ocean of Linux.