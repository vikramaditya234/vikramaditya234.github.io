---
layout: post
title:  "Redirect to HTTP to HTTPS in apache"
excerpt: "Simple redirection based on condition"
date:   2018-02-21
tags: [coding, apache]
categories: coding
comments: true
---
#### Problem
You have SSL certificate installed on the server and now want to redirect all the HTTP traffic to HTTPS

#### Code and Solution
Here is simple configuration that you can add in apache configuration. If you are using *virtualhost* add this within it

{% highlight css %}
  <IfModule mod_setenvif.c>
    SetEnvIf X-Forwarded-Proto "^https$" HTTPS
  </IfModule>

  RewriteEngine On
  RewriteCond %{HTTP:X-Forwarded-Proto} =http
  RewriteCond  %{REQUEST_URI} !^/sample(.*)$
  RewriteRule . https://%{HTTP:Host}%{REQUEST_URI} [L,R=permanent]
{% endhighlight %}

Read more about [rewrite](https://httpd.apache.org/docs/2.0/misc/rewriteguide.html)
