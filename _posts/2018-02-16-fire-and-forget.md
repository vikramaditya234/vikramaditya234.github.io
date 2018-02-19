---
layout: post
title:  "Fire and forget"
excerpt: "You don't always wait for response, it's sockets not curl"
date:   2018-02-16
tags: [coding, php]
categories: coding
comments: true
---
#### Problem
You have an event in a server that you want to send to other, but don't want to wait for its response.
Fire and forget

#### Code and Solution
Socket is your friend, here is how I did it

{% highlight css %}
    $parts = parse_url($remote_url);
    $fp = fsockopen($parts['host'], 80, $errno, $errstr, 30);

    if ( ! $fp) {
        error_log('ERROR in fire and forget: ('.$errno.') '.$errstr);
    }
    $path = $parts['path']."?".$parts['query'];
    $out = "GET ".$path." HTTP/1.1\r\n";
    $out.= "Host: ".$parts['host']."\r\n";
    $out.= "Connection: Close\r\n\r\n";
    fwrite($fp, $out);
    fclose($fp);
{% endhighlight %}

Read more about [fsockopen](http://php.net/manual/en/function.session-set-cookie-params.php)

#### Explanation
Ok this is a cheat. HTTP uses TCP for communication and as we all know (or will know now), once client intiates the connection it keeps the connection open till response is received or timeout. What this means is that its not actually a fire and forget, but as far as PHP is concerned thats done and it carry on executing next statment without waiting for response.
