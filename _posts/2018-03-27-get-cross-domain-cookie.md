---
layout: post
title:  "Share cookie across domains"
excerpt: "Get example.com's cookie while me.com is loaded"
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
Cookie cannot be sent from one domain to another, even on sub domains there are restrictions ([read here to get around sub domain](/articles/2018-02/share-session-across-subdomains)). The cookie can only be read by the domain which has set it, this to avoid man-in-the-middle attack where hackers steal your cookie and hacks you account. Thats the reason `client.com` needs to call `vendor.com` from the browser. But calling javascript/resource request to another domain is not allowed by the browser due to same-origin policy. This policy is needed as rouge sites which you open in your browser otherwise will be able to issue API request to site like `gmail.com` or `facebook.com` to which your are already logged in, these request will go through due to precense of the cookie in the browser.
To get around same-origin policy we have to use (CORS)[https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS], which is relaxation of this security. Following CORS rules  you make changes in the server of `vendor.com` to send header stating `client.com` is allowed to use the resource (Access-Control-Allow-Origin header). By using this cross domain request is allowed but this will not send the cookie, to send the cookie we need to allow the credentials (Access-Control-Allow-Credentials), by setting the header in the server and using `withCredentials` as part of the request.
Simple isn't it :)
