---
layout: post
title:  "How does internet work"
excerpt: "Its a web a really big web :)"
date:   2018-02-17
tags: [technology, whatis]
categories: technology
comments: true
---

You want to go to the site [https://wikipedia.org](https://wikipedia.org), it's simple right? You open the browser, type *wikipedia.org*, press enter and Voila! page appears like magic. You might not realize but this simple quick magic uses at least a few dozen computers and your request travels half way across the world before it comes back with the page. Let see how this works.

You might already know this, what you experienced with wikipedia or any other website is the magic of internet. Internet is global network of computer talking to each other, send data, pictures, videos, mails etc. Let's understand what this is and how it works.

Take a class of students, sitting in grid layout, we have rows and columns. Now if Peter on one side of the classroom wants to say 'Hi' to Jane, he can yell and risk of getting ignored by humiliated Jane, or can he pass a folded letter, packed in a packet. The packet is passed among the students, each of whom knows who it came from and where it needs to go. Peter and Jane chats whole day using this setup of students. *This setup of communication between computer is know as network*

This network is good but ocassionally there is either packet is lost in transit or arrives too late, causing interruption and confusion in the chat. How to over come this? Simple mark packet with number and let Jane send acknowledgement for each packet. Now Peter knows which packet has been received and which needs to be resent, also its easy to map response form Jane to message by Peter. Peter is so impressed with his little idea that he sends messsage so big that it needs multiple packet to fit in and when Jane gets them she puts all the numbered packets togather and read the message. *This packet is known as TCP packet, which is used in sending message, data, videos etc between computers*

This network is so good Ryan thought join the conversation. Ryan is naughty and thought to send joke on Jane to Peter, but unfortunately the packet landed with Jane. Jane's furious and Ryan feels like an idiot, he sends a sorry card in a packet to Jane, which then lands with Peter. This is a mess, this system working well for 2 people isn't able to cater for one more person. Ryan is intelligent he gets the problem he adds his name and Peter's name on the packet to resend the joke and now Peter is laughing. This enhancement in network allows everone to join in, there is lot more packets getting sent around the class. *This is a mesh network, where all the computers are joined to all the computer*

Everyone is happy execpt the new student of the class. She doesn't know names of all the students and is not able to contribute to the network. But she can be more help if instead of student's name their location in class is mentioned like 3rd row 4th column (in short say 3r4c). So now everyone changes from using name on the packet to this new number which is unique in the room and she can participate in this fun excercise of sending and receiving packets. *The location address of the student is the IP address, which is unique on the network, this is of the form 10.20.530.41, four numbers joined with dots. This is used for all the devices connected on the internet*

Does this system work for bigger classes? Yes, if student knows their position in the class and can then decide if the packet needs to be sent left-right-back-front. Does this work to send packet to other class. No. *This network is LAN (Local Area Network), which connection of computers at same location like in a office*
