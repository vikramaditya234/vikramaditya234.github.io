---
layout: post
title:  "Bash commands"
excerpt: "Some commands that I looked for"
date:   2018-02-16
tags: [coding, bash]
categories: coding
comments: true
---
#### Dump HTTP header
Dump the http header with no care for the body
Using `wget` this will also download the content: 
> $ wget --server-response http://www.example.com/ 

Using `curl`
> $ curl -I http://www.example.com/

#### Sum of columns 
Get sum of columns in file or from command
`<cmd> | paste -sd+ - | bc`
`paste -sd <file> | bc` 

#### Get column from input (split by delimiter) 
`<cmd> | cut -d' ' -f14` (' ' as delimiter picking text at 14th position) 

#### Get character at position from input 
`<cmd> | cut -d2` (get character at 2 position)

#### Count word, character and lines 
`wc ` 

#### Delete blank lines in vi
`:g/^$/d`

#### Update time in ubuntu
*this can mess up SSL certs because they can be future dated*
`ntpdate ntp.ubuntu.com`