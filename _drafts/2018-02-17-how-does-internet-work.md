---
layout: post
title:  "How does internet work"
excerpt: "Its a web a really big web :)"
date:   2018-02-17
tags: [technology, how does it work]
categories: technology
comments: true
---
You want to go to the site [https://wikipedia.org](https://wikipedia.org), it's simple right? You open the browser, type *wikipedia.org*, press enter and Voila! Page appears like magic. You might not realize but this simple quick magic uses at least a few dozen computers and your request travels half way across the world before it comes back with the page. Let see how this works.

You might already know this, what you experienced with Wikipedia or any other website is the magic of internet. Internet is global network of computer talking to each other, send data, pictures, videos, mails etc. Let's understand what this is and how it works.

Let's take a class of students, sitting in rows and columns. Now if Peter on one side of the classroom wants to say 'Hi' to Jane, he can either yell and risk of getting ignored by humiliated Jane, or can he pass a folded letter, packed in a envelope. The envelope is passed by the students, each of whom knows where it needs to go. When Jane receives the envelope she can respond back by packing her letter in envelope which passes the same chain backwards. Sending and receiving letter this way can help Peter and Jane chats whole day. *This setup of communication between computer is known as network*

This network is good but occasionally envelopes are lost or arrive late, causing interruption and confusion in the chat. Simple way to fix this problem is to mark packet with number and when Jane receives the envelope she sends back acknowledgement for it. Now Peter knows which envelope has been received and which needs to be resent, also message sequence doesn’t get jumbled up. Peter can also send message so big that it needs multiple envelope and when Jane gets them she puts all numbered envelopes together and read the message. *This envelope in networking world is known as TCP packet, which is used in sending message, data, videos etc. between computers*

Ryan liked the idea of chatting in class, so joined the conversation. Ryan sends joke to Peter, but unfortunately the packet landed with Jane. Jane's is confused; Ryan sends a sorry message to Jane, which then lands with Peter, now he is confused. This network which was working well for 2 people isn't working with 3 people. Easy fix Ryan adds his name and Peter's name on the packet (envelope) and resends the joke and now Peter is laughing. This enhancement in network allows everyone to join in and send packet to anyone in class. *This is a mesh network, where all the computers are joined to all other computers*

Everyone is happy execpt the new student of the class. She doesn't know names of all the students and is not able to contribute to the network. But she can be more help if instead of student's name their location in class is mentioned like 3rd row 4th column (in short say 3r4c). So now everyone changes from using name on the packet to this new number which is unique in the room and she can participate in this fun excercise of sending and receiving packets. *The location address of the student is the IP address, which is unique on the network, this is of the form 10.20.530.41, four numbers joined with dots. This is used for all the devices connected on the internet*

Does this system work for bigger classes? Yes, if student knows their position in the class and can then decide if the packet needs to be sent left-right-back-front. But what if Peter now wants to chat with Alex from other class. 

He can mention the name of the class and Alex on the packet and the student sitting by the door and quickly run to the class and deliver the letter to studnet by the door of that class, who then changes name from Alex to his position in the class and pass the packet. Also he reply back with 

 The packets gets delivered and responded no probm and no one is the class is interested in chatting with anyone else in the class. 
Think of it like talk to someone in a class, simple way is to yell their name and say 'Hi', they hear that and respond 'Hello'. But if everyone starts to yell name it will become confusing, unless you are in a rock concert then its ok :). Now there is teacher in the class so easy way is to pass the message via letter. That works well everybody knows where to pass the letter and delivery is successful and you get the response. But what if you want to pass a message to multiple friends in the class, you can't give a bunch of white folded paper to people in the class and expect them not to mess up. How to fix this, easy, write your friend's name on the folded letter, now the people passing the letter knows what to send where. This is good till there is one to one conversation, everybody knows where the message came from, so they send the letter back via same path and you get the response from your friends. This is how early internet looked like, even today single channel communication (like broadcasting) looks similar. 
and But this is a uptight nice music party with people whispering, how do you talk to the person on other side of the room The problem So to avoid a yelling party lets have a little quiter one with nice music on. 
Think of group of people

Its all about sending data between computers. Take for example you want to visit website https://wikipedia.org and you expect the site to show up on your browser. But how to make computer understand what it means and where to get the wikipedia page from. Hint: This is done using TCP/IP protocol. Before we go any further you should know all the devices/computers connected to internet (or any network) need to have an IP, it is a unique number (within the network) of the device e.g. 10.10.232.895 ([learn more about IP and TCP protocol](http://localhost:4000/articles/2018-02/how-computer-talk)).

When you type https://wikipedia.org your browser first need to find the IP of the server it needs to get page from. This IP is stored in DNS (Domain Name Service), think of it as a directory of website names and their IP addresses. For each webiste there is different DNS and the link between website and DNS is stored in Name Server (NS), these are like directory of directories. So your browser asks Name Server about the website and get DNS record, it then asks DNS the IP address of wikipedia.org, once it gets the IP address it stores it in its memory for future use. Now browser sends request to the IP (wikipedia server) to give page for https://wikipedia.org, wikipedia looks at the request and then sends the page back.

Remember your computer does not talk directly to wikipedia or to the DNS, it does through many routers on the way. Routers are like intelligent traffic lights or mail sorter. They check where the message is from and to whom its addressed to and then sends it in the right direction. I love to think this system as network of people sitting with a ledger

#### References

https://www.internetsociety.org/internet/history-internet/brief-history-internet/
https://www.youtube.com/watch?v=7_LPdttKXPc