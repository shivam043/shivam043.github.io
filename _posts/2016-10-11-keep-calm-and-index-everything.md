---
layout: post
title: Security Research Work for Directi
---

This post is regarding critical vulnerability i found on directi's codechef.com


##Proof of Concept

I started digging using burpsuite for session mishandling and idor but found nothing.
On going deeper using a Google Dork (Advanced Search Technique on Google) site:www.codechef.com inurl:”php”
Executing the dork above on Google gives me these results:
![A Screenshot of the google dork]({{ site.url }}/public/blog/bruteforce-cyberoam-shell.png)

So, I got 3 results with same URL Scheme
www.codechef.com/download.php?file=[vulnerable]
I figured out that the “file” parameter is the File Name which got downloaded automatically. So, It quickly reminds me that this kind of URL Scheme is possibly vulnerable to Directory Traversal. 
![A Screenshot of the local file dowbload]({{ site.url }}/public/blog/bruteforce-cyberoam-shell.png)

After browsing the URL above, something popped out and asked me to download a file and here’s the content of the file I have downloaded.
![A Screenshot of the etc file which i have downloaded]({{ site.url }}/public/blog/bruteforce-cyberoam-shell.png)

I also viewed etc/profile ,etc/services,server configuration file,php configuration file and many others files like backup files which contain sensitive data.
![Here’s downloaded files(It is possible to download more system files)]({{ site.url }}/public/blog/bruteforce-cyberoam-shell.png)

Some points:
. Php version and server version were exposed in headers,attackers can take benefit from this information. 
Server version-
({{ site.url }}/public/blog/bruteforce-cyberoam-shell.png)



