---
layout: post
title:  "Share cookie across domains"
excerpt: "Get vendor.com's cookie while client.com is loaded"
date:   2018-03-27
tags: [coding, javascript, cors]
categories: coding
comments: true
---
#### Problem
One of my client wanted to validate the user form our system to treat them differently. There are a few ways to do that involving both server and client side changes. But in this we didn't want to involve server side changes.

#### Code and Solution
Say cilent site is `client.com` and mine is `vendor.com`, here is what needed to be done:
1. Create a file in `vendor.com` to return cookies or response based on cookie. In the following PHP example I am returning the whole cookie (not advisible)
{% highlight css %}
<?php
echo json_encode($_COOKIE);
{% endhighlight %}
2. Have a url for this file/code e.g. http://vendor.com/getcookie.php
3. Call this url from `client.com` page, as JSON request, call this url with `withCredentials` set to true, else cookie won't be sent ([code reference](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/withCredentials))
4. Capture the response and do the needful
5. Remember to make way for CROS ([read more](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS))
6. Set these headers in `vendor.com`
{% highlight css %}
Header set Access-Control-Allow-Origin "http://client.com"
Header set Access-Control-Allow-Credentials: true
{% endhighlight %}

#### Explanation
There are three security features we have to get around: 
1. Cookie cannot be read by any domain other than one which has set it
2. Allow request to different domain than the origin site
3. Send cookie as part of this request

1. Cookie in the web world is like gold, because if it leaks people can lose money, this is known has session hijacking. Session hijacking or cookie hijacking is where hacker steals your cookie and then can do actions on the website on your behalf. Example if your `gmail.com` cookie is hijacked then hacker can delete all your mails! Hence reputed browsers secures cookie by restricting who reads and writes it, even sub domains are restricted to use cookie set by main domain ([read here to get around sub domain](/articles/2018-02/share-session-across-subdomains)). That’s the reason `client.com` needs to call `vendor.com` from the browser, so `vendor.com` will read the cookie and reply back appropriate response.

2. Loading of javascript from different domain than one is loaded is restricted (same-origin policy) as otherwise rouge sites or scripts, which you might launch in your browser, which would issue API request to site like `gmail.com` or `twitter.com` or any other site to which you are already logged in. These malevolent requests will go through due to presence of the cookie in the browser. To get past this we have to make change in the server to pass the header stating `client.com` can call API to `vendor.com`, hence using *Access-Control-Allow-Origin*. This is part of CORS[https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS], which is relaxation of this security.

3. Even after using *Access-Control-Allow-Origin*, cookie will not be passed as part of header of API call, that due to again, you guess it *Security!!*. To enable that we add another header in the response from server which is *Access-Control-Allow-Credentials*, apart from server change we would need change the JSON request (using `withCredentials`) to tell browser to send cookie as part of the request.

There you have it, get cookie from different domain than the one that is loaded in browser. Simple isn't it :)