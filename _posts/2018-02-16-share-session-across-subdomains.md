---
layout: post
title:  "Share session acorss subdomains"
excerpt: "Set session cookie to .mydomain.com instead of mydomain.com"
date:   2018-02-16
tags: [coding, php]
categories: coding
comments: true
---
#### Problem
We have a bunch of subdomains and we want to share session acorss all of them. Subdomain list:
{% highlight css %}
sub1.mydomain.com
sub2.mydomain.com
sub3.mydomain.com
{% endhighlight %}
#### Code and Solution
Change session cookie to: `.mydomain.com` Done! *Note: `.` in the start of domain*

There are two ways to do this:
1. In php.ini, by changing/adding `session.cookie_domain` to `session.cookie_domain = ".mydomain.com"`
2. If you want to have more control on this, add this in your php file/framework before `session_start()`:
> session_set_cookie_params(0, '/', '.mydomain.com');

Read more about [session_set_cookie_params](http://php.net/manual/en/function.session-set-cookie-params.php)

#### Explanation
PHP will set session cookie for host resulting in multiple session one for each domain/sub-domain. To share session we have to force session cookie to be set for one domain and access by all and that domain in this case will be `.mydomain.com`

Why not to use `mydomain.com`, because when you change session domain to `mydomain.com`, PHP will prefix `.` to domain and you will end up with `.mydomain.com`
