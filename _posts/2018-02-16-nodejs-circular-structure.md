---
layout: post
title:  "TypeError: Converting circular structure to JSON"
excerpt: "Loop through the object and print the unique keys, its that simple"
date:   2018-02-16
tags: [coding, nodejs]
categories: coding
comments: true
---
This is the solution which I used, simple and works. But there are more solutions from where I "borrowed" the snippet.([Original post](https://stackoverflow.com/questions/11616630/json-stringify-avoid-typeerror-converting-circular-structure-to-json))

{% highlight css %}
 const customStringify = function (v) {
   const cache = new Map();
   return JSON.stringify(v, function (key, value) {
     if (typeof value === 'object' && value !== null) {
       if (cache.get(value)) {
         // Circular reference found, discard key
         return;
       }
       // Store value in our collection
       cache.set(value, true);
     }
     return value;
   });
 };
{% endhighlight %}