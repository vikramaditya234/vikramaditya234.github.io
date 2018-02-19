---
layout: post
title:  "Convert string to buffer and back"
excerpt: "String to buffer to simple but getting back can be tricky"
date:   2018-02-16
tags: [coding, nodejs]
categories: coding
comments: true
---
#### Converting string to buffer
Look how easy, look ma no hands :)

`var buf = Buffer.from(bufStr, 'utf8');` 

#### Converting buffer to string
This can be tricky as in this case we get part of buffer (chunks) at a time and these chunks needed to be joined togather to get the whole string

*Shamelessly copied from [here](https://stackoverflow.com/questions/12121775/convert-streamed-buffers-to-utf8-string)*

###### Single buffer
{% highlight css %}
var req = http.request(reqOptions, function(res) {
    res.on('data', function(chunk) {
        var textChunk = chunk.toString('utf8');
        // process utf8 text chunk
    });
})
{% endhighlight %}

###### Streamed buffers
{% highlight css %}
var StringDecoder = require('string_decoder').StringDecoder;

var req = http.request(reqOptions, function(res) {
    var decoder = new StringDecoder('utf8');

    res.on('data', function(chunk) {
        var textChunk = decoder.write(chunk);
        // process utf8 text chunk
    });
});
{% endhighlight %}

#### Explaination
I am not copying the explaination. Please go the [stackoverflow link](https://stackoverflow.com/questions/12121775/convert-streamed-buffers-to-utf8-string) and while you are there upvote the answer too :)