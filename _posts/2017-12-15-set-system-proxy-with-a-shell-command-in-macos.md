---
layout: post
title: Set system proxy with a shell script in MacOS
---

Have you experienced setting a proxy in your MacOS? If you have, you must be fairly clear about how painful it is. You must 

1. Open "System Preference",
2. Find "Network", 
3. Find the right network interface, click on it, 
4. Click "Advanced.." in the right panel,
5. Switch to "Proxies" tab,
6. Check the desired proxies,
7. Enter the proxy IP address and port,
8. Click "OK",
9. Click "Apply", 

and finally, if you are still alive, the task is done.

But, if you are a coder, please do not do that for our title's sake - you can save a ton of time with the ```networksetup``` command. Among a variety of the supported operations on its [manual page](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man8/networksetup.8.html), ```-setwebproxy``` option is for this case.

```
networksetup [-setwebproxy networkservice domain portnumber authenticated username password]
```

So, with the following script added in your ```$PATH```, you can simply set the system proxy by typing the script's name and press enter in your favorite bash interface.

```
host=10.0.0.10
port=80
networksetup -setwebproxy Wi-Fi $host $port off
networksetup -setsecurewebproxy Wi-Fi $host $port off
```

🚀🚀🚀🚀🚀


What? You want to turn the proxy off and on in this way? Dig into the manual and see if it bites. 🍺
