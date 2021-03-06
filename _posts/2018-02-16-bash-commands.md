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
Get sum of columns from command
`<cmd> | paste -sd+ - | bc`

Get sum of columns in a file
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

#### Get high response time in access log
`awk '{print $NF,$0}' <file> | sort -rn | head`

#### Replace string
`echo "Replace abc with xyz" | tr abc xyz`

#### Gobal search and replace in VI
`:%s/search_string/replacement_string/g`

#### VI remove duplicate lines in file
`:sort u`
