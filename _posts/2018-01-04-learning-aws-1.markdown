---
layout: post
title:  "Learning AWS"
date:   2018-01-04 22:44:27 +1100
categories: learning aws
---
# AWS Zero to Hero
What is AWS you say? Don’t worry I will give you company while we demistify AWS togather :)

I am going to cover the following:
1. Secure access to AWS console, introduction to IAM roles
1. Creating instance (server) and creating image
2. Securing instance using security group and VPC
3. Address instance using domain, introduction to Route53
4. Prepare for high traffic using load balancer
5. Saving sessions centrally, introduction to ElastiCache
5. HTTPS using free SSL certificate
5. Alert on high load using Cloudwatch and SNS
6. Automate adding and reducing instances based on traffic
7. Using database
8. Using AWS CDN (Content Delivery Network), introduction to cloudfront
8. Script infrastructure using cloudformation
9. Serverless website, using S3 to host webpages
10. AWS Advice on optimizing AWS services using Trusted Storage 

## What is AWS and why we need it
Not long time ago the only way to host website, API service etc was renting or buying a server on a farm, which was could be a big sales process with plenty hidden cost, process delays and inflexibilities. Any change to this setup could mean repeating the process over again. Then came AWS (Amazon Web Services) and changed all that helping you to book servers whenever you want for whatever duration and almost any number. Upgrading and increasing the number of servers is litrally a mouse click away best of all "Pay for what you use". To top it all you can experiment most of the services for FREE for a year.

I would recommed you to create a "Free tier" account in AWS and try the services at no cost.

## AWS Console
When you [login](http://console.aws.amazon.com) to your AWS account you would get page very similar to this <aws1.png>. 
This is AWS console and we are going to introduce to different services using the console. AWS do also provide rich CLI (Command Line Interface) commands.
Click on "Services" (top left on the page), it will list all the services offered by AWS. In most of the cases clicking on these services will show introduction page which can provide valuable information about it. So click on various services to see what they are about.
 
## Creating your first server
Exciting time! You are going to create your own server in AWS cloud, in few minutes and if you are using AWS Free tier account, then at no cost to you.
Lets start

Once you login to AWS account you would see 